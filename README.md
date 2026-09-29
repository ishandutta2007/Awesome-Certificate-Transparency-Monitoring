# Awesome-Certificate-Transparency-Monitoring

## Top Certificate Transparency Monitoring Tools Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**

*Focused on CT Log Monitoring, Certificate Discovery, Unauthorized Issuance Detection & Phishing Domain Alerts*

**Last updated: September 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Certificate Transparency (CT) Monitoring**. These tools help security teams detect unauthorized certificate issuance, discover forgotten subdomains, identify phishing domains, and maintain visibility into their organization's public TLS certificate landscape.



**Examples** include Censys, Detectify, Red Sift Certificates, DigiCert CT Monitor, Meta CT Monitor, Sectigo CT Log Monitor, Keyfactor CT Monitor, SSLMate Cert Spotter, CertStream, and Spyse (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom CT log parsing, and transparent certificate monitoring — ideal for security teams that need full control over their CT monitoring pipeline without per-domain SaaS fees or vendor lock-in.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents



- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Censys](https://censys.com/)**

  Internet-wide scanning platform with deep Certificate Transparency log ingestion. Covers more TLS certificates than any competing scanner, including expired and revoked certificates. Unified data model ties host data to certificate chains, BGP prefixes, and autonomous systems. Academic tier free with .edu email. Individual tier $99/month for 2,000 queries . Free tier offers 100 credits/month (standard query costs 5 credits, advanced with regex costs 8 credits) .



- **[Detectify](https://detectify.com/)**

  External attack surface management platform with Surface Monitoring module. Uses Certificate Transparency logs alongside passive DNS to continuously discover and inventory internet-facing assets including web applications, subdomains, APIs, and cloud storage buckets. Helps identify shadow IT and forgotten assets .



- **[Red Sift Certificates](https://redsift.com/)**

  High-assurance CT monitoring platform ingesting and processing CT logs since 2017. Provides comprehensive certificate discovery data store. Features CAA policy management, issuer filtering, case creation for every newly discovered certificate, and automatic evaluation against defined policies. Provides webhook alerting for unauthorized issuances .



- **[DigiCert CT Monitor](https://www.digicert.com/)**

  CT log monitoring within DigiCert Trust Lifecycle Manager. Monitors CT logs for specified organizations and base domains, adding discovered certificates to centralized inventory. Supports assignment rules for metadata, custom views, reports, and email notifications for discovered certificates .



- **[Meta CT Monitor](https://developers.facebook.com/docs/certificate-transparency)**

  Free Certificate Transparency monitoring tool from Meta. Continuously fetches and stores data from public CA CT logs. Provides API and web interface for searching certificates by domain. Supports certificate alerts via webhook for new certificate issuance, and phishing alerts for domains that may be impersonating legitimate domains .



- **[Sectigo CT Log Monitor](https://www.sectigo.com/)**

  CT monitoring integrated with Sectigo Certificate Manager. Streams real-time certificate activity logs into Datadog for unified transparency, proactive monitoring, and automated logging. Enables SIEM pipeline integration for faster incident response and compliance .



- **[Keyfactor CT Monitor](https://www.keyfactor.com/)**

  CT log monitoring capabilities within Keyfactor EJBCA for certificate lifecycle management. Supports configuring CT logs for certificate issuance, ensuring compliance with browser CT policies, and monitoring certificate transparency .



- **[SSLMate Cert Spotter](https://sslmate.com/certspotter)**

  Hosted CT monitoring service from SSLMate. Zero-setup web dashboard for centrally managing certificates. Alerts when certificates are issued for your domains. Same detection capabilities as the open-source Cert Spotter tool (see Open-Source section) .



- **[Spyse](https://spyse.com/)**

  Internet asset discovery platform with certificate search API. Search parameters include issued_for_domain, issued_for_ip, issuer_org, issuer_common_name, subject_org, fingerprint hashes (MD5, SHA1, SHA256), validity dates, and trust status. Returns precise result counts for certificate queries .



## Open-Source GitHub Projects



- **[Cert Spotter](https://github.com/SSLMate/certspotter)**

  Open-source CT log monitor from SSLMate. Alerts when certificates are issued for monitored domains. **No database required** — easier to use than other open-source CT monitors. Uses a **special certificate parser** that ensures it won't miss certificates, even if other parts are unparsable. Detects certificates from CT logs recognized by Google Chrome or Apple. Implements defenses against null prefix attacks and identifier-based attacks. Configure watchlist, email recipients, and hooks for custom actions. **Go-based, MIT License** .



- **[certstream-server-go](https://github.com/Calidog/certstream-server-go)**

  Drop-in replacement for the original CertStream server. Aggregates, parses, and streams certificate data from multiple CT logs via WebSocket connections. Monitors all logs in Google Log list (Chrome-recognized). Three endpoints: `/full-stream` (all details), `/` (reduced details), `/domains-only` (domains only). **Performance**: ~40 MB RAM at idle, processes 250–300 certificates/second. Prometheus metrics endpoint. Docker deployment available. **Go-based** .



- **[certstream-go](https://github.com/CaliDog/certstream-go)**

  Go library for interacting with the CertStream network to monitor aggregated feed from CT logs. Leverages WebSocket and JSON query libraries with automatic reconnection. Returns two channels: certificate stream with JsonQuery structure and error stream. Easy to integrate into custom CT monitoring pipelines. **Go-based** .



- **[certstream (linkdata)](https://github.com/linkdata/certstream)**

  Small Go library wrapping `google/certificate-transparency-go`. Adds no new dependencies. Fetches CT log lists, streams results with configurable batch size and parallel fetch. Provides `LogEntry` type with `Cert()`, `DNSNames()`, and `Index()` methods. Lightweight alternative for custom CT log processing. **Go-based** .



- **[Sunlight](https://github.com/FiloSottile/sunlight)**

  Static CT API log implementation created by Filippo Valsorda with support from Let's Encrypt. The new architecture represents logs as simple flat file collections ("tiles"), enabling CDN caching and more efficient data distribution. Simpler and more efficient to run than traditional RFC 6962 logs. Used by Let's Encrypt's Twig, Willow, and Sycamore logs. **Go-based, BSD-3-Clause** .



### Additional Strong Open-Source Options



- **CT Log Processing**: **certstream-server-go** (WebSocket streaming, Prometheus metrics), **certstream-go** (Go library with reconnection), **certstream (linkdata)** (lightweight wrapper).

- **Monitoring**: **Cert Spotter** (no database, special parser, email/hooks alerts) .

- **Log Infrastructure**: **Sunlight** (Static CT API, tiled logs, CDN-friendly) .

- **Related Tools**: **crt.sh** (web-based CT log search), **Google Certificate Transparency Go** (official CT client library).



**Frameworks for building custom systems**: Combine **certstream-server-go** for WebSocket-based CT log streaming, **Cert Spotter** for domain-specific monitoring with alerting, and **Sunlight** for running your own CT log infrastructure. Add **PostgreSQL** for certificate storage and **Prometheus/Grafana** for monitoring the monitoring pipeline itself.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Certificate Transparency monitoring tools handle sensitive security data; ensure proper access controls and alert routing.

- **Open-source reality**: The open-source ecosystem for CT monitoring is **mature and production-ready**. **Cert Spotter** provides a robust, database-free monitoring solution . **certstream-server-go** enables real-time streaming of CT log data for custom security pipelines . **Sunlight** represents the next generation of CT log infrastructure, making log operation more accessible . For enterprise-grade inventory integration and compliance workflows, commercial platforms (Censys, DigiCert, Red Sift) offer deeper integration with certificate lifecycle management.



---



**Made for security engineers, SOC analysts, PKI administrators, and threat intelligence teams.**

Let's make certificate transparency monitoring more open, real-time, and actionable.
