# Дід Alik &amp; the Kids

Дід Alik &amp; the Kids (the **Org**) is a distributed [role-based](https://www.calmachiever.com/holacracy-role-based-structure) organisation dedicated to Automated Integration Modeling utilizing the concept of **Shared Services**. Presently, the **Stellar Help Exchange** is the Org's project that is based on Shared Services. We also offer Shared Services support to other businesses.

Within the Org, we identify the following roles:

- DEV-QA;
- PROD; and
- SVC-PROVIDER.

Physically, the Org consists of distributed devices of two types: the leaves and the hubs. A leaf is a device used by the Org's kid. The device is configured according to the kid's role(s). You bind your leaf to a hub; a hub can be bound to other hubs. Separate projects are used to configure leaves and hubs for different roles. For example, DEV-QA is configured by the following two projects:

- [dev-qa-leaf-conf](https://github.com/didalik/dev-qa-leaf-conf); and
- [dev-qa-hub-conf](https://github.com/didalik/dev-qa-hub-conf).

All devices in the Org are Ubuntu boxes, utilizing [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) or [UTM](https://docs.getutm.app/guides/ubuntu) when necessary. For a given role, cloning and running its leaf configuration project leads to cloning and running the corresponding configuration project on the hub you bind your leaf to. 
