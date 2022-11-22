# Go Decrypt Jenkins

This tool will try to automatically find and decrypt all the interesting bits from a jenkins backup folder.

Features:

* Decrypts newer and older Jenkins password formats
* Looks through all xml files for things that look encrypted
* Decrypts files encrypted in SecretBytes tags
* Supports additional Jenkins plugins with `-p`, e.g. `-p jenkins.security.ApiTokenProperty`
* Dumps user password hashes and tokens

## Usage

```
% ./go-decrypt-jenkins -d jenkinsbackup/
scope: GLOBAL
id: 42e60ee3-fe19-4e3e-9eec-fec91e96e92e
username: jenkin
privateKey: -----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAx5T0czKNmNkA7k0mbBJkl8hTLAzy...

scope: GLOBAL
id: al2e8dee-afe1-e3be-b5e1-7e797e9a9ede
username: admin
password: Password123
```

You can also specify the `credentials.xml`, `master.key`, and `hudson.util.Secret` manually.

```
% ./go-decrypt-jenkins -m master.key -s hudson.util.Secret -c credentials.xml
```

## Installing

[Download](https://github.com/thesubtlety/go-decrypt-jenkins/releases) a binary

or

`go install github.com/thesubtlety/go-decrypt-jenkins/cmd/go-decrypt-jenkins`
