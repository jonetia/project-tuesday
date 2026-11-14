# PROJECT TUESDAY™

**Mission Build Document · Version 1.2 · 14 November 2026**

*Temporal certainty. Without compromise.*

## 00 / Product and design charter — the $200m standard

**Product directive:** Project Tuesday must look, feel and behave as though a $200 million enterprise SaaS company built the world's definitive temporal verification platform. This is a standard of craft, **not** a claim about funding, customers, revenue or operational scale.

The design is **institutional, restrained, premium and deadpan**. Avoid novelty-page aesthetics, cartoon graphics, fake customer logos, fictional enterprise plans, simulated production telemetry, and self-conscious jokes explaining the premise. The comedy is the disproportion between the excellence of the execution and the simplicity of the question.

**First-screen hierarchy:** (1) the unambiguous **YES / NO** answer to *Is it Tuesday here?*; (2) the relevant timezone and timestamp, including clock provenance; (3) a concise verification state and accessible **Verify locally** action; (4) deeper evidence, globe and audit surfaces by progressive disclosure. A visitor must understand the verdict immediately without scrolling, understanding cryptography or loading 3D graphics.

**Visual system:** disciplined typographic scale, intentional whitespace, precise grid alignment, exceptional information density where warranted, restrained colors with semantic status tokens, elegant charts and evidence tables, subtle meaningful motion, and consistent responsive states. Design for mobile first without compromising desktop ambition. Provide loading, stale-data, degraded, offline, empty and failure states as deliberately as success states. Respect reduced motion, keyboard navigation, contrast and screen readers.

**Motion and globe:** cinematic but performant. Never delay the verdict for a globe, shader, animation or external asset. Any globe must reflect genuine timezone geography and support a credible accessible 2D fallback. Premium visuals may not disguise missing data or imply live independent infrastructure that does not exist.

**Copy:** formal, terse, operational. Public headings and incidents may be grandiose; evidence, timestamps, methods, limitations and counters must remain literally accurate. Internal design motto: **Build it like mission-critical infrastructure. Treat the mission with a straight face.**

**Quality gate:** each release should be visually cohesive, fast, accessible, honest and demonstrably correct at its current scope. A small polished product beats a sprawling unfinished simulation of an enterprise platform.

## 01 / Mission doctrine

Mission: create a real, absurdly rigorous public authority that answers one question: “Is it Tuesday here?” It must be technically credible, aesthetically extraordinary, independently inspectable, anonymous by default, and free to run except for an optional domain name.

North-star experience: a visitor sees an authoritative YES or NO, a globe showing where Tuesday currently exists, live evidence, an audit history, and a button to independently verify the answer. The site is stone-faced. No explanations of why the mission exists.

Success is shipping and learning—not traffic. Five visitors is sufficient. No monetization, paid notifications, growth loops, cookies, tracking pixels, advertising, or accounts.

Nonnegotiables: $0 mandatory recurring spend; permissively licensed dependencies and assets; no secrets in client code; no fabricated metrics; accessible, fast, responsive, and usable without WebGL.

## 02 / The impossible-looking experience

A. THE VERDICT: enormous YES / NO, with the exact location/timezone and timestamp used. A “verify locally” button recomputes independently in the browser.

B. THE TUESDAY FRONT: a beautiful interactive globe showing civil-time regions where Tuesday currently applies. Timezone polygons must come from a licensed, versioned dataset; boundaries and disputed regions are presented honestly. A flat map is the fallback.

C. FIVE WITNESSES: calendar arithmetic, epoch-day arithmetic, ISO-week derivation, Julian-day arithmetic, and an external time witness when available. Explicitly label shared assumptions and distinguish calculation independence from independent clocks.

D. THE CERTIFICATE: generate a signed attestation for a specific timestamp, timezone, algorithm version and result. Offer downloadable JSON plus a human-readable certificate. Public-key verification happens in the browser.

E. THE LEDGER: a hash-chained, append-only sequence of genuine observations. Publish sequence number, prior hash, digest, signature, software commit, scheduled check ID and actual execution time. Explain that a hash chain is not a decentralized blockchain and cannot alone prevent a server operator rewriting history.

F. THE WAR ROOM: cumulative passed/failed/disputed/missed checks; coverage numerator and denominator; last real check; actual uptime measurement if instrumented. Never label a design target as observed uptime.

G. INCIDENT COMMAND: an actual disagreement opens a permanent incident entry, preserves raw evidence and freezes certification for that check. Never silently override disagreement.

H. TUESDAY AFTER-ACTION REPORT: a weekly signed machine-readable report with number of checks, coverage, errors and boundary transitions. A delightfully pompous human-readable summary accompanies it.

I. THE RED BUTTON: “INITIATE MANUAL VERIFICATION” runs the genuine browser-side algorithms and verifies a published signature, displaying each step and evidence.

J. TEMPORAL CHAOS LAB: users can deliberately inject a faulty clock or timezone into a local sandbox, observe a real disagreement and learn why the system rejects it. Clearly separate simulated failures from production metrics.

## 03 / What is actually being proved?

We must distinguish four claims: (1) a given UTC instant maps to a particular civil date in a named timezone; (2) the weekday calculation is correct under specified calendar rules; (3) a named service signed a specific result; (4) a scheduled check genuinely ran at a claimed time. A signature proves origin/integrity under key custody assumptions—not truth, clock accuracy or continuous operation.

Use IANA timezone data and publish the tzdb version. ISO weekdays use Monday=1 through Sunday=7. Specify Gregorian calendar and supported date range; leap seconds and UTC source assumptions are documented. Calendar engines must not simply call the same built-in weekday function under different names.

Five checks are not five independent authorities. Four mathematical methods can share a clock and timezone mapping. The external witness is a separate clock/source when available, not an oracle; report degraded mode when offline.

For verifiable history, publish raw records plus deterministic verification code, signed checkpoints, and optionally anchor checkpoint digests in an independently controlled public repository or transparency service. That improves tamper detection, but no free solution guarantees that every scheduled check happened during an outage.

## 04 / Architecture: zero mandatory hosting bill

Recommended first deployment: static TypeScript/Vite site hosted on a provider's free static tier, with local browser verification. Build and sign periodic audit snapshots using scheduled GitHub Actions within published free quotas; commit signed append-only JSONL files and checkpoint manifests to a public GitHub repository. Publish generated data via static hosting. No database, no always-on server, no WebSocket required.

The site can animate live clock updates using local time; label those as browser calculations. Background signed checks occur only when the scheduled workflow actually runs. GitHub Actions schedules can be delayed or skipped: publish planned vs actual timestamps and count missed checks. Avoid promising minute-level reliability on free scheduled CI.

Optional later: a genuinely live WebSocket demo running only while a free compute allowance exists; never make it essential. Prefer static polling of signed manifests, not permanent connections. Browser Push requires permissions, subscription storage, a push sender and hosting; defer it rather than falsely promise free reliable notifications.

Repository: /web (Vite, TypeScript, accessible UI); /core (pure UTC, timezone and weekday logic); /witnesses (distinct implementations); /crypto (Ed25519 signing and verification); /audit (JSON schemas, hash chain and checkpoint tooling); /jobs (scheduled observations/reports); /tests (unit, property, boundary, fuzz and fault injection); /docs (protocol, threat model, licenses, learning journal).

Storage policy: one compact record per actual scheduled run, plus weekly aggregate reports; no visitor data. At one observation per hour, 8,760 observations/year; at one per minute, 525,600/year. Start hourly to minimize storage, CI quotas and noise; browser-side live checks can occur every second without creating audit claims.

## 05 / Free means free: license and cost gates

Use open-source code under a permissive license such as MIT or Apache-2.0; choose and record one license before publishing. Audit all direct and transitive packages, fonts, maps, shaders, images, geospatial datasets and attribution obligations. “Free to download” does not mean free to redistribute. Use self-authored graphics, system fonts, and explicitly compatible open datasets; avoid unlicensed map tiles and commercial imagery.

Potential stack: TypeScript, Vite, Three.js (MIT), Node.js built-in crypto/Web Crypto, Vitest (MIT), Playwright (Apache-2.0), GitHub Actions, GitHub Pages or an eligible free static hosting tier. Confirm current provider terms, build minutes, bandwidth, scheduling, public repository limits, license notices and any rate limits before launch. Domain registration/renewal is the only approved expense; optional domain privacy may depend on registrar/TLD.

No payment card required for production services if possible. No metered external APIs, hosted AI inference, paid analytics, paid certificate authority, proprietary globe imagery, external font CDNs or paid push infrastructure. Browser Web Crypto and public verification need no paid cryptography service.

Operational rule: if a free-tier provider changes terms, the system must remain portable to another static host. Export everything as ordinary files. Never quietly upgrade to paid services. A high-traffic surge can exceed free quotas; document that graceful degradation or temporary unavailability is acceptable, not a surprise bill.

## 06 / Security and scientific integrity

Threats: compromised signing key, forged history, wrong timezone mapping, stale external clock, CI schedule gaps, dependency supply chain attacks, browser clock tampering, malicious input and denial of service.

Keep private signing keys only in secured CI secrets or a protected local environment, never in the repo or frontend. Consider short-lived signing keys and a published rotation/revocation process. Pin dependencies and CI actions; minimize permissions. Public keys and verifier source are published. Use reproducible canonical JSON serialization for hashes and signatures.

Hash chain each record to the prior record; publish signed checkpoints and make old checkpoint hashes independently discoverable. Do not claim append-only immutability against the repository owner. Failure taxonomy: incorrect verdict, algorithm disagreement, external witness disagreement, missed scheduled check, unverifiable signature, unavailable service. These are distinct counters.

Define a test oracle for timezone and date boundaries, DST transitions, year boundaries, leap days, leap seconds (policy only), UTC offsets including 30/45 minutes, and extreme timezone offsets. Inject clock skew and corrupt signatures in tests. Accessibility: keyboard navigation, reduced motion, screen-reader verdicts, non-color status indicators and no mandatory 3D rendering.

## 07 / The learning contract: no prompt-only engineering

The builder writes the first implementation of every foundational concept. AI plays tutor, reviewer and test designer—not autopilot. For each feature: (1) explain the concept in plain English; (2) predict behavior before execution; (3) implement a small slice yourself; (4) write a failing test; (5) debug without asking for the entire answer; (6) explain it back; (7) only then accept AI review.

Three assistance modes: GREEN = questions and hints only; AMBER = pseudocode and targeted examples; RED = full solution only after a documented attempt and explicit request. Default GREEN for core learning tasks. Never let Claude silently rewrite a whole module during a lesson.

Learning journal per sprint: what I predicted; what surprised me; what failed; what I changed; what I can now explain unaided. Keep 20-minute focused sessions available alongside longer build sessions. Every sprint ends with a five-minute oral/written teach-back and a tiny transfer exercise.

Key learning ladder: variables/functions/tests → UTC vs local time → pure functions and date arithmetic → async tasks and scheduled jobs → hashes → digital signatures and key custody → canonical serialization → integrity chains → timezones and geospatial data → rendering and WebGL → reliability and threat modeling → CI/CD and open-source stewardship.

Learning scorecard: can I implement one witness from scratch, verify a signature without library magic, explain exactly what the ledger proves, diagnose a missed check, and rebuild the site from a clean checkout? These are stronger outcomes than lines of AI-generated code.

## 08 / Build phases and hard acceptance gates

PHASE 0 — THE OATH (one session): repo, MIT/Apache decision, cost ledger, licensing register, architecture decision record, learning journal. Gate: $0 operating plan with no paid dependency.

PHASE 1 — THE VERDICT (2–3 sessions): accessible static page, timezone selection, correct YES/NO, one independently written Gregorian weekday function, boundary tests. Gate: user can explain algorithm and pass tests.

PHASE 2 — THE WITNESSES (3–5 sessions): four mathematical routes, dependency map, adversarial dates, property-based tests. Gate: disagreement detected and not hidden.

PHASE 3 — THE SEAL (3–5 sessions): Ed25519 keys, canonical JSON, signed proof, browser verifier, corrupt-signature test. Gate: a third party can verify offline using public key and raw data.

PHASE 4 — THE LEDGER (3–5 sessions): hourly scheduled job, hash chain, signed checkpoint, audit download, missed-check reporting. Gate: real production records; no seeded fictional statistics.

PHASE 5 — THE WAR ROOM (2–4 sessions): real metrics, failures, incident view, report generation. Gate: every number traceable to raw evidence.

PHASE 6 — THE GLOBE (4–8 sessions): licensed timezone geography, Three.js globe, daylight and Tuesday boundaries, keyboard-accessible 2D fallback. Gate: correctness on International Date Line and non-hour offsets; acceptable performance on mobile.

PHASE 7 — THE ABSURDITY (2–4 sessions): red-button verification ceremony, downloadable report, chaos lab, meticulous institutional copy. Gate: funny because it is real, not because it lies.

PHASE 8 — THE RELEASE: anonymous identity, domain if desired, security review, license audit, static deploy, public protocol docs. Gate: zero required recurring costs and independent reproducibility.

Session counts are planning estimates, not deadlines. Pause and learn whenever a concept becomes opaque.

## 09 / Metrics, failure semantics and the counter joke

Define a check as one executed scheduled observation with a unique sequence ID and raw evidence. PASS: all required available local methods agree with reference result and signature verifies. DISAGREEMENT: one method differs. INVALID: record/signature malformed. MISSED: planned slot elapsed without an observation within published grace window. EXTERNAL-UNAVAILABLE: optional clock witness missing; report separately. A service outage is not a false Tuesday verdict.

Display PASS count, FAILURE count, DISAGREEMENT count, MISSED count, COVERAGE = executed scheduled slots / expected scheduled slots, and VERDICT ACCURACY = correctly classified executed checks / executed checks with trusted reference evidence. Show denominators and confidence limits; never infer 100% real-world correctness from agreement alone.

A running counter is earned only from actual signed observations. Do not backfill outages and call them live observations. If the website has five visits, the same rigorous counters still mean something.

Humorous official text: “No unauthorized Tuesdays detected.” “Tuesday has entered the Pacific theater.” “The Board finds insufficient evidence of Wednesday.” “All findings remain subject to the passage of time.” Keep jokes out of cryptographic evidence fields.

## 10 / First learning mission: implement Tuesday

Write a pure function isTuesday(instantUtc, timeZone): boolean. Before coding, answer: Is it possible for Tuesday to exist in one city while it is Monday elsewhere? What happens at midnight? What happens when daylight saving changes? What does UTC mean?

Exercise A: write a Gregorian weekday calculator without Date.getDay(); derive day count or use a known congruence after explaining its assumptions. Test 2026-11-10 (Tuesday) and 2026-11-11 (Wednesday) in UTC.

Exercise B: use Intl.DateTimeFormat with an explicit IANA timeZone to derive the local calendar date; never use the viewer's implicit timezone when certifying another place. Write tests for Pacific/Kiritimati and Pacific/Honolulu around the same UTC instant.

Exercise C: introduce an intentionally broken witness that always returns Tuesday. Write a consensus test that refuses certification and logs the disagreement.

Teach-back: explain why three agreeing weekday functions running from one faulty clock do not provide independent time assurance.

Claude tutor prompt: “You are my engineering tutor for Project Tuesday. Default to hints and questions. Ask me to predict outcomes before coding. Do not write full feature implementations unless I explicitly switch to RED mode. Review my code for correctness, security, licensing and understanding. End each session with one transfer exercise and a concise answer check.”

## 11 / The definition of done

The public site answers Tuesday correctly across supported timezones; visitors can independently recompute it; every published signed observation is independently verifiable; metrics correspond to genuine evidence; outages and missed checks remain visible; all code and assets are license-compliant; core functionality costs $0 to run under stated quotas; there is no tracking or account system; the 3D globe is optional; and the creator can explain, debug and extend the system without AI doing all the thinking.

Public-facing institutional motto: “Temporal certainty. Without compromise.”

Internal motto: “We did not need to build this. That is why we built it.”

## 12 / Governance amendment: Operation Out-Tuesday

Mission refinement (13 November 2026): This is a real open-source temporal verification protocol with an extraordinarily serious public website, not a mock enterprise dashboard. The comedy comes from the gap between genuine engineering and the trivial question. The public voice is relentlessly deadpan; never explain why Tuesday needs verification.

The mission is not virality, revenue, downloads, or retention. Five visitors is acceptable. The builder remains free to stop, pause, or spend a whole session understanding one function. A spectacular website is secondary to credible verification and genuine learning.

Priority order: (1) accurate and reproducible weekday answers; (2) independently inspectable evidence and honest statistics; (3) $0 mandatory operating cost and clean licenses; (4) developer learning; (5) excellent accessible design; (6) unnecessary but authentic engineering theatrics. The globe, WebSockets, Byzantine fault demonstrations and OpenTimestamps are optional enhancements, not launch dependencies.

Byzantine demonstration: build a real fault-injection experiment where a dissenting witness produces a reproducible disagreement and the certification policy reacts correctly. Do not call a simple vote among processes on one host a Byzantine fault-tolerant distributed protocol. Genuine independent nodes require independent failure domains, explicit network assumptions and an appropriate consensus algorithm.

OpenTimestamps: evaluate as an optional free, independently anchored timestamping mechanism for selected signed checkpoints. A completed Bitcoin-anchored proof establishes that committed data existed no later than a blockchain time bound; it does not establish Tuesday correctness, nanosecond accuracy, or guaranteed timely anchoring. Review client license, relay dependencies and availability before adoption.

No fictional production metrics, fabricated uptime percentages, false live nodes, fictional paid plans presented as purchasable, or claimed 24/7 WebSocket availability. An uptime target must be labeled as a target; measured uptime must have a defined measurement source and denominator. Comedy copy may be theatrical; operational evidence may not.

## 13 / GitHub repository decision and initial structure

Repository established on 14 November 2026: **[`jonetia/project-tuesday`](https://github.com/jonetia/project-tuesday)**, public, with `main` as default branch, README and MIT license present. Do not recreate it. No need for an LLC or separate organization. Public commits can reveal the developer's GitHub identity and configured commit email; review attribution and use a GitHub noreply address if desired. Anonymous branding on the website is separate from anonymity of source control.

Initial root files: README.md (deadpan mission and truthful status), LICENSE (MIT for original code), .gitignore, CONTRIBUTING.md (lightweight), SECURITY.md (responsible reporting), docs/PROJECT_MISSION.md (this document), docs/protocol.md (draft, versioned), docs/architecture-decisions.md, docs/learning-journal.md, docs/license-register.md, and docs/cost-ledger.md. Start with minimal folders and add `/core`, `/web`, `/tests`, `/audit`, and `/jobs` only as implemented. Do not scaffold an empty enterprise monorepo for appearances.

Repository protections: enable branch protection when available; require review of workflow changes and secret handling; use least-privilege GitHub Actions permissions; pin third-party actions to immutable commits when practical; never commit private signing keys. Public verification keys are fine to publish. A public repo is an auditable source of code and records, not by itself a guarantee of independent operation or tamper-proof history.

Licensing: MIT covers code we own, not automatically every asset, dataset, font, image, or dependency. Maintain a license register and notices. Never publish secrets, personal information, or third-party materials without redistribution rights.

## 14 / First Tuesday session: 17 November 2026

Target duration: 45 minutes, flexible and not a deadline. The user drives the keyboard; AI acts as tutor by default. Session outline, updated because GitHub setup is already complete: 5 minutes review of the mission and local setup; 10 minutes clone repository and understand its files; 5 minutes establish the smallest workable test environment; 20 minutes write the first UTC weekday function and test with the user at the keyboard; 5 minutes teach-back and commit. If the first function takes the whole session, that is a successful session.

The initial GitHub commit already exists. Next commit suggestion: `docs: adopt Project Tuesday mission v1.2`. Commit the first algorithm only after the user understands and tests it. Do not create a scheduled cloud workflow, WebSocket server, persistent database, domain purchase, or production cryptographic key in the first session.

Educational checkpoint: explain what a repository, commit, branch, unit test and pure function each do; explain why UTC is not a timezone-specific local weekday; demonstrate one failing test and repair it. Log what was understood without AI assistance.

Release order: local correct YES/NO -> public static site -> independent witnesses -> signed evidence -> scheduled real observations -> honest metrics -> optional globe -> optional OpenTimestamps and fault-tolerant experiments. Each stage must remain useful and free without the next.

## 15 / Product boundary: StandBy and Sky

Project Tuesday is a distinct, lightweight learning laboratory. The Cosmic Department of Perspective / Domestic Mission Control StandBy idea is a separate potential SwiftUI/WidgetKit experiment; Sky remains a separate aviation project. Do not combine repositories, roadmaps, databases, or release obligations. The shared philosophy is disproportionate craft, truthful engineering, privacy, and delight—not shared infrastructure.

## 16 / Release strategy: credible first, extraordinary over time

The vision in this document is a **north star, not a launch checklist**. Avoid making the globe, five witnesses, signed certificates, hourly audit jobs, the war room or the chaos lab prerequisites for publishing the first useful site.

**Release 0 — The Verdict:** a beautifully designed static website with a correct timezone-aware YES/NO, clear clock/source labeling, a local verification action, accessibility and boundary tests. Do not imply a signed institutional verdict when only browser-local calculation exists.

**Release 1 — Reproducible Evidence:** additional independent mathematical implementations, visible methods and adversarial test coverage. Report their shared clock/timezone assumptions.

**Release 2 — Attested Operations:** signatures, scheduled real observations, verifiable public records and honest coverage/failure reporting, only once the security and scheduling design is understood.

**Release 3 — Global Theatre:** beautiful globe, audit command center, weekly reports and carefully labeled chaos experiments. These remain optional and must not compromise the first-screen verdict.

The $200m visual standard applies to **every** release, including Release 0. It does not authorize fake statistics, artificial infrastructure, premature complexity or AI-written code the builder cannot explain.

## 17 / Amendment record

- **v1.1 — 13 November 2026:** verification doctrine, engineering honesty, zero-cost architecture, learning contract and Tuesday session plan.
- **v1.2 — 14 November 2026:** added explicit premium enterprise product/design charter; strengthened first-screen hierarchy and progressive disclosure; defined honest release increments; updated GitHub repository and first-session status. Existing verification, security, licensing and learning commitments remain in force.
