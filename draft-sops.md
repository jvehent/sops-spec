---
docname: draft-sops-latest
title: The Sops Document Format
abbrev: Sops
date: {DATE}

stand_alone: yes
pi: [toc, sortrefs, symrefs, docmapping]

author:
-
       ins: J. Vehent
       name: Julien Vehent
       organization: Mozilla
       email: julien@vehent.org

--- abstract

The Sops document format stores configuration files in a structured format
that protect the confidentiality of values and the integrity of the entire
document.

--- middle

# Introduction

The primary goal of Sops is to provide a secure and practical way to manage
configuration files. Its intended audience is operational groups that engineer
deployment systems for their infrastructure.

The Sops document format is best used with structured file formats, such as JSON
or YAML. In those formats, Sops guarantees the confidentiality of configuration
values stored in a given file, but does not protect the confidentiality of the
document structure. Storing the document structure in cleartext allows for
better integration with infrastructure management and versions control tools.

In addition to confidentiality, Sops guarantees the integrity of a document to
protect against malicious addition, removal and reordering of configuration
values.

Sops is a specialized document format and is not meant to cover the
confidentiality needs of the general population.

#  Conventions and Terminology

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 when, and only when, they
appear in all capitals, as shown here.

The following terms are used:

  - document: a file that contains data requiring protection.

  - document key: a symetric key that encrypts and decrypts the values of a
    document.

  - master key: a symetric or asymetric key that encrypts and decrypts a
    document key a one of its fragment.

  - key group: a set of master keys that encrypt or decrypt a document key or
    one of its fragment.

  - threshold: a configurable number of key groups needed to recover a document
    key.

  - mac: a message authentication code that protects the integrity of a document.

# Sops Design Rationale and Overview (#sops-rational)

The operation of internet services requires operational teams to manage
configuration files that contain sensitive information, such as cryptographic
keys and password. Leaking or modifying this information can have critical
consequence on services and their users, and it is thus a primary concern of
operation teams to maintain the security of configuration files.

The Sops document format provides confidentiality and integrity guarantees to
safely manage configuration files while offering features that facilitate
integration with operational practices, such as:

  - integration with YAML and JSON format. Sops documents conserve the structure
    of documents created in YAML and JSON formats.

  - integration with versions control systems (VCS). When used with structured
    document formats, such as YAML and JSON, Sops exposes the document structure
    in cleartext and only encrypts leaf values, allowing VCS to display
    meaningful diffs and handle merge conflicts.

  - flexible document key management. Each file is protected by a document key
    that is itself protected by one or several master keys. The Sops document
    format is extensible to allows for master keys format to be added easily as
    the industry provides new methods key management.
# Sops Metadata (#sops-metadata)

foo

## Document key encryption (#doc-key-encrypt)

At a minimum, implementations of the Sops document format SHOULD support master
key protocols OpenPGP, RSA OAEP and AES256-GCM.

# Document Encoding and Decoding (#encoding-decoding)

foo

# Document Key Splitting (#document-key-splitting)

foo

# Contributors

Many people have contributed to the Sops open source initiative and they are
acknowledged on github.com/mozilla/sops.

In addition, we would like to thank Adrian Utrilla, AJ Bahnken, Jeremy Orem and
Daniel Thorn from Mozilla.
