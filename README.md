# Clearwater Heat Templates

This repository contains templates for use with [OpenStack Heat](https://wiki.openstack.org/wiki/Heat) to deploy [Project Clearwater](http://www.projectclearwater.org).

`clearwater.yaml` is the top-level template, and depends on the other templates to create a network and Clearwater servers.

To use them, you must

-   have an [Ubuntu 14.04 cloud image](http://cloud-images.ubuntu.com/trusty/current/) imported into your OpenStack deployment
-   identify the external network in OpenStack that Clearwater should hang off, and find its network ID
-   create a DNS private key by running `head -c 64 /dev/random | base64`
-   create the stack by running `heat stack-create clearwater -f clearwater.yaml -P "public_mgmt_net_id=...;public_sig_net_id=...;dnssec_key=..."`.

For further options, see the definition of the `parameters` block in `clearwater.yaml`.

## FHoSS (OpenIMSCore HSS)
By supplying the parameter `use_fhoss=1` in the `-P` block, a FHoSS instance will be spun up and Clearwater will be configured to use it instead of Ellis. The HSS is automatically populated with three identities for testing purposes: `lovelace`, `dave` and `imhotep`, all with the password `test`.
