# Getting Started with SSH.st

This guide will help you get up and debugging serverless and containerised apps
and build agents in no time.

## First-time client setup

### Installation

First, lets download `sshst` onto your machine. Even though you likely
already have an SSH client, the `sshst` program wraps sessions in
websockets. Simply run:

```
curl https://ssh.st/client.sh | sh
```

This will detect which OS you are running, install the right `sshst` and
start the first-time setup process. First-time setup will create some new
SSH keys and adjust your SSH config.

### Configuration

Once the above is done, it should have some output like:

```
hello world
```

Now you can copy this public key into the [SSH.st dashboard](/user/dashboard).
Once you've done (and clicked _Save_) we can test that your client is correctly
set up.

### Test it

In a terminal, run `ssh ssh.st whoami`. If everything is working, you should
see the following:

Hello! We think you are:

```
User ID: US-01D065W618RGFBQ4NYH59GQXXX
IP address: 60.224.131.257
Email: you@youremail.com
Subscription: free
Key fingerprint: SHA256:tLRhc0ui9lpU/dRbL67z1L9kYbGTuBm47xyIwrOrnHE
Key ID: aidan.steele
CA Key fingerprint: SHA256:U1+z+7i7gOxOuj/V/HJvvlPmRtqrns0uKTOf0sMjNS0
```

## Listener setup

The other piece in the SSH.st puzzle is the _listener_. This is the program
that runs in the Lambda function, the container, the build agent, etc that you
want to connect to, i.e. the target. Lets set one up now and see how it all
fits together.

Run the following command. Note that `YOURTOKEN` is the "listener token" available
at the [SSH.st dashboard](/user/dashboard).

```
curl https://ssh.st/listener.sh | TOKEN=YOURTOKEN NAME=shell sh
```

If all goes well, the program should still be running and you should see the
following output:

```
Generated host key: SHA256:oVVLzKD9C6ybItxXrKxsAs2UkGmOMSrC/nT2bFdA/u4
Established connection to HQ as shell (LI-01D05WD8Z2ZQKK06QMWD3AXXX)
```

### Putting it all together

With the listener still running in the background, lets test two things in
a different terminal:

* That we can see the listener running
* That we can **connect** to the listener

To achieve the first point, we run `ssh ssh.st ls`. This will list all
the running listeners for your account. It looks like this:

```
# 0 sessions connected to 1 listeners
- Name: shell
  Id: LI-01D05WD8Z2ZQKK06QMWD3AXXX
  HostKeyFingerprint: SHA256:/1TwhN45CafWoyOUE/gh7plduxepR70uMyFY8kyUsNw
  Sessions: [] # no active connections
```

See how it says `# no active connections`? Lets fix that right now. Run
`ssh shell.ssh.st`. You should find yourself at a rather anti-climactic
terminal, but rest assured that you've successfully opened an SSH connection..
to your own laptop. 💯

Why not try the same now in a build agent?

# Notes

* A listener will keep on listening even after you've `exit`ed your SSH
  session. Run `ssh ssh.st kill shell` to terminate the listener we started
  earlier.
* You're not limited to a single SSH session into the listener - you can open
  multiple at the same time, you can do port-forwarding, you can do remote
  debugging, anything that you'd usually do over SSH.
