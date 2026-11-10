# ADR-0002: ELK as optional logging stack

Status: **Accepted for the architecture proposal; implementation pending**.

Decision: Preserve Elasticsearch, Logstash and Kibana as optional profile/deployment, not part of every small monitoring smoke test. Current version 7.10.1 must be reviewed for compatibility, security and upgrade path before public claims of a supported deployment. Test full ELK separately with sample log ingestion and teardown evidence.
