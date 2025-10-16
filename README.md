# NoTN Configuration Specifications

This repository contains shared specifications for configuration in components that form the Network of Trusted Networks.

## NoTN Association Registry

The NoTN Association Registry will be based on a BDI Association Registry, that is conformant to iSHARE Satellite specifications v2.0.1. This means that the NoTN Assocation Registry will provide endpoints that are specified under "iSHARE Satellite Role" on the [iSHARE developer portal](https://dev.ishare.eu/version-2.0.1/ishare-satellite-role/getting-started).

### NoTN Roles mapped to BDI and iSHARE roles

The following mapping describes the relationships between the roles used in the framework.

| NoTN | BDI | iSHARE 2.0.1 | Description |
|------|-----|--------------|-------------|
| NoTN Association Registry | BDI Association Registry | iSHARE Satellite | |
| Authorization Registry | Authorization Registry | Authorization Registry | |
| Shipper | Data Provider / Data Owner | Service Provider / Entitled Party| From a framework perspective the Shipper fulfills two roles |
| Data Provider | Data Provider | Service Provider | |
| Data Consumer | Data Consumer | Service Consumer | |

### Tags applied for NoTN role distinction

In NoTN a specific type of Data Provider is recognized: Shipper. To distinguish with other Data Providers in the NoTN Association Registry, the "tags" field will be used. All shippers will be marked with the tag "notn_shipper". This allows Data Consumers to obtain a list of Shippers from the Association Registry, to request subscription to new shipments.

## NoTN Authorization Registry

To improve interoperability of parties with NoTN, NoTN provides templates for delegation evidence. These are maintained [here](https://github.com/Network-of-Trusted-Networks/delegation-evidence-templates).
