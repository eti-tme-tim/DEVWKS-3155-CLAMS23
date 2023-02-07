# A CLI alternative to NDFC UI Template Searches

## Searching for Templates with Python

To avoid any issues with the NDFC web UI, I've written a simple Python command that will allow us to search the templates using NDFC's API interface.  The script was already installed as part of the setup script we ran earlier.

To test the command and ensure it runs, use the example command below to search for all templates with "feature" in the name:

```bash
ndfcctl --no-tls template list --filter feature
```

Your output should look something like this:

```
base_feature_leaf
base_feature_leaf_ebgp
base_feature_leaf_evpn
base_feature_leaf_upg
base_feature_spine
base_feature_spine_no_evpn
base_feature_spine_upg
base_feature_vpc
ext_multisite_rs_base_feature
feature_bfd
feature_bgp
feature_dhcp
feature_fhrp
feature_interface_vlan_11_1
feature_isis
feature_lacp
feature_lldp
feature_macsec
feature_mpls
feature_mpls_ldp
feature_mpls_sr
feature_mpls_vpn
feature_msdp
feature_netflow
feature_ngmvpn
feature_ngoam
feature_nv_overlay
feature_nxapi
feature_ospf
feature_ospfv3
feature_pbr
feature_pim
feature_ptp
feature_pvlan
feature_tacacs
feature_telemetry
feature_telnet
feature_tunnel_encryption
feature_vlan_based_vnsegment_11_1
install_feature_mpls
vpc_pair_feature_lacp
```

Last, to demonstrate the power of the API and this Python utility, to get the information we found for creating a VLAN, we simply need this command:

```bash
ndfcctl --no-tls template get create_vlan --full --nvpairs
```

As you can see in the output, we have the parameter name and the default value shown:

```
(optional): MODE                                : CE
(optional): NAME                                : 
(optional): VLAN                                : 
(optional): VNI                                 : 
```

## Feature

As we have seen, the template names are easily guessable in NDFC. So for enabling the OSPF feature, let's search for templates with feature in the name (hint, we just did this at the end of the last session) and limit the output to ospf:
 
```bash
ndfcctl --no-tls template list --filter feature | grep -i ospf
```

-The output is:
 
 ```
feature_ospf
feature_ospfv3
 ```
 
Does the **feature_ospf** template have any parameters?

```bash
ndfcctl --no-tls template get feature_ospf --full --nvpairs
```
 
No.  So, in our Ansible playbook (01-routing-protocols.yaml), we update the following entry to read:

```yaml
     enable_feature_template_name: feature_ospf
```

## Routing Process

From this search command, we get the following templates:

```
adv_static_prefix_ospf
base_ospf
base_ospf_auth
base_ospfv3
bfd_ospf
csr_ipsec_over_ospf
csr_ospf_redistribute
feature_ospf
feature_ospfv3
ios_xe_router_ospf
ospf_mpls_sr
ospf_redistribute_static
show_underlay_ospf
```

While the choice isn't quite so obvious, the correct template is **base_ospf** and we can see this with a little command line magic:

```bash
ndfcctl --no-tls template get base_ospf --full --verbose | jq .content | awk -F'##' '{ print $(NF-1); }'
```

where we can clearly see (poorly formatted) the NX-OS commands we are looking for. Yes, this is easier in the NDFC UI.

```
template content\n\nrouter ospf $$OSPF_TAG$$\n  router-id $$LOOPBACK_IP$$\n\n
```

## For the curious mind...

This section is completely optional.  

If you have time and want to see parameters for the **base_ospf** template, you'll use our favorite command as follows:

```bash
ndfcctl --no-tls template get base_ospf --full --nvpairs
```

which produces the following, now familiar output:

```
(optional): LOOPBACK_IP                         : 
(optional): OSPF_TAG                            :
```

As there are no value printed on the right, there are no pre-programmed defaults for this template.
