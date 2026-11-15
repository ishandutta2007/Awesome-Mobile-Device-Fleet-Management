# Awesome-Mobile-Device-Fleet-Management

# Awesome Mobile Device Fleet Management

> A curated list of top Mobile Device Fleet Management platforms — both SaaS/Hosted commercial UEM/MDM solutions and open-source alternatives for enrolling, securing, and managing fleets of Android, iOS, Windows, and macOS devices.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Microsoft Intune](#microsoft-intune)
  - [VMware Workspace ONE](#vmware-workspace-one)
  - [Jamf Pro](#jamf-pro)
  - [Kandji](#kandji)
  - [Hexnode UEM](#hexnode-uem)
  - [Miradore](#miradore)
- [Open-Source Software](#-open-source-software)
  - [Fleet](#fleet)
  - [Headwind MDM](#headwind-mdm)
  - [MDMesh](#mdmesh)
  - [OpenUEM](#openuem)
  - [NanoMDM](#nanomdm)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Mobile Device Fleet Management platforms. These are not open-source but are included as reference points for feature comparison.

### Microsoft Intune
**Type:** Unified endpoint management within Microsoft 365
Intune provides device enrollment, configuration profiles, compliance policies, app deployment, and conditional access across Windows, macOS, iOS, Android, and Linux. It is the default choice for Microsoft-centric organizations, deeply integrated with Entra ID and the broader Microsoft security stack.

### VMware Workspace ONE
**Type:** UEM with enterprise wipe and full device wipe
Workspace ONE provides unified endpoint management with a clear separation between **Enterprise Wipe** (removes business data only) and **Device Wipe** (full factory reset). It is positioned for enterprises needing flexible deployment options and granular wipe controls.

### Jamf Pro
**Type:** Apple-focused MDM with deep macOS and iOS management
Jamf Pro is the enterprise standard for Apple device management, covering zero-touch deployment, configuration profiles, app management, and compliance enforcement. It is the natural choice for organizations with significant Apple fleets requiring Apple-specific depth.

### Kandji
**Type:** Modern Apple MDM with automated compliance
Kandji provides Apple device management with a focus on automation, compliance blueprints, and zero-touch deployment. It is positioned as a modern alternative to Jamf for organizations wanting a cleaner interface and automated workflows.

### Hexnode UEM
**Type:** Unified endpoint management across platforms
Hexnode provides device management for Android, iOS, Windows, macOS, and tvOS, with kiosk mode, app management, and compliance policies. It is positioned for mid-market organizations wanting comprehensive UEM without enterprise complexity.

### Miradore
**Type:** Free-tier MDM for small businesses
Miradore provides MDM for Android, Apple, and Windows devices, with a free plan that was limited to **50 enrolled devices** starting September 2024 . It is positioned for small businesses wanting essential device security without upfront cost, with paid plans unlocking additional features.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Mobile Device Fleet Management tools. The open-source ecosystem spans **cross-platform GitOps-native device management**, **Android-specific MDM**, **modern self-hosted Android fleet control**, **unified endpoint managers**, and **minimalist Apple MDM libraries**.

### Fleet
**Stack:** Go / React / MySQL / Redis | **License:** Open Source (free tier) / Commercial (Enterprise)
Fleet is the leading open-source device management platform for **macOS, Linux, Windows, Chromebooks, iOS, and Android** (BYOD or corporate-owned) . Key characteristics:
- **Single platform for every OS**: zero-touch enrollment, configuration profiles, policy enforcement, script deployment, and software management across macOS, iOS/iPadOS, Windows, Android, and Linux [citation:4][citation:7]
- **GitOps-native**: configuration lives in YAML, changes go through pull requests, and CI/CD validates and deploys—peer reviews can replace the change advisory board bottleneck [citation:4]
- **Scale proven**: used in production by IT and security teams managing thousands of devices, with some organizations managing **400,000+ devices** [citation:7]
- **Software management**: Fleet-maintained app catalog covers Chrome, Office, Firefox, Slack, Zoom, and more, with patch status connected to CVE data and automated compliance evidence [citation:4]
- **BYOD and department-level control**: account-based enrollment for Apple and work-profile-based management for Android, with department-based targeting for different OS settings and policies [citation:4]
- **Free version always free**: the free tier is independently backed and actively maintained, with Enterprise features available commercially [citation:7]

**Trade-off:** The free tier covers core MDM functionality, but some advanced features (like Okta conditional access integration and certain Apple DDM capabilities) are part of the commercial offering [citation:4].
**Best for:** Organizations wanting a single open-source platform for cross-platform device management with GitOps workflows and proven scale, accepting the free-tier feature boundaries.

### Headwind MDM
**Stack:** Java / PostgreSQL / Android | **License:** Apache-2.0
Headwind MDM is an established open-source **Android MDM** with a single admin console and REST API for enrolling company devices, pushing configurations, applications, and policies over the air . Key characteristics:
- **Android-focused**: launcher/agent app installed on devices, with web panel for management 
- **Community Edition**: free and open source under Apache-2.0, with no per-device or per-deployment fee [citation:8]
- **Dockerized deployment**: official Docker image available for running on any Linux distro [citation:3]
- **Secure-by-default images**: cloudimg offers an Ubuntu 24.04 image that generates unique random administrator passwords, device shared secrets, and database passwords on first boot, with the upstream default administrator never reachable over the network [citation:8]
- **Legacy v5 note**: the old web panel (AngularJS, Java EE) reaches end of life in December 2026 [citation:3]

**Trade-off:** Android-only—no iOS, Windows, or macOS management. The web panel source is available but the project is less active than Fleet.
**Best for:** Organizations managing Android-only fleets wanting a proven open-source MDM with a secure deployment path, accepting the Android-specific scope.

### MDMesh
**Stack:** Java / Kotlin / React / PostgreSQL | **License:** Apache-2.0
MDMesh is a modern, self-hosted Android MDM with a console that "doesn't feel like 2012" . Key characteristics:
- **No paid edition**: kiosk mode, app installs, location, and installers are all open source under Apache-2.0 [citation:1]
- **Device Owner enrollment**: scan a QR code during setup to make the MDMesh agent Device Owner [citation:1]
- **Kiosk mode**: locks a device to one app or a grid of chosen apps, with exit PIN protection and brute-force lockout that emails administrators [citation:1]
- **App delivery**: install from your own APK uploads, F-Droid catalog, or APK link, with SHA-256 verification on every install [citation:1]
- **Remote actions**: alert, lock-screen message, ring, lock, reboot, kiosk enter/exit, passcode reset, and factory reset [citation:1]
- **Signed updates with rollback**: the updater only offers releases whose signature verifies, backs up the database first, and rolls back automatically if the new version fails its health check [citation:1]
- **Staged agent rollouts**: canary devices first, then promote to the fleet [citation:1]

**Trade-off:** Android-only and a newer project than Headwind MDM. The console is modern but the ecosystem is smaller.
**Best for:** Android fleets wanting a modern, self-hosted MDM with kiosk mode, signed updates, and no paid tier, accepting the Android-specific scope.

### OpenUEM
**Stack:** Go / NATS / Web UI | **License:** Apache-2.0
OpenUEM is an open-source **Unified Endpoint Manager** recognized with a SourceForge Rising Star award in January 2026 . Key capabilities include:
- **Cross-platform agents** for Windows, Linux, and macOS [citation:12]
- **Remote assistance** via VNC session [citation:5]
- **Package deployment** using Winget, with uninstall support [citation:5]
- **Configuration profiles** to automate software deployment and settings (registry, local users, local groups) [citation:5]
- **Remote actions**: Wake-on-LAN, power off, reboot [citation:5]
- **File browsing** of endpoint logical disks [citation:5]
- **Clean web interface** designed for ease of use [citation:12]

**Trade-off:** Primarily endpoint management rather than mobile-first MDM—Android and iOS support are not the primary focus. The project has 126 stars on its console repository, indicating a smaller community than Fleet [citation:9].
**Best for:** IT teams wanting a self-hosted UEM for Windows/Linux/macOS endpoints with remote assistance and package deployment, accepting a narrower mobile focus.

### NanoMDM
**Stack:** Go / MySQL or PostgreSQL | **License:** Open Source (MIT-style)
NanoMDM is a minimalist **Apple MDM server** and library heavily inspired by MicroMDM . Key characteristics:
- **Horizontal scaling**: zero/minimal local state, with persistence in MySQL or PostgreSQL [citation:11]
- **Multiple APNs topics**: potentially multi-tenant [citation:11]
- **Multi-command targeting**: send the same command to multiple enrollments without individually queuing commands [citation:11]
- **Migration endpoint**: allow migrating MDM enrollments between storage backends or servers [citation:11]
- **API-driven**: queuing commands and APNs pushes via API [citation:11]

**Important:** NanoMDM is **one component** of a functioning MDM server—you need a SCEP server and TLS termination at minimum. It does not include SCEP, TLS, ADE/DEP API access, enrollment profiles, or VPP [citation:11].
**Best for:** Developers and advanced IT teams building custom Apple MDM infrastructure who want a minimalist, scalable MDM library, accepting that substantial surrounding infrastructure must be sourced separately.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Cross-Platform | Android | iOS | Self-Hosted | Best For |
|----------|---------|-------|----------------|---------|-----|-------------|----------|
| **Microsoft Intune** | Proprietary | Cloud | ✅ | ✅ | ✅ | ❌ | Microsoft 365 organizations |
| **Workspace ONE** | Proprietary | Cloud | ✅ | ✅ | ✅ | (On-prem) | Enterprise wipe controls |
| **Jamf Pro** | Proprietary | Cloud | Apple-only | ❌ | ✅ | (On-prem) | Apple-centric fleets |
| **Miradore** | Proprietary | Cloud | ✅ | ✅ | ✅ | ❌ | Small business free tier (50 devices) |
| **Fleet** | Open Source | Go/React/MySQL | ✅ | ✅ | ✅ | ✅ | Cross-platform GitOps + 400k scale |
| **Headwind MDM** | Apache-2.0 | Java/PostgreSQL | Android-only | ✅ | ❌ | ✅ | Android MDM with secure images |
| **MDMesh** | Apache-2.0 | Java/Kotlin/React | Android-only | ✅ | ❌ | ✅ | Modern Android kiosk + signed updates |
| **OpenUEM** | Apache-2.0 | Go/NATS | Desktop-focused | (Limited) | (Limited) | ✅ | Windows/Linux/macOS endpoints |
| **NanoMDM** | Open Source | Go/MySQL | Apple-only | ❌ | ✅ | ✅ | Apple MDM library for custom builds |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Mobile Device Fleet Management tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source.

**Note on the open-source ecosystem:** The open-source device management landscape has matured significantly in 2026. **Fleet** is the clear leader for cross-platform MDM, with proven scale (400k+ devices), GitOps-native configuration, and first-class support for macOS, iOS, Windows, Android, and Linux [citation:4][citation:7]. For **Android-only** fleets, **Headwind MDM** provides a battle-tested Apache-2.0 option with secure deployment images [citation:8], while **MDMesh** offers a modern alternative with kiosk mode and signed updates [citation:1]. **OpenUEM** addresses desktop endpoint management (Windows/Linux/macOS) rather than mobile-first MDM [citation:12]. **NanoMDM** fills the niche of a minimalist Apple MDM library for teams building custom infrastructure [citation:11]. No open-source project fully replicates Intune's depth of Microsoft 365 integration or Jamf's Apple-specific polish, but Fleet covers the core cross-platform fleet management workflow comprehensively.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
