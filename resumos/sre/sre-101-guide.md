# Site Reability Engineering 101 - Guide

## Sumary

- [1. Objective](#1-objective)
- [2. Implementation Framework](#2-implementation-framework)
- [3. Applying in a Real Project](#3-applying-in-a-real-project)
- [4. Operational Checklist](#4-operational-checklist)
- [5. Common Mistakes to Avoid](#5-common-mistakes-to-avoid)

---

## 1. Objective

Balance the risk of unavailability with the goals of rapid innovation and efficient service operations, so that users' overall happiness — with features, service, and performance — is optimized. Concretely this means:

- **Embracing risk as a continuum.** Reliability is not binary. Every service sits somewhere on a cost/risk curve; the job is to find the right spot, not to chase 100 %.
- **Making risk decisions explicit and data-driven.** Use SLIs, SLOs, and error budgets to replace politics and gut-feel with objective metrics that both product development and SRE teams share.
- **Defining, implementing, and continuously refining SLOs** so that engineering teams can make data-driven decisions about the balance between reliability work and feature development.
- **Keeping users happy** by measuring what matters, setting explicit targets, and enforcing those targets through error budgets.

---

## 2. Implementation Framework

### Step 1 — Identify risk tolerance for each service

Before selecting any metric, determine *how much risk the business is willing to bear* for each service. The process differs by service type:

| Factor | Consumer services | Infrastructure services |
|--------|------------------|------------------------|
| **Who decides?** | Product manager / product team. In the absence of a dedicated product team, the engineers building the system play this role. | Multiple clients with varying needs — there is rarely a single product owner. |
| **Key questions** | Is this paid or free? Consumer or enterprise? Does it tie directly to revenue? What do competitors offer? What level of service will users expect? | Which clients need low latency? Which need throughput? Can you partition the infrastructure into tiers? |
| **Availability target drivers** | User expectations, competitive landscape, revenue impact, business lifecycle stage (e.g., YouTube in 2006 prioritized velocity over nines). | Client SLAs, criticality of the infrastructure's position in the request path (e.g., frontend load balancers must be ultra-reliable because a dropped request is lost). |
| **Failure-shape considerations** | Constant low error rate vs. occasional full outage — same absolute errors, vastly different business impact. Privacy-violating failures may warrant taking the entire service down. | Low-latency clients need empty queues; throughput clients need queues that are never empty — success for one is failure for the other. |
| **Cost trade-off** | Translate reliability into revenue: `value_of_improvement = revenue × delta_availability`. If the cost to add a nine exceeds this value, stop. When direct translation is impossible, use ISP background error rate (0.01 %–1 %) as a floor. | Partition infrastructure into tiers (e.g., low-latency clusters vs. throughput clusters). Throughput tier can run at 10–50 % of the cost of the low-latency tier. Expose cost differences to clients so they self-select the cheapest tier that meets their needs. |

### Step 2 — Measure service risk (choose an availability metric)

| Method | Formula | When to use |
|--------|---------|-------------|
| **Time-based availability** | `availability = uptime / (uptime + downtime)` | Single-region or single-instance services where "up/down" is binary. |
| **Aggregate (request-based) availability** | `availability = successful_requests / total_requests` | Globally distributed services that are always at least partially serving (Google's default). Also applicable to non-serving systems by defining "successful units of work". |

Practical notes:

- Set **quarterly** availability targets and track performance against them **weekly or daily** to catch deviations early.
- Not all requests are equal (e.g., a failed sign-up vs. a failed background poll), but request success rate is a reasonable first-order approximation of unplanned downtime.
- For batch/pipeline systems, define success in terms of records processed correctly.

### Step 3 — Understand the SLI / SLO / SLA hierarchy

| Concept | Definition | Example |
|---------|-----------|---------|
| **SLI** (Service Level Indicator) | A quantitative measure of service behavior, expressed as *good events / total events*. | Proportion of HTTP requests that return non-5xx status codes. |
| **SLO** (Service Level Objective) | A target value (or range) for an SLI over a defined time window. | 99.9 % of requests succeed over a rolling 4-week window. |
| **SLA** (Service Level Agreement) | A contract with consequences (financial or otherwise) tied to SLOs. | "If monthly availability < 99.95 %, customer receives 10 % credit." |

SRE teams own SLIs and SLOs. SLAs are a business/legal concern, but SREs advise on feasibility.

### Step 4 — Select SLIs by component type

Classify every service component into one of three categories and pick the SLIs that match:

| Component type | Recommended SLIs |
|---------------|-----------------|
| **Request-driven** (APIs, web front-ends) | Availability (success rate), Latency (proportion faster than threshold), Quality (proportion served in undegraded state) |
| **Pipeline** (batch / streaming data processing) | Freshness (proportion of data updated within threshold), Correctness (proportion of correct output), Coverage (proportion of records processed) |
| **Storage** (databases, object stores) | Durability (proportion of written records that can be read back), Availability, Latency |

Express every SLI as a ratio: `good events / total events` (range 0–100 %).

### Step 5 — Choose SLI implementations

For each SLI specification, pick the data source that is closest to the user experience while remaining practical to collect:

1. **Client-side instrumentation** — highest fidelity, highest cost.
2. **Load balancer / CDN metrics** — good fidelity, readily available in most cloud setups.
3. **Application server logs** — easy to start with, but may miss client-side issues.
4. **Black-box monitoring / synthetic probes** — useful for end-to-end checks.

Rule of thumb: start with whatever is already available (e.g., load balancer metrics), then graduate to client-side instrumentation as the SLO practice matures.

### Step 6 — Set initial SLO targets

1. Collect at least 4 weeks of SLI measurements.
2. Round observed values down to manageable numbers (e.g., 97 % availability instead of 97.123 %).
3. Use multiple thresholds for latency (e.g., "90 % < 450 ms **and** 99 % < 900 ms").
4. Calculate the implied error budget: `budget = (1 − SLO) × total_events`.
5. Treat the availability target as **both a minimum and a maximum** — exceeding it by too much wastes opportunities to add features, clean up tech debt, or reduce operational costs.

### Step 7 — Obtain stakeholder agreement and form the error budget

Three groups must sign off before the SLO becomes active:

| Stakeholder | Must agree that… |
|-------------|-----------------|
| **SRE / Ops team** | The SLO is defensible without excessive toil or burnout. |
| **Product developers** | They will prioritize reliability when the error budget is exhausted. |
| **Product manager** | The threshold is good enough for users; below it is unacceptable. Product Management defines the SLO, which sets the expectation of how much uptime the service should have per quarter. |

**Forming the error budget:**

- Product Management defines an SLO, setting the expected quarterly uptime.
- The actual uptime is measured by a **neutral third party**: the monitoring system.
- The difference between the SLO and measured performance is the remaining error budget.
- As long as error budget remains, new releases can be pushed. When the budget is nearly or fully consumed, releases slow down or halt.

Example: if SLO = 99.999 % per quarter, error budget = 0.001 % failure rate. A problem causing 0.0002 % failures spends 20 % of the quarterly budget.

### Step 8 — Write an error budget policy

Document what happens when the error budget runs out:

- Development team prioritizes reliability bugs.
- Production freeze halts risky changes until the service is back within SLO.
- High-level escalation path if stakeholders disagree on actions.
- More subtle approaches than a simple on/off freeze: slow down releases or roll them back when the SLO-violation error budget is close to being used up.

**Key benefit:** the error budget provides a common incentive. Product developers become self-policing — when budget is large they take more risks; when it is nearly drained, *they themselves* push for more testing or slower push velocity, because they don't want to stall their launch.

### Step 9 — Set up monitoring, alerting, and dashboards

- Alert on SLO burn rate so engineers are notified **before** the budget is fully consumed.
- Build dashboards showing: current error budget remaining, SLI trends, and per-incident budget consumption.
- Produce periodic compliance reports (weekly for task prioritization, quarterly for project planning).

### Step 10 — Iterate and refine

- Review SLOs monthly when starting out; quarterly once mature.
- Correlate SLI dips with real incidents and support tickets.
- Adjust SLO tightness, change SLI implementations, or introduce aspirational SLOs as needed.
- If the team is having trouble launching new features, consider **loosening** the SLO (increasing the error budget) to increase innovation velocity.

---

## 3. Applying in a Real Project

### Phase 1 — Setup

1. **Assess risk tolerance.** For each service, answer the key questions from Step 1 (consumer vs. infrastructure, revenue impact, competitive landscape, failure-shape sensitivity). Document the answers.
2. **Choose the availability metric.** Decide between time-based and aggregate (request-based) availability. For globally distributed services, prefer aggregate availability.
3. **Map the architecture.** Draw a high-level diagram showing key components, request flow, data flow, and critical dependencies. Classify each component as request-driven, pipeline, or storage.
4. **Identify users and critical interactions.** Decide who the "users" are. List the most important user journeys (e.g., "complete a purchase", "run a search query"). For infrastructure services, identify client tiers and their distinct needs (latency vs. throughput).
5. **Pick 3–5 SLI specifications.** Choose SLIs that cover the most critical user-facing behavior. Favor availability and latency for request-driven services; freshness and correctness for pipelines.
6. **Choose SLI implementations.** Use the cheapest adequate data source available today (load balancer logs, existing Prometheus metrics, cloud monitoring dashboards).
7. **Instrument.** If needed, add histogram buckets for latency, success/error counters, or freshness watermarks.

**Example — Prometheus availability SLI for an HTTP API:**

```promql
sum(rate(http_requests_total{host="api", status!~"5.."}[7d]))
/
sum(rate(http_requests_total{host="api"}[7d]))
```

**Example — Prometheus latency SLI (90th percentile):**

```promql
histogram_quantile(0.9, rate(http_request_duration_seconds_bucket[7d]))
```

### Phase 2 — Execution

1. **Collect baseline data.** Run the SLI queries over the previous 4 weeks of data. Record observed availability, latency percentiles, and any other SLIs.
2. **Derive starter SLOs.** Round observed values down to two significant figures. Example: observed availability 97.12 % → SLO 97 %; observed p90 latency 432 ms → SLO "90 % of requests < 450 ms".
3. **Compute error budgets.** For 3,663,253 total requests and a 97 % availability SLO, the budget is ~109,897 allowed failures in 4 weeks.
4. **Perform cost/benefit analysis for the target.** If the service has a direct revenue translation, calculate: `value_of_improvement = revenue × delta_availability`. Ensure the cost of reaching the next nine does not exceed the projected revenue gain. If no direct translation exists, use the ISP background error rate (0.01 %–1 %) as a practical floor.
5. **Draft the SLO document.** Include: service description, SLI definitions, SLO targets, rationale, error budget calculation, review dates, authors, reviewers, and approvers.
6. **Draft the error budget policy.** Include: actions on budget exhaustion, escalation path, review cadence, handling of budget burns caused by external dependencies.
7. **Get stakeholder sign-off.** Present the SLO and error budget policy to the ops team, dev team, and product manager. Ensure the error budget is measured by a neutral third party (the monitoring system).
8. **Configure alerts.** Set burn-rate alerts so the team is paged when the error budget is being consumed faster than expected.

### Phase 3 — Maintenance

1. **Weekly review.** Check SLI dashboards. Identify top incidents by error budget consumed. Prioritize bugs accordingly.
2. **Monthly SLO review (early maturity).** Correlate SLI dips with support tickets and known outages. Adjust SLOs if false positives are too high or real incidents are missed.
3. **Quarterly planning.** Use error budget data to decide between competing reliability projects. Compare estimated budget savings of each project (e.g., "automating rollbacks saves ~26 % of quarterly budget vs. database HA saving ~13 %").
4. **Refine SLI implementations.** Migrate from server-side logs to load balancer metrics, then to client-side instrumentation as coverage gaps are discovered.
5. **Introduce aspirational SLOs.** If a tighter target is needed but the product can't meet it yet, track it alongside the current SLO without triggering the error budget policy.
6. **Model user journeys.** As the practice matures, define SLOs around end-to-end critical user journeys (e.g., "search → add to cart → checkout") rather than individual API endpoints.
7. **Re-assess risk tolerance periodically.** Business lifecycle, competitive landscape, and user expectations change. Re-evaluate whether the current availability target is still the right point on the cost/risk continuum (e.g., YouTube's target evolved as the product matured).
8. **Use error budget data to manage dev/SRE tension.** When the budget is large, allow faster push velocity, shorter canary durations, and lighter testing. When the budget shrinks, the product team self-polices by slowing down. Track this loop explicitly.

---

## 4. Operational Checklist

### Risk assessment

- [ ] Risk tolerance assessed for each service (consumer vs. infrastructure, revenue impact, competitive landscape, failure-shape sensitivity).
- [ ] For infrastructure services: client tiers identified and distinct SLO levels defined (e.g., low-latency vs. throughput clusters).
- [ ] Cost/benefit analysis performed: cost of adding a nine vs. incremental revenue or user impact.
- [ ] Availability metric chosen (time-based vs. aggregate/request-based) with rationale documented.

### Initial setup

- [ ] Architecture diagram drawn and components classified (request-driven / pipeline / storage).
- [ ] Users and critical user journeys identified.
- [ ] 3–5 SLI specifications selected (availability, latency, freshness, correctness, durability, quality, coverage).
- [ ] SLI implementations chosen and data sources confirmed.
- [ ] Instrumentation deployed (counters, histograms, watermarks).
- [ ] At least 4 weeks of baseline SLI data collected.

### SLO definition

- [ ] Starter SLO targets derived from baseline data (rounded down).
- [ ] Multiple latency thresholds defined (e.g., p90 and p99).
- [ ] Error budgets calculated for each SLO.
- [ ] SLO treated as both a minimum and a maximum — deliberate avoidance of overachieving.
- [ ] SLO document written (service description, SLIs, SLOs, rationale, dates, authors).
- [ ] Error budget policy written (actions, escalation path, review cadence, dependency-caused burns).
- [ ] All three stakeholder groups signed off (SRE/ops, dev team, product manager).

### Error budget operation

- [ ] Error budget measured by a neutral third party (monitoring system), not by either team.
- [ ] Error budget remaining is visible to both product development and SRE teams.
- [ ] Release velocity control loop in place: releases continue while budget remains; releases slow/halt when budget is nearly consumed.
- [ ] Graduated response defined (not just on/off freeze — slow down, roll back, invest in testing).

### Monitoring and alerting

- [ ] Burn-rate alerts configured to fire before budget is fully consumed.
- [ ] SLI trend dashboard operational.
- [ ] Error budget remaining dashboard operational.
- [ ] Per-incident budget consumption visible in dashboards.
- [ ] Weekly SLI summary reports automated.
- [ ] Quarterly compliance reports scheduled.

### Continuous improvement

- [ ] Monthly SLO review meetings scheduled (move to quarterly once mature).
- [ ] Process in place to correlate SLI dips with incidents and support tickets.
- [ ] Aspirational SLOs tracked when tighter targets are needed but not yet achievable.
- [ ] SLI implementation upgrade path planned (server logs → load balancer → client-side).
- [ ] Critical user journeys mapped and measured as the practice matures.
- [ ] Rolling 4-week window used for SLO evaluation (integral number of weeks to normalize weekday/weekend variance).
- [ ] Risk tolerance re-evaluated periodically as business lifecycle and competitive landscape evolve.
- [ ] Error budget used as an explicit mechanism to manage dev/SRE velocity tension.
- [ ] If unable to launch features fast enough, team has considered loosening the SLO to increase the error budget.

---

## 5. Common Mistakes to Avoid

### Risk and reliability philosophy

- **Targeting 100 % reliability.** 100 % is impossible and paralyzes innovation. Extreme reliability costs exponentially more while delivering diminishing marginal value. Users on a 99 % reliable smartphone cannot distinguish 99.99 % from 99.999 % service reliability. Always set a target below 100 % and budget for acceptable failure.
- **Treating reliability as purely a cost, never as a risk trade-off.** Reliability has two cost dimensions: (1) redundant compute/infrastructure, and (2) *opportunity cost* — engineers working on reliability are not building user-facing features. Balance both.
- **Ignoring opportunity cost.** Adding nines protects against failure but reduces feature velocity. If the cost of adding a nine exceeds the projected revenue gain, the investment is not justified.
- **Overachieving silently.** If you consistently deliver 99.99 % but only promise 99.9 %, users build expectations on the actual performance. When you eventually regress to your stated SLO, users will be unhappy. Deliberately avoid drifting far above your published SLO (e.g., use planned maintenance windows, throttle under light load). Treat the availability target as both a minimum and a maximum.

### SLO definition and measurement

- **Picking SLOs based on current performance without reflection.** This locks you into targets that may require heroic effort to sustain. Use current data as a starting point, but set SLOs based on what users actually need.
- **Too many SLIs.** Tracking dozens of indicators dilutes attention. Start with 3–5 that cover the most critical user experiences and expand only when gaps are proven.
- **Using averages instead of percentiles.** Averages hide tail latency. A system averaging 50 ms may have a 99th percentile of 1 s. Use percentile-based SLIs (p50, p90, p99) to capture the full distribution.
- **Choosing calendar-aligned windows without accounting for variability.** A 30-day window sometimes includes 4 weekends and sometimes 5, causing SLI variance for uninteresting reasons. Prefer rolling windows in integral numbers of weeks (e.g., 28 days).
- **Using only time-based availability for distributed services.** For globally distributed services that are always at least partially serving, time-based uptime/downtime is not meaningful. Use aggregate (request-based) availability instead.

### Error budgets and policy

- **No error budget policy.** An SLO without an enforcement mechanism is just a vanity metric. The policy is what turns the SLO into a decision-making tool.
- **Letting politics drive risk decisions instead of data.** Without an objective metric like the error budget, the balance between velocity and reliability becomes a function of negotiating skills rather than evidence. "Hope is not a strategy."
- **Applying the error budget policy when the outage was caused by an external dependency.** If the failure was not caused by your system, freezing your own releases penalizes your velocity without improving reliability. Document a clear policy for dependency-caused budget burns.
- **Using only a binary freeze (on/off) as the error budget response.** A simple "releases stop" policy is crude. Implement graduated responses: slow down releases, increase canary duration, roll back risky changes, invest more in testing — proportional to how much budget remains.

### Stakeholders and operations

- **Skipping stakeholder alignment.** If the dev team, ops team, and product manager don't all agree on the SLO and the consequences of missing it, the error budget will not be respected during crunch time.
- **Not re-evaluating risk tolerance as the business evolves.** A service in rapid growth (like YouTube in 2006) may deliberately accept lower availability to prioritize velocity. As the product matures, the target should tighten. Risk tolerance is not static.
- **Treating all infrastructure clients identically.** Infrastructure services have clients with opposing needs (low-latency vs. throughput). Offering a single service level wastes money or underserves clients. Partition into tiers with explicitly delineated levels of service.

### Dependencies and architecture

- **Assuming independent failure of redundant components.** Two zones sharing a global control plane do not multiply nines. Always enumerate shared dependencies and common failure domains before doing availability math.
- **Ignoring dependency SLOs.** If a critical dependency offers 99.9 % availability, your service cannot promise higher than 99.9 % unless you engineer around that dependency (caching, graceful degradation, store-and-forward).

### Continuous improvement

- **Never iterating.** SLOs are not set-and-forget. Services evolve, user expectations shift, and new failure modes emerge. Review and refine SLIs and SLOs at least quarterly.
- **Not using the error budget to highlight the cost of overly high targets.** If the team struggles to launch features, the error budget data should prompt a conversation about *loosening* the SLO to increase innovation velocity. The budget is a two-way tool.
