[![Build Status](https://travis-ci.org/Azure/batch-shipyard.svg?branch=master)](https://travis-ci.org/Azure/batch-shipyard)
[![Docker Pulls](https://img.shields.io/docker/pulls/alfpark/batch-shipyard.svg)](https://hub.docker.com/r/alfpark/batch-shipyard)
[![Image Layers](https://images.microbadger.com/badges/image/alfpark/batch-shipyard:cli-latest.svg)](http://microbadger.com/images/alfpark/batch-shipyard)

# Batch Shipyard
[Batch Shipyard](https://github.com/Azure/batch-shipyard) is a tool to help
provision and execute batch processing and HPC Docker workloads on
[Azure Batch](https://azure.microsoft.com/en-us/services/batch/) compute
pools. No experience with the
[Azure Batch SDK](https://github.com/Azure/azure-batch-samples) is needed; run
your Dockerized tasks with easy-to-understand configuration files!

## Major Features
* Automated [Docker Host Engine](https://www.docker.com) installation tuned
for Azure Batch compute nodes
* Automated deployment of required Docker images to compute nodes
* Accelerated Docker image deployment at scale to compute pools consisting of
a large number of VMs via private peer-to-peer distribution of Docker images
among the compute nodes
* Comprehensive data movement support: move data easily between locally
accessible storage systems, remote filesystems, Azure Blob or File Storage,
and compute nodes
* Docker Private Registry support
  * [Azure Container Registry](https://azure.microsoft.com/en-us/services/container-registry/)
  * Any internet accessible Docker container registry
  * Self-hosted [private registry backed to Azure Storage](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-linux-docker-registry-in-blob-storage) with automated private registry
    instance creation on compute nodes
* [Integrated Remote Filesystem Provisioning](docs/65-batch-shipyard-remote-fs.md)
and auto-linking of these filesystems to compute nodes with support for
  * [NFS](https://en.wikipedia.org/wiki/Network_File_System)
  * [GlusterFS](https://www.gluster.org/) distributed network file system
* Automatic shared data volume support
  * Remote Filesystems as provisioned by Batch Shipyard
  * [Azure File Docker Volume Driver](https://github.com/Azure/azurefile-dockervolumedriver)
    installation and share setup for SMB/CIFS backed to Azure Storage
  * [GlusterFS](https://www.gluster.org/) provisioned directly on compute nodes
* Seamless integration with Azure Batch job, task and file concepts along with
full pass-through of the
[Azure Batch API](https://azure.microsoft.com/en-us/documentation/articles/batch-api-basics/)
to containers executed on compute nodes
* Support for
[Azure Batch task dependencies](https://azure.microsoft.com/en-us/documentation/articles/batch-task-dependencies/)
allowing complex processing pipelines and DAGs with Docker containers
* Transparent support for
[GPU-accelerated Docker applications](https://github.com/NVIDIA/nvidia-docker)
on [Azure N-Series VM instances](https://azure.microsoft.com/en-us/blog/azure-n-series-general-availability-on-december-1/)
* Support for multi-instance tasks to accommodate Dockerized MPI and multi-node
cluster applications on compute pools with automatic job completion and Docker
task termination
* Transparent assist for running Docker containers utilizing Infiniband/RDMA
for MPI on HPC low-latency Azure VM instances:
  * [A-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-a8-a9-a10-a11-specs?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json): STANDARD\_A8, STANDARD\_A9
  * [H-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#h-series): STANDARD\_H16R, STANDARD\_H16MR
  * [N-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#n-series): STANDARD\_NC24R (not yet ready with Linux hosts)
* Automatic setup of SSH users to all nodes in the compute pool and optional
tunneling to Docker Hosts on compute nodes
* Support for credential management through
[Azure KeyVault](https://azure.microsoft.com/en-us/services/key-vault/)

## Installation
Installation is typically an easy two-step process. The CLI is also available
as a Docker image:
[alfpark/batch-shipyard:cli-latest](https://hub.docker.com/r/alfpark/batch-shipyard).
Please see [the installation guide](https://github.com/Azure/batch-shipyard/blob/master/docs/01-batch-shipyard-installation.md)
for more information regarding installation and requirements.

## Documentation
Please refer to the
[Batch Shipyard Guide](https://github.com/Azure/batch-shipyard/blob/master/docs)
for a complete primer on concepts, usage and a quickstart guide.

Please visit the
[Batch Shipyard Recipes](https://github.com/Azure/batch-shipyard/blob/master/recipes)
for various sample Docker workloads using Azure Batch and Batch Shipyard
after you have completed the introductory sections of the Batch Shipyard
Guide.

## Batch Shipyard Compute Node OS Support
Batch Shipyard is currently only compatible with
[Azure Batch supported Marketplace Linux VMs](https://azure.microsoft.com/en-us/documentation/articles/batch-linux-nodes/#list-of-virtual-machine-images).

## Change Log
See the [CHANGELOG.md](https://github.com/Azure/batch-shipyard/blob/master/CHANGELOG.md)
file.

* * *
This project has adopted the
[Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the
[Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any
additional questions or comments.
