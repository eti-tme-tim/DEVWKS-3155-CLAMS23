# DEVWKS-3155 Build Your Network Programmatically with Nexus Dashboard Fabric Controller

With the recent release of Nexus Dashboard Fabric Controller (NDFC) and its automation support via Ansible and Terraform, network engineers are able to leverage its rich capabilities to manage their networks at scale in a more declarative fashion.  For more comprehensive automation support, attendees will want to leverage NDFC's OpenAPI-based REST API. This session will provide a general understanding about the API endpoints available. On this foundation, you will then jump right into a detailed investigation of templates, policies, and how they are leveraged to build configurations for your network switches.  Automation Python examples will be made available via GitHub as part of this session.

## Expectations

This is a Cisco Live DevNet 3000-level (expert) course that runs 45 minutes. The time constraints will greatly focus our efforts on the unique knowledge that is being presented today. As such, there is a bit more foundational (and intermediate) knowledge that you are expected to know for the session:

- Ansible
    - Understanding Playbooks, Modules.
- REST API (or general Web) workflows
    - Endpoints, Query parameters, HTTP GET/POST, JSON/YAML
- Nexus Dashboard Fabric Controller 12.x (or DCNM 11.x)
    - Save Intent, Recalculate Config, Deploy  

By the end of this session, you should be able to answer the questions:

- What are NDFC Templates?
- How do I apply them to my switches with the UI?
- How do I apply them to my switches with Ansible?

## Outline

In this workshop, you will cover the following topics:

1. [Learning Lab Orientation](./00-orientation.md)
1. [Workshop Setup](./01-setup.md)
1. [NDFC Templates Explained](./02-templates.md)
1. [NDFC Template Example - Creating a VLAN](./03-example.md)
1. [Workshop Challenge](./04-challenge.md)
1. [Routing Process Automation](./05-routing.md)
1. [Neighbor Adjacency Automation](./06-adjacencies.md)

## Workshop Requirements

This workshop leverages the Cisco dCloud demo ["NDFC for NX-OS v1"](https://dcloud2-rtp.cisco.com/content/demo/885306), customized for our specific use case. As part of the live, in-person Cisco Live Amsterdam 2023 event, this workshop environment has been pre-provisioned for you.

VPN connectivity into this demo environment is **required**. The credentials for the environment are available once the environment has been deployed. Since this reservation was done on your behalf, the credentials and connection information will be provided to you on handouts.

This learning lab environment will provide you with all the pre-requisite software. For your information, those dependencies are:

- Python 3.9+
    - REST API dependencies in requirements.txt
- Ansible
- Nexus Dashboard Fabric Controller 12.0.2f
