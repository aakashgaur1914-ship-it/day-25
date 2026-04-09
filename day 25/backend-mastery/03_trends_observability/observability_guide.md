# Module 3.2: Observability Guide

Observability is the measure of how well internal states of a system can be inferred from knowledge of its external outputs. In distributed systems, this is critical.

## 1. The Three Pillars of Observability

### Logging
Discrete records of events.
- **Tools**: ELK Stack (Elasticsearch, Logstash, Kibana), Grafana Loki.
- **Best Practice**: Use structured logging (JSON format).

### Metrics
Aggregated numerical data over time (CPU, latency, error rates).
- **Tools**: Prometheus, Grafana, Datadog.
- **Best Practice**: Use standardized formats like OpenMetrics.

### Tracing
The "path" of a single request through multiple services.
- **Tools**: Jaeger, Honeycomb, AWS X-Ray.
- **Best Practice**: Use **OpenTelemetry** for vendor-neutral instrumentation.

## 2. Distributed Tracing Concepts
- **Span**: A single unit of work (e.g., a database query).
- **Trace**: A collection of spans that represent a full request flow.
- **Context Propagation**: Passing trace IDs between services (usually via HTTP headers).

## 3. Application Performance Monitoring (APM)
Deep monitoring of application internals, including memory leaks, slow functions, and database bottlenecks.
- **Tools**: New Relic, Dynatrace, Sentry.

## 4. Alerting Strategies
- **Golden Signals**: Latency, Traffic, Errors, and Saturation.
- **SLIs/SLOs**: Service Level Indicators (what you measure) and Service Level Objectives (the targets).
- **On-Call Management**: Tools like PagerDuty or Opsgenie.
