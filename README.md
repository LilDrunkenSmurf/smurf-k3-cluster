<div align="center">

<img src="https://raw.githubusercontent.com/joryirving/home-ops/main/docs/src/assets/icons/kah-logo.png" align="center" width="144px" height="144px"/>


### <img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f680/512.gif" alt="🚀" width="16" height="16"> My Home Operations Repository <img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f6a7/512.gif" alt="🚧" width="16" height="16">

_... managed with Flux, Renovate, and GitHub Actions_ <img src="https://fonts.gstatic.com/s/e/notoemoji/latest/1f916/512.gif" alt="🤖" width="16" height="16">

</div>

<div align="center">

[![Discord](https://img.shields.io/discord/673534664354430999?style=for-the-badge&label&logo=discord&logoColor=white&color=blue)](https://discord.gg/home-operations)&nbsp;&nbsp;
[![Talos](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjoryirving%2Fhome-ops%2Fmain%2Fkubernetes%2Fmain%2Ftalos%2Ftalconfig.yaml&query=talosVersion&style=for-the-badge&logo=talos&logoColor=white&color=blue&label=%20)](https://www.talos.dev/)&nbsp;&nbsp;
[![Kubernetes](https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2Fjoryirving%2Fhome-ops%2Fmain%2Fkubernetes%2Fmain%2Ftalos%2Ftalconfig.yaml&query=kubernetesVersion&style=for-the-badge&logo=talos&logoColor=white&color=blue&label=%20)](https://www.talos.dev/)&nbsp;&nbsp;
[![Renovate](https://img.shields.io/github/actions/workflow/status/joryirving/joryirving/scheduled-renovate.yaml?branch=main&label=&logo=renovatebot&style=for-the-badge&color=blue)](https://github.com/joryirving/joryirving/actions/workflows/scheduled-renovate.yaml)

</div>

<div align="center">

[![Home-Internet](https://img.shields.io/endpoint?url=https%3A%2F%2Fhealthchecks.io%2Fbadge%2Ff0288b6a-305e-4084-b492-bb0a54%2FKkxSOeO1-2.shields&style=for-the-badge&logo=ubiquiti&logoColor=white&label=Home%20Internet)](https://status.jory.dev)&nbsp;&nbsp;
[![Status-Page](https://img.shields.io/endpoint?url=https%3A%2F%2Fstatus.jory.dev%2Fapi%2Fv1%2Fendpoints%2Fmain-external_gatus%2Fhealth%2Fbadge.shields&style=for-the-badge&logo=statuspage&logoColor=white&label=Status%20Page)](https://status.jory.dev/endpoints/external_gatus)&nbsp;&nbsp;
[![Plex](https://img.shields.io/endpoint?url=https%3A%2F%2Fstatus.jory.dev%2Fapi%2Fv1%2Fendpoints%2Fmain-external_plex%2Fhealth%2Fbadge.shields&style=for-the-badge&logo=plex&logoColor=white&label=Plex)](https://status.jory.dev/endpoints/external_plex)

</div>

<div align="center">

[![Age-Days](https://kromgo.jory.dev/cluster_age_days?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![Uptime-Days](https://kromgo.jory.dev/cluster_uptime_days?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![Node-Count](https://kromgo.jory.dev/cluster_node_count?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![Pod-Count](https://kromgo.jory.dev/cluster_pod_count?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![CPU-Usage](https://kromgo.jory.dev/cluster_cpu_usage?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![Memory-Usage](https://kromgo.jory.dev/cluster_memory_usage?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)&nbsp;&nbsp;
[![Power-Usage](https://kromgo.jory.dev/cluster_power_usage?format=badge&style=flat-square)](https://github.com/kashalls/kromgo/)

</div>

---

## Overview

This is a monorepository is for my home kubernetes clusters.
I try to adhere to Infrastructure as Code (IaC) and GitOps practices using tools like [Terraform](https://www.terraform.io/), [Kubernetes](https://kubernetes.io/), [Flux](https://github.com/fluxcd/flux2), [Renovate](https://github.com/renovatebot/renovate), and [GitHub Actions](https://github.com/features/actions).

The purpose here is to learn k8s, while practicing Gitops.

---

## ⛵ Kubernetes

There is a template over at [onedr0p/cluster-template](https://github.com/onedr0p/cluster-template) if you want to try and follow along with some of the practices I use here.

### Installation

My clusters run [talos linux](https://www.talos.dev) immutable kubernetes OS. This is a semi-hyper-converged cluster, workloads and block storage are sharing the same available resources on my nodes while I have a separate NAS server running Unraid withg NFS/SMB shares, bulk file storage and backups.

### Core Components

- [actions-runner-controller](https://github.com/actions/actions-runner-controller): self-hosted Github runners
- [cilium](https://github.com/cilium/cilium): internal Kubernetes networking plugin
- [cert-manager](https://cert-manager.io/docs/): creates SSL certificates for services in my cluster
- [external-dns](https://github.com/kubernetes-sigs/external-dns): automatically syncs DNS records from my cluster ingresses to a DNS provider
- [external-secrets](https://github.com/external-secrets/external-secrets/): managed Kubernetes secrets using [1Password](https://1password.com/).
- [ingress-nginx](https://github.com/kubernetes/ingress-nginx/): ingress controller for Kubernetes using NGINX as a reverse proxy and load balancer
- [longhorn](https://longhorn.io/): Cloud native distributed block storage for Kubernetes
- [rook-ceph](https://rook.io/): Cloud native distributed block storage for Kubernetes
- [sops](https://toolkit.fluxcd.io/guides/mozilla-sops/): managed secrets for Kubernetes, Ansible, and Terraform which are committed to Git
- [spegel](https://github.com/XenitAB/spegel): stateless cluster local OCI registry mirror
- [tf-controller](https://github.com/weaveworks/tf-controller): additional Flux component used to run Terraform from within a Kubernetes cluster.
- [volsync](https://github.com/backube/volsync): backup and recovery of persistent volume claims

### GitOps

[Flux](https://github.com/fluxcd/flux2) watches the clusters in my [kubernetes](./kubernetes/) folder (see Directories below) and makes the changes to my clusters based on the state of my Git repository.

The way Flux works for me here is it will recursively search the `kubernetes/${cluster}/apps` folder until it finds the most top level `kustomization.yaml` per directory and then apply all the resources listed in it. That aforementioned `kustomization.yaml` will generally only have a namespace resource and one or many Flux kustomizations. Those Flux kustomizations will generally have a `HelmRelease` or other resources related to the application underneath it which will be applied.

[Renovate](https://github.com/renovatebot/renovate) watches my **entire** repository looking for dependency updates, when they are found a PR is automatically created. When some PRs are merged Flux applies the changes to my cluster.

### Directories

This Git repository contains the following directories under [Kubernetes](./kubernetes/).

```sh
📁 kubernetes
├── 📁 main            # main cluster
│   ├── 📁 apps        # applications
│   ├── 📁 bootstrap   # bootstrap procedures
│   ├── 📁 flux        # core flux configuration
│   └── 📁 talos       # talos configuration
├── 📁 shared          # shared cluster resources
└── 📁 utility         # utility cluster
    ├── 📁 apps        # applications
    ├── 📁 bootstrap   # bootstrap procedures
    ├── 📁 flux        # core flux configuration
    └── 📁 talos       # talos configuration
```

### Networking

<details>
  <summary>Click to see a high-level network diagram</summary>

  <img src="https://raw.githubusercontent.com/joryirving/home-ops/main/docs/src/assets/network-topology.png" align="center" alt="dns"/>
</details>

---

## ☁️ Cloud Dependencies

While most of my infrastructure and workloads are self-hosted I do rely upon the cloud for certain key parts of my setup. This saves me from having to worry about two things. (1) Dealing with chicken/egg scenarios and (2) services I critically need whether my cluster is online or not.

The alternative solution to these two problems would be to host a Kubernetes cluster in the cloud and deploy applications like [HCVault](https://www.vaultproject.io/), [Vaultwarden](https://github.com/dani-garcia/vaultwarden), [ntfy](https://ntfy.sh/), and [Gatus](https://gatus.io/). However, maintaining another cluster and monitoring another group of workloads is a lot more time and effort than I am willing to put in.

| Service                                     | Use                                                               | Cost          |
|---------------------------------------------|-------------------------------------------------------------------|---------------|
| [1Password](https://1PAssword.com/)         | Secrets with [External Secrets](https://external-secrets.io/)     | Free - Work   |
| [Cloudflare](https://www.cloudflare.com/)   | Domain and R2                                                     | ~$30/yr       |
| [GitHub](https://github.com/)               | Hosting this repository and continuous integration/deployments    | Free          |
| [Healthchecks.io](https://healthchecks.io/) | Monitoring internet connectivity and external facing applications | Free          |
|                                             |                                                                   | Total: ~$3/mo |

---

## 🌐 DNS

### Home DNS

In my cluster there are two instances of [ExternalDNS](https://github.com/kubernetes-sigs/external-dns) running. One for syncing private DNS records to my `UDM Pro-SE` using [ExternalDNS webhook provider for UniFi](https://github.com/kashalls/external-dns-unifi-webhook), while another instance syncs public DNS to `Cloudflare`. This setup is managed by creating ingresses with two specific classes: `internal` for private DNS and `external` for public DNS. The `external-dns` instances then syncs the DNS records to their respective platforms accordingly.

---

## 🔧 Hardware

### Main Kubernetes Cluster

| Name  | Device       | CPU       | OS Disk   | Data Disk | RAM  | OS    | Purpose           |
|-------|--------------|-----------|-----------|-----------|------|-------|-------------------|
| Ayaka | Dell 7080mff | i5-10500T | 480GB SSD | 1TB NVME  | 64GB | Talos | k8s control-plane |
| Eula  | Dell 7080mff | i7-10700T | 480GB SSD | 1TB NVME  | 64GB | Talos | k8s control-plane |
| Ganyu | Dell 3080mff | i5-10500T | 500GB SSD | 1TB NVME  | 64GB | Talos | k8s control-plane |
| HuTao | Dell 3080mff | i5-10500T | 480GB SSD | 1TB NVME  | 64GB | Talos | k8s worker        |
| Navia | Dell 3080mff | i5-10500T | 240GB SSD | 1TB NVME  | 64GB | Talos | k8s worker        |
| Yelan | Dell 3080mff | i5-10500T | 240GB SSD | 1TB NVME  | 64GB | Talos | k8s worker        |

Total CPU: 76 threads
Total RAM: 384GB

### Utility Kubernetes Cluster

| Name     | Device     | CPU           | OS Disk   | Data Disk | RAM  | OS    | Purpose           |
|----------|------------|---------------|-----------|-----------|------|-------|-------------------|
| Celestia | Bosgame P1 | Ryzen 7 5700U | 480GB SSD | 1TB NVME  | 32GB | Talos | k8s control-plane |

Total CPU: 16 threads
Total RAM: 32GB

### Supporting Hardware

| Name    | Device        | CPU        | OS Disk    | Data Disk  | RAM  | OS           | Purpose        |
|---------|---------------|------------|------------|------------|------|--------------|----------------|
| Voyager | MS-01         | i5-12600H  | 32GB USB   | 1.92TB U.2 | 96GB | Unraid       | NAS/NFS/Backup |
| DAS     | Lenovo SA120  | -          | -          | 72TB       | -    | -            | ZFS - Raidz2   |
| PiKVM   | Raspberry Pi4 | Cortex A72 | 64GB mSD   | -          | 4GB  | PiKVM (Arch) | KVM            |

### Networking/UPS Hardware

| Device                      | Purpose          |
|-----------------------------|------------------|
| Unifi UDM-SE                | Network - Router |
| USW-Pro-24-POE              | Network - Switch |
| Back-UPS 600                | Network - UPS    |
| Unifi USW-Enterprise-24-PoE | Server - Switch  |
| Tripp Lite 1500             | Server - UPS     |

---

## ⭐ Stargazers

<div align="center">

[![Star History Chart](https://api.star-history.com/svg?repos=joryirving/home-ops&type=Date)](https://star-history.com/#joryirving/home-ops&Date)

</div>

---

## 🤝 Thanks

Big shout out to original [cluster-template](https://github.com/onedr0p/cluster-template), and the [Home Operations](https://discord.gg/home-operations) Discord community.

Be sure to check out [kubesearch.dev](https://kubesearch.dev/) for ideas on how to deploy applications or get ideas on what you may deploy.

---

## 📜 Changelog

See my _awful_ [commit history](https://github.com/joryirving/home-ops/commits/)

---

## 🔏 License

See [LICENSE](./LICENSE)
