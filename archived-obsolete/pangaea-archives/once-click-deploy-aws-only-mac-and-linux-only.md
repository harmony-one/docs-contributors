---
description: >-
  This is the quicker way to setup your Pangaea node. If you plan to use AWS and
  using Mac or Linux OS, you can follow the steps in this page.
---

# One-Click Setup

## **Prerequisites**

* You would need a MacOS/Linux Computer.  
* You should have basic knowledge of running commands from the command line. 
* Have your BLS and Wallet Key Downloaded by Redeeming [your coupon code](https://pangaea.harmony.one/pkg). 
* Have your [AWS Credentials ready.](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html) 
  * You need to have access to your AWS account and then create a IAM user with a `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`. **Don't worry** the process is very simple and should take you about 1 minute. Please see the following video on how to do it

Your AWS Keys would like the following:

```text
AWS_ACCESS_KEY_ID = AKIAZRWVEKULIDHPU5PJ
AWS_SECRET_ACCESS_KEY = awZfBZIAt5OaSSZrs44DN3oZ8hYv5Drm4xhYmJ8v.
```

{% embed url="https://www.youtube.com/watch?v=3dmBrqBGpsw&feature=youtu.be" caption="" %}

* Download the **ONE CLICK DEPLOY** setup folder from here

{% file src="../../.gitbook/assets/one-click-deploy-4.zip" %}

## **Running One Click Setup**

{% embed url="https://www.youtube.com/watch?v=S01O2PEZjtQ" caption="" %}

Unzip the `one-click-deploy.zip` using your favorite unzip program or on command line by saying `unzip`. It is quite likely the zip file will automatically unzip when you try to open it, if not open a terminal and go to the folder where you downloaded the zip and do this:

```text
cd <path to folder which contains one-click-deploy.zip>
unzip one-click-deploy.zip
```

Unzipping would open a folder called `one-click-deploy`.

Next `cd` into one-click-deploy

Run the `one-click-setup`script as follows on your terminal.

```text
chmod u+x setup-one-click-deploy.sh
sudo ./setup-one-click-deploy.sh
```

After running `sudo ./setup-one-click-depoloy.sh`, it will ask you for you password. Enter in your password you use to sign in to your computer.

**Place only your 2 keys in the `key-folder` within** `one-click-deploy.`

Go into your unzipped `keys` folder and you will see 2 key files.

Now you are ready to run the `node`. You can run the node by running the following on command line.

```text
chmod u+x run-one-click-node.sh
./run-one-click-node.sh
```

This will install `terraform` \(don't worry about what that means\) and create a `key-folder` in the `one-click-deploy` folder.

Now just answer basic **Y/N** questions to have your node running on the _Pangaea-net._

The script will auto-detect whether your AWS credentials are already set. If this is the first time you are running the script, it will prompt your for `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`

```text
Enter your AWS ACCESS KEY
AKIAZRWVEKULIDHGU5PJ
Enter your AWS SECRET ACCESS KEY
awZfBZIAt5OaSSZrs44DN3oZ8hYv5Drm4xhYmJ8v
```

This has now setup your `~/.aws/credentials` file, with the following information

```text
[profile harmony-foundational]
aws_access_key_id = AKIAZRWVEKULIDHGU5PJ
aws_secret_access_key = awZfBZIAt5OaSSZrs44DN3oZ8hYv5Drm4xhYmJ8v
```

The ssh keys are used to login into the AWS Instance we are planning to use to run the node.

New keys would normally be generated in the folder `ssh-keys/harmony-foundation.`However if keys already exist, you have option to use them or overwrite them. Just enter what you want to do when you are prompted.

```text
Overwrite (y/n)?
y
```

The script has all inputs it now wants to run the node. You will be logged into your AWS machine.  
The node process is running in something called `tmux`. In order to see whether the node is running type the following on the command prompt.

```text
tmux attach
```

You can see that your node might be syncing. If everything looks good. _\*\*_You can `detach` from tmux by doing, `<CTRL><b>` then `d`

```text
<CTRL><b> d
```

**You can exit your aws instance just by typing**

```text
exit
```

**Logging back into AWS node**

There would be a file in the folder `one-click-deploy` called `instance-ip.txt` If you open the file you will find your "IP". The IP would look something like: `13.15.27.89`

```text
ssh -i ssh-keys/harmony-foundation ec2-user@<your ip>
```

## How to setup your wallet after you have done one-click-setup?

If you are attached to your tmux session, detach first.

```text
tmux detach
```

After detaching, read the last steps page in order to make sure your node is properly running.

{% page-ref page="last-steps.md" %}

## Common Errors and Problems

* **Error creating Security Group: InvalidGroup.Duplicate:  The security group 'Harmony Foundational Node Security Group' already exists**
  * The script is unable to create a security group due to one of the same name already existing
  * To fix it, the group needs to be manually deleted: **\(MAKE SURE YOU'RE ON N. CALIFORNIA\)**
    1. Navigate to "Security Groups"
    2. Select "Harmony Foundational Node Security Group"
    3. Click "Actions"
    4. Click "Delete Security Group"
    5. Click "Yes, Delete"

![](../../.gitbook/assets/brave_9qcqegi80u.png)

* **Error: Error import KeyPair: InvalidKeyPair.Duplicate: The keypair 'harmony-foundation' already exists.**
  * The script is unable to create a key pair due to one of the same name already existing
  * To fix it, the key pair needs to be manually deleted: **\(MAKE SURE YOU'RE ON N. CALIFORNIA\)**
    1. Navigate to "Key Pairs"
    2. Select "harmony-foundation"
    3. Click "Yes"

![](../../.gitbook/assets/brave_vluhobrex0.png)

* **Error: SSH agent requested but SSH\_AUTH\_SOCK not-specified**
  * The SSH agent is not running, so to start it, run this command:

```text
eval $(ssh-agent -s)
```

![](../../.gitbook/assets/mobaxterm_oqwpfrx7d3.png)

