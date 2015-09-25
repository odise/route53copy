# route53copy, copies one domain between two AWS Route53 accounts

`route53copy` copies resource records from one AWS account to another. It
creates a `ChangeResourceRecordSet` with `UPSERT` for all `ResourceRecord`s of
the source account and sends it to the destination account.

The domain must already exist in both accounts and [AWS Named Profiles](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html#cli-multiple-profiles) must be configured for both the source account and the destination account.

## Installation

`route53copy` is a single binary. Install it by right-clicking and `Save as...`
or with `curl`.

### Links

* [OS X](https://github.com/andersjanmyr/route53copy/releases/download/v1.0.0/route53copy-osx)
* [Linux](https://github.com/andersjanmyr/route53copy/releases/download/v1.0.0/route53copy-linux)
* [Windows](https://github.com/andersjanmyr/route53copy/releases/download/v1.0.0/route53copy.exe)

### Curl

```
# OS X
$ curl -L https://github.com/andersjanmyr/route53copy/releases/download/v1.0.0/route53copy-osx \
  > /usr/local/bin/route53copy

# Linux
$ curl -L https://github.com/andersjanmyr/route53copy/releases/download/v1.0.0/route53copy-linux \
  > /usr/local/bin/route53copy

# Make executable
$ chmod a+x /usr/local/bin/route53copy

```

## Usage

```
$ route53copy
Usage: route53copy-linux <source_profile> <dest_profile> <domain>
```

```
$ route53copy aws_profile1 aws_profile2 example.com
Number of Records:  55
Skipping NS record for: example.com.
Skipping SOA record for: example.com.
53 records in 'example.com' are copied from aws_profile1-dev to aws_profile2
{
  Comment: "Importing ALL records from aws_profile",
  Id: "/change/C3QI8LAP4H5G9",
  Status: "PENDING",
  SubmittedAt: 2015-09-25 08:47:19.908 +0000 UTC
}
```

## Release Notes

A list of changes are in the [RELEASE_NOTES](RELEASE_NOTES.md).
