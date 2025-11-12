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

### Endpoint

The base endpoint of the Association Registry is: `https://dilsat1-mw.pg.bdinetwork.org/`. This means that (for example) the parties endpoint is available on `https://dilsat1-mw.pg.bdinetwork.org/parties`.

## NoTN Authorization Registry

To improve interoperability of parties with NoTN, NoTN provides templates for delegation evidence. These are maintained [here](https://github.com/Network-of-Trusted-Networks/delegation-evidence-templates).

### Endpoint

The base endpoint of the Authorization Registry is: `https://ar.isharetest.net/`. This means that the delegation endpoint is available on `https://ar.isharetest.net/delegation`.

This Authorization Registry allows for an automated creation of policies using the /policy endpoint. More information on [the OpenAPI specifications of the /policy endpoint](https://ar.isharetest.net/swagger/index.html#/Policy/post_policy).

## NoTN Data Providers and Shippers

Data Providers and Shippers must (in line with iSHARE) register their capabilities endpoint in the Association Registry. The [capabilities endpoint](https://dev.ishare.eu/version-2.0.1/ishare-satellite-role/capabilities) provided must list the [NOTN-defined API-requirements](https://network-of-trusted-networks.github.io/api-requirements/) under supported_features->public. The following table explains the IDs that must be used to expose the feature (the ID is the same as the operationId in the OpenAPI specifications).

| NoTN API feature | id to be used in capabilities feature |
| ---------------- | ------------------------------------- |
| /webhooks/shipment-subscriptions POST | subscribeToShipments |
| /webhooks/event-subscriptions POST | subscribeToEvents |
| /webhooks/event-subscriptions/{subscriptionId} GET | getEventsSubscription |
| /webhooks/event-subscriptions/{subscriptionId} DELETE | deleteEventsSubscription |
| /webhooks/shipment-subscriptions/{subscriptionId} GET | getShipmentsSubscription |
| /webhooks/shipment-subscriptions/{subscriptionId} DELETE | deleteShipmentsSubscription |
| /shipments/{id} GET | getShipmentDetails |
| /events/{eventId} GET | getEventDetails |
