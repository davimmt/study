# Site Reability Engineering 101 - Overview and Concepts

Obviously based on the [Google SRE book series](https://sre.google/books/):

- [Site Reliability Engineering](https://sre.google/sre-book/table-of-contents/)
- [The Site Reliability Workbook](https://sre.google/workbook/table-of-contents/)
- [Building Secure & Reliable Systems](https://google.github.io/building-secure-and-reliable-systems/raw/toc.html)

## Sumary

1. [Service Level Objectives](#service-level-objectives)
2. [Implementing SLOs](#implementing-slos)
3. [Embracing Risk](#embracing-risk)

## Service Level Objectives

*[Book, Part II - Principles, Chapter 4](https://sre.google/sre-book/service-level-objectives/)*

### Quick Description

Introduces the terminology and framework for reasoning about service reliability: how to select meaningful metrics, set targets for them, and use those targets to drive prioritization and set user expectations. Also covers practical pitfalls in aggregation, the control loop that connects measurement to action, and how contractual agreements relate to internal objectives.

### Core Keywords

- **SLI (Service Level Indicator)** — quantitative measure of a service aspect (latency, error rate, throughput, availability, durability)
- **SLO (Service Level Objective)** — target value or range for an SLI (e.g., 99th-percentile latency < 100 ms)
- **SLA (Service Level Agreement)** — contract with consequences (usually financial) for missing SLOs
- **Error Budget** — tolerable SLO miss rate (100% − SLO target); governs release velocity
- **Nines** — shorthand for availability (99% = "2 nines", 99.99% = "4 nines")
- **Percentile** — preferred over averages for SLIs; captures tail latency (p50, p95, p99, p99.9)
- **Yield** — fraction of well-formed requests that succeed (synonym for availability in some contexts)
- **Durability** — likelihood data is retained over time; key SLI for storage systems

### Mental Model

SLI → what you measure | SLO → what you aim for | SLA → what you promise (with teeth). Together they create a control loop: monitor SLIs → compare to SLOs → act if budget is at risk.

### Quick Reminders

- Use percentiles (not averages) to capture tail behavior
- Standardize SLI definitions into reusable templates
- Start from user needs, not from what is easy to measure
- Keep SLOs few, simple, and defensible — "perfection can wait"
- Don't pick targets based solely on current performance
- Avoid absolutes (no "always available" or "infinite scale")
- Keep a safety margin: internal SLO tighter than advertised SLO
- Don't overachieve: users rely on actual performance, not stated SLOs
- SLI categories by service type: user-facing (availability, latency, throughput), storage (latency, availability, durability), pipelines (throughput, end-to-end latency), all (correctness)
- SLAs are business decisions; SRE helps define measurable SLIs within them

---

## Implementing SLOs

*[Workbook, Part I - Foundations, Chapter 2](https://sre.google/workbook/implementing-slos/)*

### Quick Description

A step-by-step recipe for putting SLOs into practice: how to go from zero to a working error-budget-based approach. Covers choosing what to measure and how, deriving initial targets from real data, getting organizational buy-in, writing enforceable policies, and continuously refining the system. Also explores advanced patterns like user-journey modeling, request bucketing, and dependency-aware SLOs.

### Core Keywords

- **SLI Specification** — abstract description of what matters to users, independent of measurement method
- **SLI Implementation** — concrete measurement of the SLI specification (logs, load balancer, client-side, probes)
- **Error Budget** — 100% − SLO; quantifies acceptable unreliability (e.g., 99.9% SLO → 0.1% budget)
- **Error Budget Policy** — written policy of actions when budget is exhausted (freeze releases, prioritize reliability bugs)
- **Rolling Window** — recommended SLO evaluation period (prefer integral weeks; 4-week default)
- **Calendar Window** — aligns with business quarters; introduces mid-period uncertainty
- **Critical User Journey (CUJ)** — end-to-end sequence of user tasks used to define user-centric SLOs
- **Aspirational SLO** — tighter target tracked alongside current SLO but exempt from error budget enforcement
- **Bucketing** — labeling requests by tier/type to apply differentiated SLOs (e.g., premium vs. free)
- **Recall vs. Precision (SLI context)** — recall = proportion of real incidents captured; precision = proportion of SLI-flagged events that are real

### Mental Model

SLI spec → SLI implementation → measure → set starter SLO → get stakeholder buy-in → error budget policy → monitor & alert → iterate. The SLO is only useful when it has "teeth" (an enforced error budget policy).

### Quick Reminders

- Express SLIs as `good events / total events` for a 0–100% scale
- 100% reliability is the wrong target — it kills velocity and is unachievable end-to-end
- Start with what's cheap to measure (logs, load balancer); iterate toward client-side instrumentation
- Round down raw SLI measurements to get starter SLOs (e.g., 97.1% → 97%)
- Use multiple latency thresholds (e.g., p90 < 450 ms AND p99 < 900 ms) to capture tail
- Three stakeholders must agree: SREs (defensible), PMs (good enough for users), devs (achievable)
- Error budget policy must specify concrete actions and owners (production freeze, reliability sprint)
- Prefer 4-week rolling windows (integral weeks avoid weekend bias)
- Correlate SLO misses with support tickets and outages to validate SLI quality
- Use aspirational SLOs when the desired target isn't yet achievable
- Model dependencies carefully — don't naively multiply availability across zones (shared fate exists)
- Rank incidents by error-budget consumption to prioritize fixes
- SLO decision matrix axes: SLO met/missed × toil high/low × customer satisfaction high/low
- Component SLI types: request-driven (availability, latency, quality), pipeline (freshness, correctness, coverage), storage (durability)
- Review SLO docs monthly at first, then quarterly as maturity grows

---

## Embracing Risk

*[Book, Part II - Principles, Chapter 3](https://sre.google/sre-book/embracing-risk/)*

### Quick Description

Explores why pursuing maximum reliability is counterproductive and how SRE reframes reliability as a risk-management problem. Discusses how to measure service risk through unplanned downtime and request success rates, how to assess risk tolerance for both consumer and infrastructure services (considering availability targets, failure types, cost, and latency trade-offs), and how the error budget mechanism aligns product development velocity with reliability goals.

### Core Keywords

- **Risk Continuum** — reliability is not binary; services are placed on a cost/benefit curve where each incremental nine costs disproportionately more
- **Unplanned Downtime** — the primary proxy metric for service risk; captures user-facing failure
- **Time-based Availability** — `uptime / (uptime + downtime)`; traditional but less useful for globally distributed systems
- **Aggregate Availability** — successful requests / total requests; preferred yield-based metric at Google
- **Risk Tolerance** — the level of unreliability a service can accept, derived from business goals, user expectations, market position, and cost
- **Error Budget** — `100% − SLO target`; the allowed failure quota that governs release velocity
- **Error Budget Policy** — agreed-upon actions when budget is spent (e.g., halt releases, invest in resilience)
- **Partitioned Infrastructure** — offering the same infrastructure at multiple service levels (e.g., low-latency vs. throughput clusters) to match diverse client needs at different cost points
- **Background Error Rate** — typical ISP error rate (0.01%–1%); a useful floor when setting availability targets from the end-user perspective

### Mental Model

Reliability has diminishing returns: past a threshold, users can't tell the difference, but engineering cost explodes. Treat the availability target as both a floor and a ceiling. The error budget converts the reliability vs. velocity tension into a shared, data-driven negotiation: budget remaining → ship fast; budget spent → slow down and harden.

### Quick Reminders

- Extreme reliability hurts: it slows features, raises cost, and users on unreliable networks can't perceive the difference
- Cost of reliability has two dimensions: redundant resources + opportunity cost of not building features
- Availability target is both a minimum and a maximum — don't over-deliver
- Use request success rate (aggregate availability) over time-based uptime for distributed systems
- Risk tolerance factors for consumer services: target users (consumer vs. enterprise), competition, revenue link, failure type sensitivity
- Different failure shapes matter: constant low-rate errors vs. full outages have different business impact
- Infrastructure services should expose explicitly delineated service levels so clients choose cost/reliability trade-offs
- Partitioning infrastructure (e.g., low-latency vs. throughput clusters) can cut costs 50–90% for relaxed use cases
- Error budget is set quarterly from the SLO; a neutral monitoring system measures actual performance
- When budget remains, ship freely; when budget is nearly spent, the product team self-polices velocity
- Unplanned outages (network, datacenter) also consume the error budget, reducing remaining push capacity
- If launching is too slow, consider loosening the SLO to widen the budget — reliability targets should serve the business, not the other way around
