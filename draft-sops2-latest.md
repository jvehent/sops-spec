docname: draft-sops2-latest
title: The Sops 2 Document Format
abbrev: Sops 2
author:
 -
       ins: J. Vehent
       name: Julien Vehent
       organization: Mozilla
       email: julien@vehent.org

--- abstract

--- middle

# Introduction

The primary goal of the Sops document format is to provide a secure and
practical way to store configuration files at rest. Its intended audience is
operational groups that engineer deployment systems for their infrastructure. 

The Sops 2 document format is designed to be used with structured file formats,
such as JSON or YAML. In those formats, Sops 2 guarantees the confidentiality
of configuration values stored in a given file, but does not protect the
confidentiality of the document structure. In other words: document keys are
stored in cleartext and values are encrypted. The reasons for this design
choice are detailed in section X.Y.

Sops 2 provides strong integrity guarantees to protect against malicious
addition, removal and reordering of configuration values.

#  Conventions and Terminology

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in BCP 14 {{RFC2119}} {{RFC8174}}
when, and only when, they appear in all capitals, as shown here.

The following terms are used:

  - document: a file that contains data requiring protection

  - document key: a symetric key that encrypts and decrypts the values of a
    document

  - master key: a symetric or asymetric key that encrypts and decrypts a
    document key a one of its fragment

  - key group: a set of master keys that encrypt or decrypt a document key or
    one of its fragment

  - threshold: a configurable number of key groups needed to recover a document
    key

  - mac: a message authentication code that protects the integrity of a document

# Sops Design Rationale and Overview (#sops-rational)

foo

# Sops Metadata (#sops-metadata)

foo

# Document Encoding and Decoding (#encoding-decoding)

foo

# Document Key Splitting (#document-key-splitting)

foo

# Contributors

Many people have contributed to the Sops open source initiative and they are
acknowledged on github.com/mozilla/sops.

In addition, we would like to thank Adrian Utrilla, AJ Bahnken, Jeremy Orem and
Daniel Thorn from Mozilla.
