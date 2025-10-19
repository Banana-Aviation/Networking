Basic L3VPN demo

All routers password : Juniper$$

On Juniper routers - PE routers will not redistribute L3VPN learned routes into OSPF running in VRF instance
In order for the routes to be exported by OSPF in VRF to CE routers policy should be applied for each VRF

```
set policy-options policy-statement EXPORT-BGP-TO-OSPF term 1 from protocol bgp
set policy-options policy-statement EXPORT-BGP-TO-OSPF term 1 then accept
set policy-options policy-statement EXPORT-BGP-TO-OSPF term 2 then reject

set routing-instances CE-BLUE-1 protocols ospf export EXPORT-BGP-TO-OSPF
```