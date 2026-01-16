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

### Example request to parties endpoint

List all participants of the NoTN dataspace:

```
https://dilsat1-mw.pg.bdinetwork.org/parties?active_only=true&dataSpaceID=EU.DS.MOB.NL.NOTN.PDC
```

List all Data Providers in the NoTN dataspace:
```
https://dilsat1-mw.pg.bdinetwork.org/parties?active_only=true&role=ServiceProvider&dataSpaceID=EU.DS.MOB.NL.NOTN.PDC
```

List all shippers in the NoTN dataspace:

```
https://dilsat1-mw.pg.bdinetwork.org/parties?active_only=true&tags=*notn_shipper&dataSpaceID=EU.DS.MOB.NL.NOTN.PDC
```

### Public certificate

The X.509 certificate (DER format, Base64 encoded)  of this Association Registry is:

```
MIID5zCCAs+gAwIBAgIIJ1Lf4bnzVPkwDQYJKoZIhvcNAQELBQAwPDE6MDgGA1UEAwwxVEVTVCBpU0hBUkUgRVUgSXNzdWluZyBDZXJ0aWZpY2F0aW9uIEF1dGhvcml0eSBHNTAeFw0yMzA2MjYxMTMzMDZaFw0zMzA2MjMxMTMzMDVaMHMxHTAbBgNVBAMMFERpTCBTYXRlbGxpdGUgVGVzdCAxMR4wHAYDVQQFExVFVS5FT1JJLk5MRElMU0FUVEVTVDExFzAVBgNVBAsMDlByb3ZpbmcgR3JvdW5kMQwwCgYDVQQKDANCREkxCzAJBgNVBAYTAk5MMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAjUFIh3BUx70QTeaLEITO0jfFwwRc+cwWopUpvu+SZuStk75/nBiFm7HqAjsSfj2rlaV3kryIL2FzquT7oZAdYMncJIxqbDHCWvHlAt2OeGv+OaAROz+RuNUqs0GrAYHfHO0JsPzJ1E+xnsw2JlzJ993TslsfCjVCP5kkr6QhBRCIUTtAPvtf5pe+eHszMJOCeqIyxNiu65aQcfaxpN6z47xgH/e0sXU1qKDwyDt3DEudGijqGkEEXECbIhfT9WDLLm2w2TkgwIE2Plt0B3MFOoc8J98phL+rIFqavKkG2L/fEFlO3RvtAnVTptybXBuJlTDFsX7UoOMMOiEaQc2lawIDAQABo4G1MIGyMB8GA1UdIwQYMBaAFG3FZYnL35FU0Ws8twKlLs2KaJAdMCcGA1UdJQQgMB4GCCsGAQUFBwMCBggrBgEFBQcDBAYIKwYBBQUHAwEwNwYIKwYBBQUHAQMEKzApMAgGBgQAjkYBATAIBgYEAI5GAQQwEwYGBACORgEGMAkGBwQAjkYBBgIwHQYDVR0OBBYEFPJJBaKVp6zOQ7nyS2PPF8PQY4wCMA4GA1UdDwEB/wQEAwIGwDANBgkqhkiG9w0BAQsFAAOCAQEATk8CXtnbjUjCmsncYvMByljyxkh9uMAcb9yRFdp+pxYYo2G93pJL34iL72xReIPKh0cxeARxqIF7TgDshBijN/g4K2ymv6dUGHI79KZtyweU+pE5DFRlxXrJxG02nRr820exqON4j2GSh1GaboFwnL3xxJ+XBdTL2KXYc53nAUUXI4eLWpXjenUFC7DYg0V7Z7pSEdmJLhBj+1J2ujpVK/XMP/KBaHeZJaQ9PLDKUyIa7pfW7RpRErcFm6+bgDSy/iUH1Z2mlV00x2gXpMOYu1yzIDvEq8lvWeZb1jmqxoRwZLrZg8mHHrx1e/ALzgmpnCKFio0bd8itLSWDwFu5qg==
```

### Dataspace identifier

The identifier for the dataspace is `EU.DS.MOB.NL.NOTN.PDC`.

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
