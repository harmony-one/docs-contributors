# Troubleshooting

## How to kill node process from outside of tmux

In case you don't have a `tmux` session running; but you have your node process running, you can kill the node process with the following.

```text
sudo pkill harmony
```

## For ONE-CLICK Setup

### If for whatever reasons you want to run new node instance completely

#### Kill your current node instance

Run the following on your AWS instance

```text
exit
```

This will sign you out of your AWS instance. Then make sure you are in the same folder as the `setup-one-click-deploy.sh` script and run the following command.

```text
terraform destroy
```

This will destroy your previous AWS instance.

#### Start a new instance

Follow the steps in running [one-click-setup](https://docs.harmony.one/pangaea/setup-your-node-and-connect-to-pangaea/node-setup/once-click-deploy-aws-only-mac-and-linux-only#running-one-click-setup) again.

**Note: You would \(should\) not need to setup the AWS credentials again.**

