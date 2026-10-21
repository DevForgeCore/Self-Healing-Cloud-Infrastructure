<div align="center">

# Decision-Driven Autonomous Self-Healing Cloud Infrastructure
### Blockchain-Based Trust and Recovery Management

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2563EB,50:7C3AED,100:06B6D4&height=180&section=header&text=Self-Healing%20Cloud&fontSize=38&fontColor=FFFFFF&fontAlignY=38&desc=Monitor%20%E2%80%A2%20Detect%20%E2%80%A2%20Decide%20%E2%80%A2%20Recover&descAlignY=60&descSize=16" width="100%" alt="Animated gradient project banner">

<p>
  <strong>An educational prototype for monitoring system health, detecting resource problems, selecting recovery actions, and recording events.</strong>
</p>

<p>
  <img src="https://img.shields.io/badge/Java-21-orange?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java 21">
  <img src="https://img.shields.io/badge/Spring%20Boot-3.2.5-6DB33F?style=for-the-badge&logo=springboot&logoColor=white" alt="Spring Boot">
  <img src="https://img.shields.io/badge/Maven-Build-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white" alt="Maven">
  <img src="https://img.shields.io/badge/Linux-Ubuntu-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
</p>

<p>
  <a href="#-overview">Overview</a> •
  <a href="#-features">Features</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-run-locally">Run Locally</a> •
  <a href="#-testing-and-safety">Testing & Safety</a>
</p>

</div>

---

## Overview

**Decision-Driven Autonomous Self-Healing Cloud Infrastructure with Blockchain-Based Trust and Recovery Management** demonstrates a workflow for detecting common system resource problems and responding with predefined recovery actions.

**In simple terms:** monitor the system, detect a problem, choose a response, attempt recovery, and record what happened.

## Features

<table>
<tr>
<td width="50%" valign="top">

### <img src="https://img.shields.io/badge/01-Monitoring-2563EB?style=flat-square" alt="01 Monitoring">

Live CPU, RAM, and disk metrics with a resource-history chart.

### <img src="https://img.shields.io/badge/02-Detection-DC2626?style=flat-square" alt="02 Detection">

Rule-based detection of supported overload conditions.

### <img src="https://img.shields.io/badge/03-Decisions-7C3AED?style=flat-square" alt="03 Decisions">

A decision engine maps classified issues to configured actions.

</td>
<td width="50%" valign="top">

### <img src="https://img.shields.io/badge/04-Recovery-16A34A?style=flat-square" alt="04 Recovery">

Demonstrates recovery for supported CPU, memory, and disk scenarios.

### <img src="https://img.shields.io/badge/05-Event%20Logs-0891B2?style=flat-square" alt="05 Event Logs">

Incident and recovery records, with blockchain-inspired integrity logging.

### <img src="https://img.shields.io/badge/06-Dashboard-F59E0B?style=flat-square" alt="06 Dashboard">

System status, decisions, processes, logs, and trust-related information in one interface.

</td>
</tr>
</table>

## Architecture

```mermaid
flowchart TD
    A(["Linux Metrics"]) --> B["Monitoring"]
    B --> C{"Failure Detection"}
    C -->|Normal| H["Dashboard / Status"]
    C -->|Issue found| D["Failure Classification"]
    D --> E["Decision Engine"]
    E --> F["Recovery Service"]
    E --> G["Event & Integrity Logging"]
    F --> G
    B --> H
    D --> H
    E --> H
    G --> H
    style A fill:#DBEAFE,stroke:#2563EB,color:#1E3A8A
    style C fill:#FEE2E2,stroke:#DC2626,color:#7F1D1D
    style E fill:#EDE9FE,stroke:#7C3AED,color:#4C1D95
    style F fill:#DCFCE7,stroke:#16A34A,color:#14532D
    style G fill:#CFFAFE,stroke:#0891B2,color:#164E63
    style H fill:#FEF3C7,stroke:#D97706,color:#78350F
```

<details>
<summary><strong>How the workflow operates</strong></summary>

1. **Monitor** system resource usage.
2. **Detect** threshold-based anomalies.
3. **Classify** the issue, such as CPU overload, memory overload, or disk pressure.
4. **Decide** which configured response fits the detected condition.
5. **Recover** by running the corresponding action, where supported.
6. **Record** events and display information in the dashboard.

</details>

## Technology Stack

| Component | Technology |
|---|---|
| Backend | Java, Spring Boot |
| Build | Maven |
| Environment | Linux / Ubuntu |
| Frontend | HTML, CSS, JavaScript |
| Charts | Chart.js |
| Integration | REST API |
| Integrity approach | Blockchain-inspired event / hash-chain logging |

## Run Locally

**Prerequisites:** Java 21 (or the version configured in the project), Maven, Git, and Linux/Ubuntu for OS-level monitoring and recovery.

**1. Clone your repository** — replace the placeholders with your GitHub username and repository name.

```bash
git clone https://github.com/DevForgeCore/Self-Healing-Cloud-Infrastructure.git
cd Self-Healing-Cloud-Infrastructure
```

**2. Build and start**

```bash
mvn clean package
mvn spring-boot:run
```

Or run the packaged JAR:

```bash
java -jar target/*.jar
```

**3. Open the dashboard**

```text
http://localhost:8080
```

Check `application.properties` or `application.yml` if your app uses another port.

## Dashboard Preview

Add a screenshot of your actual dashboard to `docs/images/dashboard.png`, then remove the comment markers below to display it:

<!--
<p align="center">
  <img src="docs/images/dashboard.png" width="95%" alt="Self-Healing Cloud dashboard">
</p>
-->

## API Endpoints

The dashboard integration may use these routes; confirm them against the current controller code:

| Endpoint | Purpose |
|---|---|
| `/api/system-health` | Current resource metrics and status |
| `/api/logs` | Application or recovery logs |
| `/api/processes` | Process information |

## Testing & Safety

Use a **disposable test VM**, not a production machine. Stress tests can make a system unstable.

| Test | Example | Expected result |
|---|---|---|
| CPU | `yes > /dev/null &` | CPU load rises; detection depends on configured rules. |
| RAM | Use a small, controlled memory test | Memory use rises; detection depends on thresholds. |
| Disk | Create a small file in a dedicated test directory | Disk use rises; detection depends on filesystem metrics. |

Stop any test process you start. Avoid large memory allocations and never delete everything in `/tmp`; these actions can disrupt other services.

## Important Limitations

- Failure detection and the **Neural Insight Engine** are rule-based unless a trained ML model is actually added.
- Blockchain-inspired logs should only be called cryptographically tamper-evident if the backend computes and verifies real cryptographic hashes. This is not automatically a distributed blockchain.
- Recovery actions can terminate processes or affect files. Test only with dedicated demo processes and project-owned test files.
- Do not expose recovery controls to the public internet without authentication, authorization, strict action allow-lists, and security review.

## Future Improvements

- Validated ML-based failure prediction
- SHA-256 hash-chain verification
- Safer recovery checks and rollback
- Authentication and role-based access control
- Container / Kubernetes monitoring
- Automated tests and deployment support

## Project Structure

```text
src/main/java/com/prathi/selfhealingcloud/
├── classification/
├── controller/
├── scheduler/
└── service/

src/main/resources/static/
├── index.html
├── style.css
└── app.js

pom.xml
README.md
```

*The actual structure may vary slightly.*

## Contributing & License

Suggestions are welcome—open an issue to discuss a substantial change before submitting a pull request. No license is specified here; add a `LICENSE` file and update this section if you want to define reuse and distribution permissions.

---

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=18&pause=900&color=2563EB&center=true&vCenter=true&width=520&lines=Monitor+%E2%86%92+Detect+%E2%86%92+Decide;Recover+%E2%86%92+Record+%E2%86%92+Improve;Built+for+learning+and+experimentation" alt="Animated project tagline">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:06B6D4,50:7C3AED,100:2563EB&height=90&section=footer" width="100%" alt="Decorative gradient footer">

<sub>Final-year project • Learning • Experimentation • Continuous improvement</sub>

</div>
