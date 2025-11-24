# Development Cluster Update Process

This repository contains documentation and diagrams for the development cluster update workflow.

## 📊 Diagram

![Cluster Update Process](cluster_update_process.svg)

The main process diagram is located at [cluster_update_process.svg](cluster_update_process.svg) and can be edited directly as SVG/XML or recreated in [draw.io](https://app.diagrams.net/) for visual editing.

## 🔄 Workflow Overview

The cluster update process involves:

1. **Repository & Registry Checks** - Verify GitLab updates and package registry
2. **Pipeline Validation** - Ensure CI/CD pipeline is passing
3. **Container Management** - Pull, clean, and tag Docker images
4. **Singularity Build** - Create HPC-compatible containers
5. **Downstream Updates** - Update dependent repositories
6. **Deployment** - Run workflow on Parallel Works platform

## 🛠️ Technology Stack

- **Docker** - Container platform
- **Singularity** - HPC containers
- **GitLab** - Version control & CI/CD
- **Parallel Works** - Workflow platform
- **OpenShift/Kubernetes** - Orchestration

## 📝 Key Repositories

- NGEN (Core)
- Account Manager
- Forecast Manager
- NWM Verf
- UI / Server Components

## ⚠️ Important Notes

- Always verify no active sessions before updates
- Build Singularity containers sequentially (parallel builds crash cluster)
- Tag images as 'latest' for scripts to function properly
- Clean up regularly to prevent disk issues
- Coordinate with team members before major updates

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on updating the diagram.

## 📚 Documentation

- [Diagram Editing Guide](EDITING.md) - How to modify the diagram using draw.io
- [Update Checklist](CHECKLIST.md) - Step-by-step update procedure

---

**Last Updated:** November 2025
