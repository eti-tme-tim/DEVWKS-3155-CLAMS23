# DEVWKS-3155-CLAMS23 - Building Your Network Programmatically with Nexus Dashboard Fabric Controller

## Requirements

For the examples in this repository, you'll need the following elements:

- Python 3.10.x
- Ansible 2.13.x
- Ansible DCNM Collection 2.4.0
- NDFC 12.1.1e
- Nexus 9000 Switching

As a part of Cisco Live Amsterdam 2023's in-person event, you'll be provided three resources to assist you in the setup:

- DevNet Learning Lab Environment (Python and Ansible sandbox)
- dCloud Environment (NDFC and Switches)

## Self Paced Usage

The following instructions are for self-paced learning attempts outside the Cisco Live in-person event. If you are in the workshop, **do not** follow the setup instructions below. You will use the learning lab and its instructions.  While similar, the below instructions will derail your DevNet workbench learning experience.

### Python/Ansible Environment Setup

There is a [setup-python.sh](./setup-python.sh) script that you can source to set up your environment, which builds a Python virtual environment ('venv') as well as installs the required Ansible DCNM collection.

### Workshop lab environment

In this workshop, we'll be Cisco's [dCloud](https://dcloud.cisco.com) platform - specifically, the ["NDFC for NX-OS v1"](https://dcloud2-rtp.cisco.com/content/demo/885306). (Note: if newer versions have been released, you have to search for the latest instance.)  The dcloud-inventory.yaml files in each of the Ansible directories has all the relevant connection information for the workshop. Due to security issues that have arisen, you must work with your Cisco Account Team to be granted access to an instance of the lab.

## Scenarios

The goal of this workshop is to walk you through the process of identifying templates within NDFC to leverage for configuring your NX-OS switches.  Three specific examples will be covered:

- Creating a VLAN within the NDFC UI
- [Creating the OSPF Routing process with Ansible](./ansible/01-routing-protocols.yaml)
- [Activating OSPF on a routed interface with Ansible](./ansible/02-routing-neighbors.yaml)

## References

- [NDFC 12.0.x Configuration Guide](https://www.cisco.com/c/en/us/td/docs/dcn/ndfc/1201/configuration/fabric-controller/cisco-ndfc-fabric-controller-configuration-guide-1201.html)
- [DevNet: NDFC REST API Reference](https://developer.cisco.com/docs/nexus-dashboard/#!nexus-dashboard-fabric-controller-lan-release-12-0-2)
- [Ansible DCNM Collection](https://galaxy.ansible.com/cisco/dcnm) [(GitHub)](https://github.com/CiscoDevNet/ansible-dcnm/)
