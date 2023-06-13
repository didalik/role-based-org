# Дід Alik &amp; the Kids

Hi there, I'm Дід Alik. Welcome to <i>Дід Alik &amp; the Kids</i> - a distributed [role-based](https://www.calmachiever.com/holacracy-role-based-structure) organisation (**the Org**) I created on [GitHub](https://github.com/didalik) to support my hobby project [Stellar Help Exchange](https://github.com/amissine/shex). When/if the project is of any use, I will need Associates and Partners to join the Org.

Within the Org, everyone is a kid - including myself. And kids have roles. Both kids and roles are associated with Linux accounts. Physically, the Org is a set of Linux hosts. If kid <i>K</i> has role <i>R</i>, she can SSH to <i>R@Rhost</i> and access the Git repositories role <i>R</i> holds. Also, kid <i>K</i> can allow kid <i>A</i> to SSH to <i>K@Khost</i> by adding <i>A</i>'s public key to <i>K</i>'s `~/.ssh/authorized_keys` file. One way role accounts differ from kid accounts is that only the Org's **configuration utils** can access a role's `~/.ssh/authorized_keys` file.

## How It Works

Consider the following example. <i>Ann</i> requested role <i>devops</i>, and <i>Bob</i> requested roles <i>devops</i> and <i>prod</i>. Upon approval of these requests, the following two [TOML](https://en.wikipedia.org/wiki/TOML) documents are being produced:

- `ann.toml`:

```
KID_NAME="Ann"
KID_ACCOUNT_NAME="ann"
KID_HOST_NAME="m1"
KID_PK=""
KID_ROLES=[ ["devops", "m1", "u20"] ]
APPROVED=""
```

- `bob.toml`:

```
KID_NAME="Bob"
KID_ACCOUNT_NAME="bob"
KID_HOST_NAME="u22"
KID_PK=""
KID_ROLES=[ ["devops", "u20"], ["prod", "u20"]
APPROVED=""
```

The configuration utils then consume these two documents and produce the requested configuration. Now <i>Ann</i> has access to <i>devops</i> Git repositories on hosts m1 and u20, and <i>Bob</i> has access to <i>devops</i> and <i>prod</i> Git repositories on host u20. <i>Bob</i>'s account resides on host u22, and <i>Ann</i>'s account resides on host m1. And all SHH access is [chrooted](https://www.tecmint.com/restrict-ssh-user-to-directory-using-chrooted-jail/) by design. Support for and examples of remote port forwarding are also included.

## Initial text to delete

Дід Alik &amp; the Kids (the **Org**) is a distributed [role-based](https://www.calmachiever.com/holacracy-role-based-structure) organisation dedicated to Automated Integration Modeling utilizing the concept of **Shared Services**. Presently, the **Stellar Help Exchange** is the Org's project that is based on Shared Services. We also offer Shared Services support to other businesses.

Within the Org, we identify the following roles:

- DEV-QA;
- PROD; and
- SVC-PROVIDER.

Physically, the Org consists of distributed devices of two types: the leaves and the hubs. A leaf is a device used by the Org's kid. The device is configured according to the kid's role(s). You bind your leaf to a hub; a hub can be bound to other hubs. Separate projects are used to configure leaves and hubs for different roles. For example, DEV-QA is configured by the following two projects:

- [dev-qa-leaf-conf](https://github.com/didalik/dev-qa-leaf-conf); and
- [dev-qa-hub-conf](https://github.com/didalik/dev-qa-hub-conf).

All devices in the Org are Ubuntu boxes, utilizing [WSL](https://learn.microsoft.com/en-us/windows/wsl/install) or [UTM](https://docs.getutm.app/guides/ubuntu) when necessary. For a given role, cloning and running its leaf configuration project leads to cloning and running the corresponding configuration project on the hub you bind your leaf to. 
