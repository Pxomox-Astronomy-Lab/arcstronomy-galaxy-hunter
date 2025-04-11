<p align="center">
  <img src="https://github.com/user-attachments/assets/807f6e09-c45a-41a0-949b-bf69be8fb70f" alt="ArcStronomy Galaxy Hunter Logo">
  <h1 align="center">ArcStronomy: Galaxy Hunter</h1>
  <p align="center">
    Discovering hidden galaxies with Azure Arc-enabled Kubernetes and on-premises GPU acceleration
  </p>
</p>

<p align="center">
  <a href="#about">About</a> •
  <a href="#architecture">Architecture</a> •
  <a href="#installation">Installation</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#requirements">Requirements</a> •
  <a href="#team">Team</a> •
  <a href="#license">License</a>
</p>

## About

**ArcStronomy: Galaxy Hunter** is a revolutionary application that discovers hidden Low Surface Brightness Galaxies (LSBGs) in the recently released Herschel-SPIRE Dark Field dataset. This groundbreaking dataset, published in early 2025, contains stacked observations that reveal previously undetectable galaxies that may fundamentally change our understanding of the universe.

Our project combines the power of:
- **On-premises GPU acceleration** via an NVIDIA A6000 in our Proxmox Astronomy Lab
- **Azure Arc-enabled Kubernetes** for management and deployment
- **Azure Functions** running directly on our K8s cluster
- **Azure Static Web Apps** for a live, engaging reporter interface

The result is a cost-effective, hybrid cloud solution that leverages the latest in cloud-native technologies while maximizing existing on-premises hardware investments.

## Key Features

- 🔍 **Real-time LSBG detection** using state-of-the-art models like DeepShadows and LSBGnet
- 🌌 **Interactive visualization** of newly discovered galaxies
- 🎙️ **Live "newsroom reporter" narration** of discoveries as they happen
- 📊 **Scientific cataloging** of finds with measured properties
- 🔄 **Continuous processing** of the Herschel-SPIRE Dark Field dataset

## Architecture

![ArcStronomy Architecture](assets/images/arcstronomy-architecture.png)

Our solution leverages a hybrid architecture that combines on-premises computing power with Azure cloud services:

1. **Data Processing Layer** (On-Premises)
   - RKE2 Kubernetes cluster running on Proxmox
   - NVIDIA A6000 GPU for accelerated image processing
   - Arc-enabled for Azure management and monitoring

2. **Application Layer** (Hybrid)
   - Azure Functions running on-premises K8s via Arc
   - Image processing models deployed as containers
   - Database services for discovery cataloging

3. **Presentation Layer** (Azure Cloud)
   - Azure Static Web Apps for the frontend interface
   - Real-time reporting through Azure SignalR Service
   - Authentication and access control

## Installation

### Prerequisites

- Azure subscription
- Kubernetes cluster (RKE2 recommended)
- NVIDIA GPU with CUDA support
- Azure CLI with Arc extension

### Quick Start

1. Clone this repository:
```bash
git clone https://github.com/yourusername/arcstronomy-galaxy-hunter.git
cd arcstronomy-galaxy-hunter
```

2. Install the required tools:
```bash
./scripts/install-tools.sh
```

3. Deploy the application:
```bash
./scripts/deploy.sh
```

For detailed installation instructions, see our [Installation Guide](docs/installation.md).

## How It Works

ArcStronomy processes the Herschel-SPIRE Dark Field dataset through a multi-stage pipeline:

1. **Data Acquisition**: The stacked image data (141 individual observations) is loaded from the Zenodo repository (ID 14846645)

2. **Preprocessing**: Images are normalized and prepared for analysis

3. **Detection**: Our implementation of the DeepShadows model scans for potential LSBGs

4. **Classification**: Detected objects are classified to filter out artifacts

5. **Property Measurement**: Surface brightness, size, and other properties are measured

6. **Reporting**: Discoveries are reported in real-time through a newsroom-style interface

7. **Cataloging**: All findings are cataloged for scientific reference

## Requirements

### Hardware
- Kubernetes cluster (minimum 3 nodes)
- NVIDIA GPU (A4000 or better recommended)
- 16GB+ RAM per node
- 500GB+ storage for dataset and processing

### Software
- Kubernetes 1.21+
- NVIDIA Container Runtime
- Azure CLI 2.40.0+
- Azure Arc-enabled Kubernetes
- Helm 3.8.0+

## Team

- **Donald Fountain** - Project Engineer
- **Alex Lemos** - Systems Administrator

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Built for the [Microsoft AI Agents Hackathon 2025](https://microsoft.github.io/AI_Agents_Hackathon/).
