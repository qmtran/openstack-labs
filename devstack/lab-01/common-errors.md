# Common Errors:


### Install DevStack, `stack.sh` fails "Keystone did not start!"

  This error is usally happends after stack.sh has been going, the reason keystone can't start up is likely because the HOST_IP parameter in local.conf is not correct, double check the address and make sure it matches the eth0 interface (`ip addr show dev eth0`)

  **Solution:** fix the config typo and run `./unstack.sh` and re-run `./stack.sh`
