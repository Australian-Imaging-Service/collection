Role Name
=========

Kubernetes configuration and infrastructure integration.

Requirements
------------

The kubernetes role uses a number of collections including the official `kubernetes.core` collection.

```bash
pipx runpip ansible install --upgrade -r "$(ansible-galaxy collection list kubernetes.core --format=json |jq -r 'keys[0]')/kubernetes/core/requirements.txt"
```

Role Variables
--------------

| Variable | Default | Description |
| -------- | ------- | ----------- |
| kubernetes_type | canonical | Set Kubernetes distribution type |
| kubernetes_cni_type | "" | Override default Container Network Interface |
| kubernetes_pod_cidr | "" | Override auto generated Pod CIDR address range |
| kubernetes_service_cidr | "" | Override auto generated Service CIDR address range |
| kubernetes_sans | [] | | Add extra x.509 certificate Subject Alternative Name (SAN) |
| kubernetes_dns_forwarders | [] | Override DNS forwarders used by the host |
| kubernetes_dns64_enabled | false | Enable the DNS64 coredns plugin |
| kubernetes_dns64_prefix | 64:ff9b::/96 | Set a DNS64 and NAT64 prefix |
| kubernetes_nat64_enabled | false | Enable NAT64 on each cluster host |
| kubernetes_ingress_enabled | false | Enable the Kuberentes Ingress controller |
| kubernetes_metrics_server_enabled | false | Enable the Kubernetes metrics server |
| kubernetes_local_storage_enabled | false | Enable a local storage CSI |
| kubernetes_local_storage_path | "" | Override default local storage path |
| kubernetes_control_plane_taints | [] | Add control plane taints |
| kubernetes_gateway_enabled | true | Enable the Kubernetes Gateway API |
| kubernetes_lb_enabled | false | Enable an in-cluster Load Balancer |
| kubernetes_lb_cidrs | [] | Provide IP address CIDRs to allocate to the Load Balancer address pool |
| kubernetes_lb_bgp_enabled | false | Configure the Load Balancer to utilise Border Gateway Protocol instead of OSI Layer 2 |
| kubernetes_environment | production | Set default settings to a specific environment |

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
