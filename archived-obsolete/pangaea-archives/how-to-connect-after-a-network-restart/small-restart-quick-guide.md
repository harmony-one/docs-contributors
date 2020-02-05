---
description: When the update is small.
---

# Small Restart Quick Guide

## Disclaimer

#### IF YOU HAVE NOT DOWNLOADED THE NEW FILES \(RELEASED SEPTEMBER 10TH\),                            PLEASE FOLLOW THE INSTRUCTIONS HERE:

{% page-ref page="phase-2-restart-guide.md" %}

**THIS PAGE IS EXCLUSIVELY FOR PEOPLE WHO HAVE UPDATED THEIR NODE.SH AND WALLET.SH PREVIOUSLY.**

## Cleaning the Database and Connecting to the New Network

### Killing the Current Node

Attach to your tmux session.

```text
tmux attach -t node
```

**\[If you don't have `tmux` session running, follow instructions** [**here**](https://docs.harmony.one/pangaea/troubleshooting/how-to-restart-your-node/troubleshooting#how-to-kill-node-process-from-outside-of-tmux) **to kill current node process. \]**

Once you are attached, kill the node process:

```text
<Ctrl> + C
```

Double check whether the node process has stopped running by doing the following:

```text
ps -ef | grep harmony
```

You should see something like this:

![](../../../.gitbook/assets/ec2-user.png)

### Cleaning the Database

**\[Optional but Recommended Step**\]: Create more space for your new blockchain by clearing out old blockchain:

```text
sudo rm -rf harmony_db_*
```

### Launching the Node

Launch node.sh with the -c flag.

{% hint style="warning" %}
The `-c` option backups the old blockchain, and **should only be done when the entire network is being restarted**. Unless we specifically say to do so after a network reset, it **should not be used**.
{% endhint %}

```text
sudo ./node.sh -t -c
```

