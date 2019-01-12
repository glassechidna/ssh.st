# How It Works

## Why?

There's at least two good reasons why you might be interested in how ssh.st works.

The first is doing your due diligence around the security of your servers and the
confidentiality of data in transit. Given the often sensitive nature of data 
transferred over SSH connections, this makes perfect sense. **If you reach the end
of this document and are not satisfied that your data is safe, or still have 
questions, reach out to us on [GitHub][github]**.

The second reason is that you are insatiably curious. Maybe thinking about novel
applications for and new combinations of existing protocols gets you as excited
as it does us. Or maybe you just really like sequence diagrams. 

## In 30 seconds or less

ssh.st consists of at least four logical systems. They are:

* The client program. This is the one you install on your laptop and setup `ssh`
  to use whenever you connect to `*.ssh.st`.

* The listener program. This is the one you download and run on the machine you
  want to connect to. 

* The ssh.st API. This central service coordinates which brokers serve which 
  listeners and clients connect to. It also powers the ssh.st website.

* The ssh.st brokers. These are responsible for forwarding the bits and bytes
  between client and listener. They are located in a handful of cities across
  the globe to minimise the latency we introduce.
  
Here's what that looks like in a sequence diagram:

![Sequence diagram showing relationship between the four systems](tldr-seq-diag.png)

[github]: https://github.com/glassechidna/ssh.st
