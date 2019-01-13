# Privacy

As one might hope given the nature of our service, we take privacy very seriously. 
Your data is **yours** and we've architected our service in a way that minimises 
our visibility into your data to only where it is technically necessary to provide 
this service.

## SSH credentials

At no point will we ever ask you to share the private component of your SSH keys
with us. If anyone ever asks you to do this, they are either trying to hack you
or do not know any better. Regardless of why, **you should never share your private
keys with anyone**.

If you wish to share your ssh.st account with someone else (e.g. so they can log
into one of your listeners), we **strongly** recommend you ask them for their
_public_ key. You can then sign their key with your personal SSH certificate
authority (generated during `sshst setup`) and specify an expiry time. 

The audit trail maintained by ssh.st and visible in your dashboard shows which 
certificates were used to connect to which listeners and when. This, and SSH
certificates are explained in a bit more detail at [How It Works][how].

## ssh.st website credentials

As part of our aim to minimise our exposure to our users' information, we have
"outsourced" our website authentication to [AWS Cognito][cognito]. This means
that we can avoid ever having to receive or store your password. As with SSH 
keys above, neither we nor AWS will ever ask you to divulge your password to us.

During the registration process, we ask you to provide a name and email address.
These will only ever be used for two purposes. The first is to prevent abuse of
the ssh.st service. The second is to contact you in extraordinary situations. A
non-exhaustive list of such situations:

* We believe that your account has been compromised.

* Providing information in response to a GDPR subject access request (until we
  have automated this process through the site.)
  
* Termination of your account for breaching our terms of use.

* Termination of the ssh.st service itself.

With the exception of the second example, we hope this means we will never have
to send you any emails after the first address confirmation one sent by AWS.

## Third parties

As part of providing the ssh.st service to you, data about you may be collected
and stored by third parties. A complete list of these parties are:

* [Amazon Web Services][aws]. Our hosting infrastructure is provided by AWS. We 
  store our data inside AWS, host our servers there and have outsourced website 
  credential handling to AWS Cognito as described above.
  
* [Intercom][intercom]. We use Intercom to interact with and provide support to 
  current and potential users of ssh.st. Intercom provides the icon seen on the 
  bottom-right corner of our website.
  
* [Datadog][datadog]. We use Datadog to monitor our infrastructure to ensure healthy 
  operation of our servers and to understand usage of the ssh.st service. 
  Information collected is ssh.st-service-wide and aggregated. No personally
  identifying data is transmitted to Datadog.
  
  This telemetry information is only collected server-side. The only telemetry
  sent by the client applications is the version of the client application, to 
  ensure backwards compatibility as we upgrade our service.
  
## Future plans

For completeness' sake, it is worth discussing some of the future plans described
in our public [roadmap][roadmap]. 

### Email address usage

In the future, we may consider starting an ssh.st blog and sending out weekly
or monthly digests of the blog. In this case, receiving emails will be **opt-in**
and we will _not_ email you to alert to to the creation of this. 

### Crash logging

We may introduce "crash logging" to our client applications in the future. This
will be exclusively on an **opt-in** and **manual** basis. The purpose of this 
will be to assist us in responding to bug reports. If this happens, we will
update the above information about telemetry collection.

### Web terminal

At some point we will introduce a web-based terminal experience for users who 
might find that useful. This will be entirely _optional_ functionality. Due to
implementation considerations, this will necessitate some greater degree of
trust in ssh.st than a command-line experience. **We will not change any of the
above to accommodate this.** At no point will we change our service in such a 
way that requires you to store your private keys with us. 

[cognito]: https://aws.amazon.com/cognito/
[how]: how-it-works
[aws]: https://aws.amazon.com/
[intercom]: https://intercom.io/
[datadog]: https://www.datadoghq.com/
[roadmap]: https://github.com/glassechidna/ssh.st/blob/master/ROADMAP.md
