---
title: The Transport Layer Security (TLS) Protocol Version 1.3
abbrev: TLS
docname: draft-ietf-tls-tls13-latest
category: std
updates: 4492, 5705, 6066, 6961
obsoletes: 5077, 5246

ipr: pre5378Trust200902
area: General
workgroup:
keyword: Internet-Draft

stand_alone: yes
pi:
  rfcedstyle: yes
  toc: yes
  tocindent: yes
  sortrefs: yes
  symrefs: yes
  strict: yes
  comments: yes
  inline: yes
  text-list-symbols: -o*+
  docmapping: yes
author:
 -
       ins: E. Rescorla
       name: Eric Rescorla
       organization: RTFM, Inc.
       email: ekr@rtfm.com

normative:
  RFC2104:
  RFC2119:
  RFC5226:
  RFC3447:
  RFC5280:
  RFC5869:
  RFC6066:
  RFC6655:
  RFC7539:
  RFC7748:
  RFC7919:
  RFC8032:

  AES:
       title: Specification for the Advanced Encryption Standard (AES)
       date: 2001-11-26
       author:
         org: National Institute of Standards and Technology
       seriesinfo:
         NIST: FIPS 197
  SHS:
       title: Secure Hash Standard
       date: 2012-03
       author:
         org: National Institute of Standards and Technology, U.S. Department of Commerce
       seriesinfo:
         NIST: FIPS PUB 180-4
  X690:
       title: "Information technology - ASN.1 encoding Rules: Specification of Basic Encoding Rules (BER), Canonical Encoding Rules (CER) and Distinguished Encoding Rules (DER)"
       date: 2002
       author:
         org: ITU-T
       seriesinfo:
         ISO/IEC: 8825-1:2002
  X962:
       title: "Public Key Cryptography For The Financial Services Industry: The Elliptic Curve Digital Signature Algorithm (ECDSA)"
       date: 1998
       author:
         org: ANSI
       seriesinfo:
         ANSI: X9.62
  DH:
        title: "New Directions in Cryptography"
        author:
          - ins: W. Diffie
          - ins: M. Hellman
        date: 1977-06
        seriesinfo: IEEE Transactions on Information Theory, V.IT-22 n.6


informative:
  RFC4086:
  RFC4279:
  RFC4346:
  RFC4366:
  RFC4492:
  RFC4507:
  RFC4681:
  RFC5054:
  RFC5077:
  RFC5081:
  RFC5116:
  RFC5246:
  RFC5764:
  RFC5878:
  RFC5929:
  RFC6176:
  RFC6091:
  RFC6520:
  RFC7301:
  RFC7230:
  RFC7250:
  RFC7366:
  RFC7465:
  RFC7568:
  RFC7627:
  RFC7685:

  DSS:
       title: "Digital Signature Standard, version 4"
       date: 2013
       author:
         org: National Institute of Standards and Technology, U.S. Department of Commerce
       seriesinfo:
         NIST: FIPS PUB 186-4
  ECDSA:
       title: "Public Key Cryptography for the Financial Services Industry: The Elliptic Curve Digital Signature Algorithm (ECDSA)"
       author:
         org: American National Standards Institute
       date: 2005-11
       seriesinfo:
         ANSI: ANS X9.62-2005

  GCM:
       title: "Recommendation for Block Cipher Modes of Operation: Galois/Counter Mode (GCM) and GMAC"
       date: 2007-11
       author:
         ins: M. Dworkin
       seriesinfo:
         NIST: Special Publication 800-38D

  KEYAGREEMENT:
       title: "Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography"
       author:
         -
           ins: E. Barker
         -
           ins: Lily Chen
         -
           ins: A. Roginsky
         -
           ins: M. Smid
       date: 2013-05
       seriesinfo:
         NIST: Special Publication 800-38D

  PKCS6:
       title: "PKCS #6: RSA Extended Certificate Syntax Standard, version 1.5"
       author:
         org: RSA Laboratories
       date: 1993-11
  PKCS7:
       title: "PKCS #7: RSA Cryptographic Message Syntax Standard, version 1.5"
       author:
         org: RSA Laboratories
       date: 1993-11
  RSA:
       title: "A Method for Obtaining Digital Signatures and Public-Key Cryptosystems"
       author:
         -
           ins: R. Rivest
         -
           ins: A. Shamir
         -
           ins: L. M. Adleman
       date: 1978-02
       seriesinfo:
         Communications of the ACM: v. 21, n. 2, pp. 120-126.
  SSL2:
       title: "The SSL Protocol"
       author:
         name: Kipp Hickman
         org: Netscape Communications Corp.
       date: 1995-02-09
  SSL3:
       title: The SSL 3.0 Protocol
       author:
         -
           ins: A. Freier
           org: Netscape Communications Corp.
         -
           ins: P. Karlton
           org: Netscape Communications Corp.
         -
           ins: P. Kocher
           org: Netscape Communications Corp.
       date: 1996-11-18
  TIMING:
       title: "Remote timing attacks are practical"
       author:
         -
           ins: D. Boneh
         -
           ins: D. Brumley
       seriesinfo:
         USENIX: Security Symposium
       date: 2003
  X501:
       title: "Information Technology - Open Systems Interconnection - The Directory: Models"
       date: 1993
       seriesinfo:
         ITU-T: X.501
  IEEE1363:
       title: "Standard Specifications for Public Key Cryptography"
       date: 2000
       author:
         org: IEEE
       seriesinfo:
         IEEE 1363
  PSK-FINISHED:
       title: "Revision 10: possible attack if client authentication is allowed during PSK"
       date: 2015
       target: https://www.ietf.org/mail-archive/web/tls/current/msg18215.html
       author:
       -
         ins: C. Cremers
       -
         ins: M. Horvat
       -
         ins: T. van der Merwe
       -
         ins: S. Scott
  CHHSV17:
       title: "Awkward Handshake: Possible mismatch of client/server view on client authentication in post-handshake mode in Revision 18"
       date: 2017
       target: https://www.ietf.org/mail-archive/web/tls/current/msg22382.html
       author:
       -
         ins: C. Cremers
       -
         ins: M. Horvat
       -
         ins: J. Hoyland
       -
         ins: T. van der Merwe
       -
         ins: S. Scott
  SLOTH:
       title: "Transcript Collision Attacks: Breaking Authentication in TLS, IKE, and SSH"
       author:
       -
         ins: K. Bhargavan
       -
         ins: G. Leurent
       seriesinfo: Network and Distributed System Security Symposium (NDSS 2016)
       date: 2016
  AEAD-LIMITS:
       title: "Limits on Authenticated Encryption Use in TLS"
       author:
       -
         ins: A. Luykx
       -
         ins: K. Paterson
       target: http://www.isg.rhul.ac.uk/~kp/TLS-AEbounds.pdf
       date: 2016
  CK01:
       title: "Analysis of Key-Exchange Protocols and Their Use for Building Secure Channels"
       author:
       -
         ins: R. Canetti
       -
         ins: H. Krawczyk
       seriesinfo: Proceedings of Eurocrypt 2001
       date: 2001
  CCG16:
       title: "On Post-Compromise Security"
       author:
       -
         ins: K. Cohn-Gordon
       -
         ins: C. Cremers
       -
         ins: L. Garratt
       seriesinfo: IEEE Computer Security Foundations Symposium
       date: 2015
  BBFKZG16:
       title: "Downgrade Resilience in Key-Exchange Protocols"
       author:
       -
         ins: K. Bhargavan
       -
         ins: C. Brzuska
       -
         ins: C. Fournet
       -
         ins: M. Kohlweiss
       -
         ins: S. Zanella-Beguelin
       -
         ins: M. Green
       seriesinfo: Proceedings of IEEE Symposium on Security and Privacy (Oakland) 2016
       date: 2016
  DOW92:
       title: “Authentication and authenticated key exchanges”
       author:
       -
         ins: W. Diffie
       -
         ins: P. van Oorschot
       -
         ins: M. Wiener
       seriesinfo: Designs, Codes and Cryptography
       date: 1992
  HGFS15:
       title: "Prying Open Pandora's Box: KCI Attacks against TLS"
       author:
       -
         ins: C. Hlauschek
       -
         ins: M. Gruber
       -
         ins: F. Fankhauser
       -
         ins: C. Schanes
       seriesinfo: Proceedings of USENIX Workshop on Offensive Technologies
       date: 2015
  SIGMA:
       title: "SIGMA: the 'SIGn-and-MAc' approach to authenticated Diffie-Hellman and its use in the IKE protocols"
       author:
       -
         ins: H. Krawczyk
       seriesinfo: Proceedings of CRYPTO 2003
       date: 2003
  CHSV16:
       title: "Automated Analysis and Verification of TLS 1.3: 0-RTT, Resumption and Delayed Authentication"
       author:
       -
         ins: C. Cremers
       -
         ins: M. Horvat
       -
         ins: S. Scott
       -
         ins: T. van der Merwe
       seriesinfo: Proceedings of IEEE Symposium on Security and Privacy (Oakland) 2016
       date: 2016
  FGSW16:
       title: "Key Confirmation in Key Exchange: A Formal Treatment and Implications for TLS 1.3"
       author:
       -
         ins: M. Fischlin
       -
         ins: F. Guenther
       -
         ins: B. Schmidt
       -
         ins: B. Warinschi
       seriesinfo: Proceedings of IEEE Symposium on Security and Privacy (Oakland) 2016
       date: 2016
  LXZFH16:
       title: "Multiple Handshakes Security of TLS 1.3 Candidates"
       author:
       -
         ins: X. Li
       -
         ins: J. Xu
       -
         ins: D. Feng
       -
         ins: Z. Zhang
       -
         ins: H. Hu
       seriesinfo: Proceedings of IEEE Symposium on Security and Privacy (Oakland) 2016
       date: 2016
  FW15:
       title: "Factoring RSA Keys With TLS Perfect Forward Secrecy"
       author:
       -
         ins: Florian Weimer
         org: Red Hat Product Security
       date: 2015-09
  REKEY:
      title: "Increasing the Lifetime of a Key: A Comparative Analysis of the Security of Re-keying Techniques"
      author:
      -
        ins: M. Abdalla
      -
        ins: M. Bellare
      seriesinfo: ASIACRYPT2000
      date: 2000-10
  RECORD:
      title: "Implementing and Proving the TLS 1.3 Record Layer"
      author:
      -
        ins: K. Bhargavan
      -
        ins: A. Delignat-Lavaud
      -
        ins: C. Fournet
      -
        ins: M. Kohlweiss
      -
        ins: J. Pan
      -
        ins: J. Protzenko
      -
        ins: A. Rastogi
      -
        ins: N. Swamy
      -
        ins: S. Zanella-Beguelin
      -
        ins: J.K. Zinzindohoue
      date: 2016-12
      target: http://eprint.iacr.org/2016/1178

--- abstract

This document specifies version 1.3 of the Transport Layer Security
(TLS) protocol.  TLS allows client/server applications to
communicate over the Internet in a way that is designed to prevent eavesdropping,
tampering, and message forgery.
--- middle


#  Introduction

DISCLAIMER: This is a WIP draft of TLS 1.3 and has not yet seen significant security analysis.

RFC EDITOR: PLEASE REMOVE THE FOLLOWING PARAGRAPH
The source for this draft is maintained in GitHub. Suggested changes
should be submitted as pull requests at
https://github.com/tlswg/tls13-spec. Instructions are on that page as
well. Editorial changes can be managed in GitHub, but any substantive
change should be discussed on the TLS mailing list.

The primary goal of TLS is to provide a secure channel
between two communicating peers. Specifically, the channel should
provide the following properties:

- Authentication: The server side of the channel is always
  authenticated; the client side is optionally
  authenticated. Authentication can happen via asymmetric cryptography
  (e.g., RSA {{RSA}}, ECDSA {{ECDSA}}) or a pre-shared key (PSK).

- Confidentiality: Data sent over the channel is only visible to the
  endpoints. TLS does not hide the length of the data it transmits,
  though endpoints are able to pad in order to obscure lengths.

- Integrity: Data sent over the channel cannot be modified by attackers.

These properties should be true even in the face of an attacker who has complete
control of the network, as described in {{?RFC3552}}.
See {{security-analysis}} for a more complete statement of the relevant security
properties.

TLS consists of two primary components:

- A handshake protocol ({{handshake-protocol}}) that authenticates the communicating parties,
  negotiates cryptographic modes and parameters, and establishes
  shared keying material. The handshake protocol is designed to
  resist tampering; an active attacker should not be able to force
  the peers to negotiate different parameters than they would
  if the connection were not under attack.

- A record protocol ({{record-protocol}}) that uses the parameters established by the
  handshake protocol to protect traffic between the communicating
  peers. The record protocol divides traffic up into a series of
  records, each of which is independently protected using the
  traffic keys.

TLS is application protocol independent; higher-level protocols can
layer on top of TLS transparently. The TLS standard, however, does not
specify how protocols add security with TLS; how to
initiate TLS handshaking and how to interpret the authentication
certificates exchanged are left to the judgment of the designers and
implementors of protocols that run on top of TLS.

This document defines TLS version 1.3. While TLS 1.3 is not directly
compatible with previous versions, all versions of TLS incorporate a
versioning mechanism which allows clients and servers to interoperably
negotiate a common version if one is supported.

##  Conventions and Terminology

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this
document are to be interpreted as described in RFC 2119 {{RFC2119}}.

The following terms are used:

client: The endpoint initiating the TLS connection.

connection: A transport-layer connection between two endpoints.

endpoint: Either the client or server of the connection.

handshake: An initial negotiation between client and server that establishes the parameters of their subsequent interactions.

peer: An endpoint. When discussing a particular endpoint, "peer" refers to the endpoint that is not the primary subject of discussion.

receiver: An endpoint that is receiving records.

sender: An endpoint that is transmitting records.

server: The endpoint which did not initiate the TLS connection.


##  Major Differences from TLS 1.2

(*) indicates changes to the wire protocol which may require implementations
    to update.

draft-19

- Hash context_value input to Exporters (*)

- Add an additional Derive-Secret stage to Exporters (*).

- Hash ClientHello1 in the transcript when HRR is used. This
  reduces the state that needs to be carried in cookies. (*)

- Restructure CertificateRequest to have the selectors
  in extensions. This also allowed defining a "certificate_authorities"
  extension which can be used by the client instead of trusted_ca_keys (*).

- Tighten record framing requirements and require checking of them (*).

- Consolidate "ticket_early_data_info" and "early_data" into a single
  extension (*).

- Change end_of_early_data to be a handshake message (*).

- Add pre-extract Derive-Secret stages to key schedule (*).

- Remove spurious requirement to implement "pre_shared_key".

- Clarify location of "early_data" from server (it goes in EE,
  as indicated by the table in S 10).

- Require peer public key validation

- Add state machine diagram.


draft-18

- Remove unnecessary resumption_psk which is the only thing expanded from
  the resumption master secret. (*).

- Fix signature_algorithms entry in extensions table.

- Restate rule from RFC 6066 that you can't resume unless SNI is the same.


draft-17

- Remove 0-RTT Finished and resumption_context, and replace with a
  psk_binder field in the PSK itself (*)

- Restructure PSK key exchange negotiation modes (*)

- Add max_early_data_size field to TicketEarlyDataInfo (*)

- Add a 0-RTT exporter and change the transcript for the regular exporter (*)

- Merge TicketExtensions and Extensions registry. Changes
  ticket_early_data_info code point (*)

- Replace Client.key_shares in response to HRR (*)

- Remove redundant labels for traffic key derivation (*)

- Harmonize requirements about cipher suite matching: for resumption you
  need to match KDF but for 0-RTT you need whole cipher suite. This
  allows PSKs to actually negotiate cipher suites. (*)

- Move SCT and OCSP into Certificate.extensions (*)

- Explicitly allow non-offered extensions in NewSessionTicket

- Explicitly allow predicting ClientFinished for NST

- Clarify conditions for allowing 0-RTT with PSK


draft-16

- Revise version negotiation (*)

- Change RSASSA-PSS and EdDSA SignatureScheme codepoints for better backwards compatibility (*)

- Move HelloRetryRequest.selected_group to an extension (*)

- Clarify the behavior of no exporter context and make it the same
  as an empty context.(*)

- New KeyUpdate format that allows for requesting/not-requesting an
  answer. This also means changes to the key schedule to support
  independent updates (*)

- New certificate_required alert (*)

- Forbid CertificateRequest with 0-RTT and PSK.

- Relax requirement to check SNI for 0-RTT.


draft-15

- New negotiation syntax as discussed in Berlin (*)

- Require CertificateRequest.context to be empty during handshake (*)

- Forbid empty tickets (*)

- Forbid application data messages in between post-handshake messages
  from the same flight (*)

- Clean up alert guidance (*)

- Clearer guidance on what is needed for TLS 1.2.

- Guidance on 0-RTT time windows.

- Rename a bunch of fields.

- Remove old PRNG text.

- Explicitly require checking that handshake records not span
  key changes.



draft-14

- Allow cookies to be longer (*)

- Remove the "context" from EarlyDataIndication as it was undefined
  and nobody used it (*)

- Remove 0-RTT EncryptedExtensions and replace the ticket_age extension
  with an obfuscated version. Also necessitates a change to
  NewSessionTicket (*).

- Move the downgrade sentinel to the end of ServerHello.Random
  to accommodate tlsdate (*).

- Define ecdsa_sha1 (*).

- Allow resumption even after fatal alerts. This matches current
  practice.

- Remove non-closure warning alerts. Require treating unknown alerts as
  fatal.

- Make the rules for accepting 0-RTT less restrictive.

- Clarify 0-RTT backward-compatibility rules.

- Clarify how 0-RTT and PSK identities interact.

- Add a section describing the data limits for each cipher.

- Major editorial restructuring.

- Replace the Security Analysis section with a WIP draft.


draft-13

- Allow server to send SupportedGroups.

- Remove 0-RTT client authentication

- Remove (EC)DHE 0-RTT.

- Flesh out 0-RTT PSK mode and shrink EarlyDataIndication

- Turn PSK-resumption response into an index to save room

- Move CertificateStatus to an extension

- Extra fields in NewSessionTicket.

- Restructure key schedule and add a resumption_context value.

- Require DH public keys and secrets to be zero-padded to the size
  of the group.

- Remove the redundant length fields in KeyShareEntry.

- Define a cookie field for HRR.


draft-12

- Provide a list of the PSK cipher suites.

- Remove the ability for the ServerHello to have no extensions
  (this aligns the syntax with the text).

- Clarify that the server can send application data after its first
  flight (0.5 RTT data)

- Revise signature algorithm negotiation to group hash, signature
  algorithm, and curve together. This is backwards compatible.

- Make ticket lifetime mandatory and limit it to a week.

- Make the purpose strings lower-case. This matches how people
  are implementing for interop.

- Define exporters.

- Editorial cleanup


draft-11

- Port the CFRG curves & signatures work from RFC4492bis.

- Remove sequence number and version from additional_data, which
  is now empty.

- Reorder values in HkdfLabel.

- Add support for version anti-downgrade mechanism.

- Update IANA considerations section and relax some of the policies.

- Unify authentication modes. Add post-handshake client authentication.

- Remove early_handshake content type. Terminate 0-RTT data with
  an alert.

- Reset sequence number upon key change (as proposed by Fournet et al.)


draft-10

- Remove ClientCertificateTypes field from CertificateRequest
  and add extensions.

- Merge client and server key shares into a single extension.


draft-09

- Change to RSA-PSS signatures for handshake messages.

- Remove support for DSA.

- Update key schedule per suggestions by Hugo, Hoeteck, and Bjoern Tackmann.

- Add support for per-record padding.

- Switch to encrypted record ContentType.

- Change HKDF labeling to include protocol version and value lengths.

- Shift the final decision to abort a handshake due to incompatible
  certificates to the client rather than having servers abort early.

- Deprecate SHA-1 with signatures.

- Add MTI algorithms.


draft-08

- Remove support for weak and lesser used named curves.

- Remove support for MD5 and SHA-224 hashes with signatures.

- Update lists of available AEAD cipher suites and error alerts.

- Reduce maximum permitted record expansion for AEAD from 2048 to 256 octets.

- Require digital signatures even when a previous configuration is used.

- Merge EarlyDataIndication and KnownConfiguration.

- Change code point for server_configuration to avoid collision with
  server_hello_done.

- Relax certificate_list ordering requirement to match current practice.


draft-07

- Integration of semi-ephemeral DH proposal.

- Add initial 0-RTT support.

- Remove resumption and replace with PSK + tickets.

- Move ClientKeyShare into an extension.

- Move to HKDF.


draft-06

- Prohibit RC4 negotiation for backwards compatibility.

- Freeze & deprecate record layer version field.

- Update format of signatures with context.

- Remove explicit IV.


draft-05

- Prohibit SSL negotiation for backwards compatibility.

- Fix which MS is used for exporters.


draft-04

- Modify key computations to include session hash.

- Remove ChangeCipherSpec.

- Renumber the new handshake messages to be somewhat more
  consistent with existing convention and to remove a duplicate
  registration.

- Remove renegotiation.

- Remove point format negotiation.


draft-03

- Remove GMT time.

- Merge in support for ECC from RFC 4492 but without explicit
  curves.

- Remove the unnecessary length field from the AD input to AEAD
  ciphers.

- Rename {Client,Server}KeyExchange to {Client,Server}KeyShare.

- Add an explicit HelloRetryRequest to reject the client's.


draft-02

-  Increment version number.

-  Rework handshake to provide 1-RTT mode.

-  Remove custom DHE groups.

-  Remove support for compression.

-  Remove support for static RSA and DH key exchange.

-  Remove support for non-AEAD ciphers.


## Updates Affecting TLS 1.2

This document defines several changes that optionally affect implementations of
TLS 1.2:

* A version downgrade protection mechanism is described in {{server-hello}}.

* RSASSA-PSS signature schemes are defined in {{signature-algorithms}}.

An implementation of TLS 1.3 that also supports TLS 1.2 might need to include
changes to support these changes even when TLS 1.3 is not in use.  See the
referenced sections for more details.


# Protocol Overview

The cryptographic parameters of the connection state are produced by the
TLS handshake protocol, which a TLS client and server use when first
communicating to agree on a protocol version, select cryptographic
algorithms, optionally authenticate each other, and establish shared
secret keying material. Once the handshake is complete, the peers
use the established keys to protect application layer traffic.

A failure of the handshake or other protocol error triggers the
termination of the connection, optionally preceded by an alert message
({{alert-protocol}}).

TLS supports three basic key exchange modes:

- (EC)DHE (Diffie-Hellman both the finite field and elliptic curve
  varieties),

- PSK-only, and

- PSK with (EC)DHE

{{tls-full}} below shows the basic full TLS handshake:

~~~
       Client                                               Server

Key  ^ ClientHello
Exch | + key_share*
     | + psk_key_exchange_modes*
     v + pre_shared_key*         -------->
                                                       ServerHello  ^ Key
                                                      + key_share*  | Exch
                                                 + pre_shared_key*  v
                                             {EncryptedExtensions}  ^  Server
                                             {CertificateRequest*}  v  Params
                                                    {Certificate*}  ^
                                              {CertificateVerify*}  | Auth
                                                        {Finished}  v
                                 <--------     [Application Data*]
     ^ {Certificate*}
Auth | {CertificateVerify*}
     v {Finished}                -------->
       [Application Data]        <------->      [Application Data]

              +  Indicates noteworthy extensions sent in the
                 previously noted message.

              *  Indicates optional or situation-dependent
                 messages/extensions that are not always sent.

              {} Indicates messages protected using keys
                 derived from a [sender]_handshake_traffic_secret.

              [] Indicates messages protected using keys
                 derived from traffic_secret_N
~~~
{: #tls-full title="Message flow for full TLS Handshake"}

The handshake can be thought of as having three phases (indicated
in the diagram above):

- Key Exchange: Establish shared keying material and select the
   cryptographic parameters. Everything after this phase is
   encrypted.

- Server Parameters: Establish other handshake parameters
   (whether the client is authenticated, application layer protocol support, etc.).

- Authentication: Authenticate the server (and optionally the client)
   and provide key confirmation and handshake integrity.

In the Key Exchange phase, the client sends the ClientHello
({{client-hello}}) message, which contains a random nonce
(ClientHello.random); its offered protocol versions; a list of
symmetric cipher/HKDF hash pairs; some set of Diffie-Hellman key shares (in the
"key_share" extension {{key-share}}), a set of pre-shared key labels (in the
"pre_shared_key" extension {{pre-shared-key-extension}}) or both; and
potentially some other extensions.

The server processes the ClientHello and determines the appropriate
cryptographic parameters for the connection. It then responds with its
own ServerHello ({{server-hello}}), which indicates the negotiated connection
parameters. The combination of the ClientHello
and the ServerHello determines the shared keys. If (EC)DHE
key establishment is in use, then the ServerHello
contains a "key_share" extension with the server's ephemeral
Diffie-Hellman share which MUST be in the same group as one of the
client's shares. If PSK key establishment is
in use, then the ServerHello contains a "pre_shared_key"
extension indicating which of the client's offered PSKs was selected.
Note that implementations can use (EC)DHE and PSK together, in which
case both extensions will be supplied.

The server then sends two messages to establish the Server Parameters:

EncryptedExtensions:
: responses to any extensions that are not required to
  determine the cryptographic parameters, other than those
  that are specific to individual certificates. \[{{encrypted-extensions}}]

CertificateRequest:
: if certificate-based client authentication is desired, the
  desired parameters for that certificate. This message is
  omitted if client authentication is not desired. \[{{certificate-request}}]

Finally, the client and server exchange Authentication messages. TLS
uses the same set of messages every time that authentication is needed.
Specifically:

Certificate:
: the certificate of the endpoint and any per-certificate extensions.
  This message is omitted by the server if not authenticating with a
  certificate and by the client if the server did not send
  CertificateRequest (thus indicating that the client should not
  authenticate with a certificate). Note that if raw
  public keys {{RFC7250}} or the cached information extension
  {{?RFC7924}} are in use, then this message will not
  contain a certificate but rather some other value corresponding to
  the server's long-term key.  \[{{certificate}}]

CertificateVerify:
: a signature over the entire handshake using the private key
  corresponding to the public key in the Certificate message. This
  message is omitted if the endpoint is not authenticating via a
  certificate. \[{{certificate-verify}}]

Finished:
: a MAC (Message Authentication Code) over the entire handshake.
  This message provides key confirmation, binds the endpoint's identity
  to the exchanged keys, and in PSK mode
  also authenticates the handshake. \[{{finished}}]
{:br }

Upon receiving the server's messages, the client responds with its Authentication
messages, namely Certificate and CertificateVerify (if requested), and Finished.

At this point, the handshake is complete, and the client and server may exchange
application-layer data. Application data MUST NOT be sent prior to sending the
Finished message. Note that while the server may send application data
prior to receiving the client's Authentication messages, any data sent at
that point is, of course, being sent to an unauthenticated peer.

## Incorrect DHE Share

If the client has not provided a sufficient "key_share" extension (e.g., it
includes only DHE or ECDHE groups unacceptable to or unsupported by the
server), the server corrects the mismatch with a HelloRetryRequest and
the client needs to restart the handshake with an appropriate
"key_share" extension, as shown in Figure 2.
If no common cryptographic parameters can be negotiated,
the server MUST abort the handshake with an appropriate alert.

~~~
         Client                                               Server

         ClientHello
         + key_share             -------->
                                 <--------         HelloRetryRequest
                                                         + key_share

         ClientHello
         + key_share             -------->
                                                         ServerHello
                                                         + key_share
                                               {EncryptedExtensions}
                                               {CertificateRequest*}
                                                      {Certificate*}
                                                {CertificateVerify*}
                                                          {Finished}
                                 <--------       [Application Data*]
         {Certificate*}
         {CertificateVerify*}
         {Finished}              -------->
         [Application Data]      <------->        [Application Data]
~~~
{: #tls-restart title="Message flow for a full handshake with mismatched parameters"}

Note: The handshake transcript includes the initial
ClientHello/HelloRetryRequest exchange; it is not reset with the new
ClientHello.


TLS also allows several optimized variants of the basic handshake, as
described in the following sections.

## Resumption and Pre-Shared Key (PSK) {#resumption-and-psk}

Although TLS PSKs can be established out of band,
PSKs can also be established in a previous connection and
then reused ("session resumption"). Once a handshake has completed, the server can
send the client a PSK identity that corresponds to a key derived from
the initial handshake (see {{NewSessionTicket}}). The client
can then use that PSK identity in future handshakes to negotiate use
of the PSK. If the server accepts it, then the security context of the
new connection is tied to the original connection and the key derived
from the initial handshake is used to bootstrap the cryptographic state
instead of a full handshake. In TLS 1.2 and
below, this functionality was provided by "session IDs" and
"session tickets" {{RFC5077}}. Both mechanisms are obsoleted in TLS
1.3.

PSKs can be used with (EC)DHE key exchange in order to provide forward
secrecy in combination with shared keys, or can be used alone, at the
cost of losing forward secrecy.

{{tls-resumption-psk}} shows a pair of handshakes in which the first establishes
a PSK and the second uses it:

~~~
       Client                                               Server

Initial Handshake:
       ClientHello
       + key_share               -------->
                                                       ServerHello
                                                       + key_share
                                             {EncryptedExtensions}
                                             {CertificateRequest*}
                                                    {Certificate*}
                                              {CertificateVerify*}
                                                        {Finished}
                                 <--------     [Application Data*]
       {Certificate*}
       {CertificateVerify*}
       {Finished}                -------->
                                 <--------      [NewSessionTicket]
       [Application Data]        <------->      [Application Data]


Subsequent Handshake:
       ClientHello
       + key_share*
       + psk_key_exchange_modes
       + pre_shared_key          -------->
                                                       ServerHello
                                                  + pre_shared_key
                                                      + key_share*
                                             {EncryptedExtensions}
                                                        {Finished}
                                 <--------     [Application Data*]
       {Finished}                -------->
       [Application Data]        <------->      [Application Data]
~~~
{: #tls-resumption-psk title="Message flow for resumption and PSK"}

As the server is authenticating via a PSK, it does not send a
Certificate or a CertificateVerify message. When a client offers resumption
via PSK, it SHOULD also supply a "key_share" extension to the server to
allow the server to decline resumption and fall back
to a full handshake, if needed. The server responds with a "pre_shared_key"
extension to negotiate use of PSK key establishment and can (as shown here)
respond with a "key_share" extension to do (EC)DHE key establishment, thus
providing forward secrecy.

When PSKs are provisioned out of band, the PSK identity and the KDF
to be used with the PSK MUST also be provisioned.

## Zero-RTT Data

When clients and servers share a PSK (either obtained externally or
via a previous handshake), TLS 1.3 allows clients to send data on the
first flight ("early data"). The client uses the PSK to authenticate
the server and to encrypt the early data.

When clients use a PSK obtained externally then the following
additional information MUST be provisioned to both parties:

  * The cipher suite for use with this PSK
  * The Application-Layer Protocol Negotiation (ALPN) protocol, if any is to be used
  * The Server Name Indication (SNI), if any is to be used

As shown in {{tls-0-rtt}}, the 0-RTT data is just added to the 1-RTT
handshake in the first flight. The rest of the handshake uses the same messages
as with a 1-RTT handshake with PSK resumption.

~~~
         Client                                               Server

         ClientHello
         + early_data
         + key_share*
         + psk_key_exchange_modes
         + pre_shared_key
         (Application Data*)     -------->
                                                         ServerHello
                                                    + pre_shared_key
                                                        + key_share*
                                               {EncryptedExtensions}
                                                          {Finished}
                                 <--------       [Application Data*]
         (EndOfEarlyData)
         {Finished}              -------->

         [Application Data]      <------->        [Application Data]

               *  Indicates optional or situation-dependent
                  messages/extensions that are not always sent.

               () Indicates messages protected using keys
                  derived from client_early_traffic_secret.

               {} Indicates messages protected using keys
                  derived from a [sender]_handshake_traffic_secret.

               [] Indicates messages protected using keys
                  derived from traffic_secret_N
~~~
{: #tls-0-rtt title="Message flow for a zero round trip handshake"}


IMPORTANT NOTE: The security properties for 0-RTT data are weaker than
those for other kinds of TLS data.  Specifically:

1. This data is not forward secret, as it is encrypted solely under
keys derived using the offered PSK.

2. There are no guarantees of non-replay between connections.
Unless the server takes special measures outside those provided by TLS,
the server has no guarantee that the same
0-RTT data was not transmitted on multiple 0-RTT connections
(see {{replay-time}} for more details).
This is especially relevant if the data is authenticated either
with TLS client authentication or inside the application layer
protocol. However, 0-RTT data cannot be duplicated within a connection (i.e., the server
will not process the same data twice for the same connection) and
an attacker will not be able to make 0-RTT data appear to be
1-RTT data (because it is protected with different keys.)

Protocols MUST NOT use 0-RTT data without a profile that defines its
use. That profile needs to identify which messages or interactions are
safe to use with 0-RTT. In addition, to avoid accidental misuse,
implementations SHOULD NOT enable 0-RTT unless specifically
requested. Implementations SHOULD provide special functions for 0-RTT data to ensure
that an application is always aware that it is sending or receiving
data that might be replayed.

The same warnings apply to any use of the early_exporter_secret.

The remainder of this document provides a detailed description of TLS.


#  Presentation Language

This document deals with the formatting of data in an external representation.
The following very basic and somewhat casually defined presentation syntax will
be used.

##  Basic Block Size

The representation of all data items is explicitly specified. The basic data
block size is one byte (i.e., 8 bits). Multiple byte data items are
concatenations of bytes, from left to right, from top to bottom. From the byte
stream, a multi-byte item (a numeric in the example) is formed (using C
notation) by:

       value = (byte[0] << 8*(n-1)) | (byte[1] << 8*(n-2)) |
               ... | byte[n-1];

This byte ordering for multi-byte values is the commonplace network byte order
or big-endian format.


##  Miscellaneous

Comments begin with "/\*" and end with "\*/".

Optional components are denoted by enclosing them in "\[\[ \]\]" double
brackets.

Single-byte entities containing uninterpreted data are of type
opaque.


##  Vectors

A vector (single-dimensioned array) is a stream of homogeneous data elements.
The size of the vector may be specified at documentation time or left
unspecified until runtime. In either case, the length declares the number of
bytes, not the number of elements, in the vector. The syntax for specifying a
new type, T', that is a fixed-length vector of type T is

       T T'[n];

Here, T' occupies n bytes in the data stream, where n is a multiple of the size
of T.  The length of the vector is not included in the encoded stream.

In the following example, Datum is defined to be three consecutive bytes that
the protocol does not interpret, while Data is three consecutive Datum,
consuming a total of nine bytes.

       opaque Datum[3];      /* three uninterpreted bytes */
       Datum Data[9];        /* 3 consecutive 3-byte vectors */

Variable-length vectors are defined by specifying a subrange of legal lengths,
inclusively, using the notation \<floor..ceiling\>. When these are encoded, the
actual length precedes the vector's contents in the byte stream. The length
will be in the form of a number consuming as many bytes as required to hold the
vector's specified maximum (ceiling) length. A variable-length vector with an
actual length field of zero is referred to as an empty vector.

       T T'<floor..ceiling>;

In the following example, mandatory is a vector that must contain between 300
and 400 bytes of type opaque. It can never be empty. The actual length field
consumes two bytes, a uint16, which is sufficient to represent the value 400
(see {{numbers}}). On the other hand, longer can represent up to 800 bytes of
data, or 400 uint16 elements, and it may be empty. Its encoding will include a
two-byte actual length field prepended to the vector. The length of an encoded
vector must be an exact multiple of the length of a single element (e.g.,
a 17-byte vector of uint16 would be illegal).

       opaque mandatory<300..400>;
             /* length field is 2 bytes, cannot be empty */
       uint16 longer<0..800>;
             /* zero to 400 16-bit unsigned integers */


##  Numbers

The basic numeric data type is an unsigned byte (uint8). All larger numeric
data types are formed from fixed-length series of bytes concatenated as
described in {{basic-block-size}} and are also unsigned. The following numeric
types are predefined.

       uint8 uint16[2];
       uint8 uint24[3];
       uint8 uint32[4];
       uint8 uint64[8];

All values, here and elsewhere in the specification, are stored in network byte
(big-endian) order; the uint32 represented by the hex bytes 01 02 03 04 is
equivalent to the decimal value 16909060.


##  Enumerateds

An additional sparse data type is available called enum. Each definition is a
different type. Only enumerateds of the same type may be assigned or compared.
Every element of an enumerated must be assigned a value, as demonstrated in the
following example. Since the elements of the enumerated are not ordered, they
can be assigned any unique value, in any order.

       enum { e1(v1), e2(v2), ... , en(vn) [[, (n)]] } Te;

Future extensions or additions to the protocol may define new values.
Implementations need to be able to parse and ignore unknown values unless the
definition of the field states otherwise.

An enumerated occupies as much space in the byte stream as would its maximal
defined ordinal value. The following definition would cause one byte to be used
to carry fields of type Color.

       enum { red(3), blue(5), white(7) } Color;

One may optionally specify a value without its associated tag to force the
width definition without defining a superfluous element.

In the following example, Taste will consume two bytes in the data stream but
can only assume the values 1, 2, or 4 in the current version of the protocol.

       enum { sweet(1), sour(2), bitter(4), (32000) } Taste;

The names of the elements of an enumeration are scoped within the defined type.
In the first example, a fully qualified reference to the second element of the
enumeration would be Color.blue. Such qualification is not required if the
target of the assignment is well specified.

       Color color = Color.blue;     /* overspecified, legal */
       Color color = blue;           /* correct, type implicit */

The names assigned to enumerateds do not need to be unique.  The numerical value
can describe a range over which the same name applies.  The value includes the
minimum and maximum inclusive values in that range, separated by two period
characters. This is principally useful for reserving regions of the space.

       enum { sad(0), meh(1..254), happy(255) } Mood;



##  Constructed Types

Structure types may be constructed from primitive types for convenience. Each
specification declares a new, unique type. The syntax for definition is much
like that of C.

       struct {
           T1 f1;
           T2 f2;
           ...
           Tn fn;
       } [[T]];

The fields within a structure may be qualified using the type's name, with a
syntax much like that available for enumerateds. For example, T.f2 refers to
the second field of the previous declaration. Structure definitions may be
embedded. Anonymous structs may also be defined inside other structures.


## Constants

Fields and variables may be assigned a fixed value using "=", as in:

       struct {
           T1 f1 = 8;  /* T.f1 must always be 8 */
           T2 f2;
       } T;

##  Variants

Defined structures may have variants based on some knowledge that is
available within the environment. The selector must be an enumerated
type that defines the possible variants the structure defines.
The body of the variant structure may be given a label
for reference. The mechanism by which the variant is selected at
runtime is not prescribed by the presentation language.

       struct {
           T1 f1;
           T2 f2;
           ....
           Tn fn;
           select (E) {
               case e1: Te1;
               case e2: Te2;
               ....
               case en: Ten;
           } [[fv]];
       } [[Tv]];

For example:

       enum { apple(0), orange(1) } VariantTag;

       struct {
           uint16 number;
           opaque string<0..10>; /* variable length */
       } V1;

       struct {
           uint32 number;
           opaque string[10];    /* fixed length */
       } V2;

       struct {
           VariantTag type;
           select (VariantRecord.type) {
               case apple:  V1;
               case orange: V2;
           };
       } VariantRecord;


## Decoding Errors

TLS defines two generic alerts (see {{alert-protocol}}) to use upon failure to parse
a message. Peers which receive a message which cannot be parsed according to the syntax
(e.g., have a length extending beyond the message boundary or contain an out-of-range
length) MUST terminate the connection with a "decode_error" alert. Peers which receive
a message which is syntactically correct but semantically invalid (e.g., a DHE share of p - 1,
or an invalid enum) MUST terminate the connection with an "illegal_parameter" alert.


# Handshake Protocol

The handshake protocol is used to negotiate the secure attributes
of a connection. Handshake messages are supplied to the TLS record layer, where
they are encapsulated within one or more TLSPlaintext or TLSCiphertext structures, which are
processed and transmitted as specified by the current active connection state.

%%% Handshake Protocol

       enum {
           hello_request_RESERVED(0),
           client_hello(1),
           server_hello(2),
           hello_verify_request_RESERVED(3),
           new_session_ticket(4),
           end_of_early_data(5),
           hello_retry_request(6),
           encrypted_extensions(8),
           certificate(11),
           server_key_exchange_RESERVED(12),
           certificate_request(13),
           server_hello_done_RESERVED(14),
           certificate_verify(15),
           client_key_exchange_RESERVED(16),
           finished(20),
           key_update(24),
           message_hash(254),
           (255)
       } HandshakeType;

       struct {
           HandshakeType msg_type;    /* handshake type */
           uint24 length;             /* bytes in message */
           select (Handshake.msg_type) {
               case client_hello:          ClientHello;
               case server_hello:          ServerHello;
               case end_of_early_data:     EndOfEarlyData;
               case hello_retry_request:   HelloRetryRequest;
               case encrypted_extensions:  EncryptedExtensions;
               case certificate_request:   CertificateRequest;
               case certificate:           Certificate;
               case certificate_verify:    CertificateVerify;
               case finished:              Finished;
               case new_session_ticket:    NewSessionTicket;
               case key_update:            KeyUpdate;
           } body;
       } Handshake;

Protocol messages MUST be sent in the order defined below (and
shown in the diagrams in {{protocol-overview}}).
A peer which receives a handshake message in an unexpected order
MUST abort the handshake with an "unexpected_message" alert.
Unneeded handshake messages are omitted, however.

New handshake message types are assigned by IANA as described in
{{iana-considerations}}.

## Key Exchange Messages

The key exchange messages are used to exchange security capabilities
between the client and server and to establish the traffic keys used to protect
the handshake and data.


### Cryptographic Negotiation

TLS cryptographic negotiation proceeds by the client offering the
following four sets of options in its ClientHello:

- A list of cipher suites which indicates the AEAD algorithm/HKDF hash
  pairs which the client supports.
- A "supported_groups" ({{negotiated-groups}}) extension which indicates the (EC)DHE groups
  which the client supports and a "key_share" ({{key-share}}) extension which contains
  (EC)DHE shares for some or all of these groups.
- A "signature_algorithms" ({{signature-algorithms}}) extension which indicates the signature
  algorithms which the client can accept.
- A "pre_shared_key" ({{pre-shared-key-extension}}) extension which
  contains a list of symmetric key identities known to the client and a
  "psk_key_exchange_modes" ({{pre-shared-key-exchange-modes}})
  extension which indicates the key exchange modes that may be used
  with PSKs.

If the server does not select a PSK, then the first three of these
options are entirely orthogonal: the server independently selects a
cipher suite, an (EC)DHE group and key share for key establishment,
and a signature algorithm/certificate pair to authenticate itself to
the client. If there is no overlap in "supported_groups" then the server MUST
abort the handshake.

If the server selects a PSK, then it MUST also select a key
establishment mode from the set indicated by client's
"psk_key_exchange_modes" extension (PSK alone or with (EC)DHE). Note
that if the PSK can be used without (EC)DHE then non-overlap in the
"supported_groups" parameters need not be fatal, as it is in the
non-PSK case discussed in the previous paragraph.

If the server selects an (EC)DHE group and the client did not offer a
compatible "key_share" extension in the initial ClientHello, the server MUST
respond with a HelloRetryRequest ({{hello-retry-request}}) message.

If the server successfully selects parameters and does not require a
HelloRetryRequest, it indicates the selected parameters in the ServerHello as
follows:

- If PSK is being used, then the server will send a
"pre_shared_key" extension indicating the selected key.
- If PSK is not being used, then (EC)DHE and certificate-based
authentication are always used.
- When (EC)DHE is in use, the server will also provide a
"key_share" extension.
- When authenticating via a certificate, the server will send the Certificate ({{certificate}}) and
CertificateVerify ({{certificate-verify}}) messages. In TLS 1.3
as defined by this document, either a PSK or a certificate
is always used, but not both. Future documents may define how to use them
together.

If the server is unable to negotiate a supported set of parameters
(i.e., there is no overlap between the client and server parameters),
it MUST abort the handshake with either
a "handshake_failure" or "insufficient_security" fatal alert
(see {{alert-protocol}}).


###  Client Hello

When a client first connects to a server, it is REQUIRED to send the
ClientHello as its first message. The client will also send a
ClientHello when the server has responded to its ClientHello with a
HelloRetryRequest. In that case, the client MUST send the same
ClientHello (without modification) except:

- If a "key_share" extension was supplied in the HelloRetryRequest,
  replacing the list of shares with a list containing a single
  KeyShareEntry from the indicated group.

- Removing the "early_data" extension ({{early-data-indication}}) if one was
  present. Early data is not permitted after HelloRetryRequest.

- Including a "cookie" extension if one was provided in the
  HelloRetryRequest.

- Updating the "pre_shared_key" extension if present by
  recomputing the "obfuscated_ticket_age" and binder values
  and (optionally) removing
  any PSKs which are incompatible with the server's indicated
  cipher suite.

Because TLS 1.3 forbids renegotiation, if a server receives a
ClientHello at any other time, it MUST terminate the connection.

If a server established a TLS connection with a previous version of TLS
and receives a TLS 1.3 ClientHello in a renegotiation, it MUST retain the
previous protocol version. In particular, it MUST NOT negotiate TLS 1.3.

Structure of this message:

%%% Key Exchange Messages

       uint16 ProtocolVersion;
       opaque Random[32];

       uint8 CipherSuite[2];    /* Cryptographic suite selector */

       struct {
           ProtocolVersion legacy_version = 0x0303;    /* TLS v1.2 */
           Random random;
           opaque legacy_session_id<0..32>;
           CipherSuite cipher_suites<2..2^16-2>;
           opaque legacy_compression_methods<1..2^8-1>;
           Extension extensions<8..2^16-1>;
       } ClientHello;

All versions of TLS allow extensions to optionally follow the
compression_methods field as an extensions field.  TLS 1.3
ClientHellos will contain at least two extensions,
"supported_versions" and either "key_share" or "pre_shared_key".  The
presence of extensions can be detected by determining whether there
are bytes following the compression_methods at the end of the
ClientHello. Note that this method of detecting optional data differs
from the normal TLS method of having a variable-length field, but it
is used for compatibility with TLS before extensions were defined.
TLS 1.3 servers will need to perform this check first and only
attempt to negotiate TLS 1.3 if a "supported_version" extension
is present.

legacy_version
: In previous versions of TLS, this field was used for version negotiation
  and represented the highest version number supported by the client.
  Experience has shown that many servers do not properly implement
  version negotiation, leading to "version intolerance" in which
  the server rejects an otherwise acceptable ClientHello with a version
  number higher than it supports.
  In TLS 1.3, the client indicates its version preferences in the
  "supported_versions" extension ({{supported-versions}}) and the legacy_version field MUST
  be set to 0x0303, which was the version number for TLS 1.2.
  (See {{backward-compatibility}} for details about backward compatibility.)

random
: 32 bytes generated by a secure random number generator.
  See {{implementation-notes}} for additional information.

legacy_session_id
: Versions of TLS before TLS 1.3 supported a "session resumption"
  feature which has been merged with Pre-Shared Keys in this version
  (see {{resumption-and-psk}}).
  This field MUST be ignored by a server negotiating TLS 1.3 and
  MUST be set as a zero length vector (i.e., a single zero byte
  length field) by clients which do not have a cached session ID
  set by a pre-TLS 1.3 server.

cipher_suites
: This is a list of the symmetric cipher options supported by the
  client, specifically the record protection algorithm (including
  secret key length) and a hash to be used with HKDF, in descending
  order of client preference. If the list contains cipher suites
  the server does not recognize, support, or wish to use, the server
  MUST ignore those cipher suites, and process the remaining ones as
  usual. Values are defined in {{cipher-suites}}. If the client is
  attempting a PSK key establishment, it SHOULD advertise at least one
  cipher suite containing a Hash associated with the PSK.

legacy_compression_methods
: Versions of TLS before 1.3 supported compression with the list of
  supported compression methods being sent in this field. For every TLS 1.3
  ClientHello, this vector MUST contain exactly one byte set to
  zero, which corresponds to the "null" compression method in
  prior versions of TLS. If a TLS 1.3 ClientHello is
  received with any other value in this field, the server MUST
  abort the handshake with an "illegal_parameter" alert. Note that TLS 1.3
  servers might receive TLS 1.2 or prior ClientHellos which contain
  other compression methods and MUST follow the procedures for
  the appropriate prior version of TLS.

extensions
: Clients request extended functionality from servers by sending
  data in the extensions field.  The actual "Extension" format is
  defined in {{extensions}}.  In TLS 1.3, use
  of certain extensions is mandatory, as functionality is moved into
  extensions to preserve ClientHello compatibility with previous versions of TLS.
  Servers MUST ignore unrecognized extensions.
{:br }

In the event that a client requests additional functionality using
extensions, and this functionality is not supplied by the server, the
client MAY abort the handshake. Note that TLS 1.3 ClientHello messages
always contain extensions (minimally they must contain
"supported_versions" or they will be interpreted as TLS 1.2 ClientHello
messages). TLS 1.3 servers might receive ClientHello messages from versions
of TLS prior to 1.3 that do not contain extensions.
If negotiating a version of TLS prior to 1.3, a server MUST check that
the message either contains no data after legacy_compression_methods
or that it contains a valid extensions block with no data following.
If not, then it MUST abort the handshake with a "decode_error" alert.

After sending the ClientHello message, the client waits for a ServerHello
or HelloRetryRequest message.

### Server Hello {#server-hello}

The server will send this message in response to a ClientHello message if it is
able to find an acceptable set of parameters and the ClientHello contains
sufficient information to proceed with the handshake.

Structure of this message:

%%% Key Exchange Messages

       struct {
           ProtocolVersion version;
           Random random;
           CipherSuite cipher_suite;
           Extension extensions<6..2^16-1>;
       } ServerHello;

version
: This field contains the version of TLS negotiated for this connection.  Servers
  MUST select a version from the list in ClientHello.supported_versions extension.
  A client which receives a version that was not offered MUST abort the handshake.
  For this version of the specification, the version is 0x0304.  (See
  {{backward-compatibility}} for details about backward compatibility.)

random
: 32 bytes generated by a secure random number generator.
  See {{implementation-notes}} for additional information.
  The last eight bytes MUST be overwritten as described
  below if negotiating TLS 1.2 or TLS 1.1.
  This structure is generated by the server and MUST be
  generated independently of the ClientHello.random.

cipher_suite
: The single cipher suite selected by the server from the list in
  ClientHello.cipher_suites. A client which receives a cipher suite
  that was not offered MUST abort the handshake.

extensions
: A list of extensions.  The ServerHello MUST only include extensions
  which are required to establish the cryptographic context. Currently
  the only such extensions are "key_share" and "pre_shared_key".
  All current TLS 1.3 ServerHello messages will contain one of these
  two extensions, or both when using a PSK with (EC)DHE key establishment.
{:br }

TLS 1.3 has a downgrade protection mechanism embedded in the server's
random value. TLS 1.3 servers which negotiate TLS 1.2 or below in
response to a ClientHello MUST set the last eight bytes of their
Random value specially.

If negotiating TLS 1.2, TLS 1.3 servers MUST set the last eight bytes of their
Random value to the bytes:

      44 4F 57 4E 47 52 44 01

If negotiating TLS 1.1, TLS 1.3 servers MUST and TLS 1.2 servers SHOULD
set the last eight bytes of their Random value to the bytes:

      44 4F 57 4E 47 52 44 00

TLS 1.3 clients receiving a TLS 1.2 or below ServerHello MUST check
that the last eight bytes are not equal to either of these values.
TLS 1.2 clients SHOULD also check that the last eight bytes are not
equal to the second value if the ServerHello indicates TLS 1.1 or
below.  If a match is found, the client MUST abort the handshake
with an "illegal_parameter" alert.  This mechanism provides limited
protection against downgrade attacks over and above that provided
by the Finished exchange: because the ServerKeyExchange, a message
present in TLS 1.2 and below, includes a signature over both random
values, it is not possible for an active attacker to modify the
random values without detection as long as ephemeral ciphers are used.
It does not provide downgrade protection when static RSA is used.

Note: This is a change from {{RFC5246}}, so in practice many TLS 1.2 clients
and servers will not behave as specified above.

A client that receives a TLS 1.3 ServerHello during renegotiation
MUST abort the handshake with a "protocol_version" alert.

RFC EDITOR: PLEASE REMOVE THE FOLLOWING PARAGRAPH
Implementations of draft versions (see {{draft-version-indicator}}) of this
specification SHOULD NOT implement this mechanism on either client and server.
A pre-RFC client connecting to RFC servers, or vice versa, will appear to
downgrade to TLS 1.2. With the mechanism enabled, this will cause an
interoperability failure.


###  Hello Retry Request

The server will send this message in response to a ClientHello message if it is
able to find an acceptable set of parameters but the ClientHello does not
contain sufficient information to proceed with the handshake.

Structure of this message:

%%% Key Exchange Messages

       struct {
           ProtocolVersion server_version;
           CipherSuite cipher_suite;
           Extension extensions<2..2^16-1>;
       } HelloRetryRequest;

{:br }

The version, cipher_suite, and extensions fields have the
same meanings as their corresponding values in the ServerHello.
The server SHOULD send only the extensions necessary for the client to
generate a correct ClientHello pair. As with ServerHello, a
HelloRetryRequest MUST NOT contain any extensions that were not first
offered by the client in its ClientHello, with the exception of optionally the
"cookie" (see {{cookie}}) extension.

Upon receipt of a HelloRetryRequest, the client MUST verify that the
extensions block is not empty and otherwise MUST abort the handshake
with a "decode_error" alert. Clients MUST abort the handshake with
an "illegal_parameter" alert if the HelloRetryRequest would not result in
any change in the ClientHello. If a client receives a second
HelloRetryRequest in the same connection (i.e., where
the ClientHello was itself in response to a HelloRetryRequest), it
MUST abort the handshake with an "unexpected_message" alert.

Otherwise, the client MUST process all extensions in the HelloRetryRequest and
send a second updated ClientHello. The HelloRetryRequest extensions defined in
this specification are:

- cookie (see {{cookie}})

- key_share (see {{key-share}})

In addition, in its updated ClientHello, the client SHOULD NOT offer
any pre-shared keys associated with a hash other than that of the
selected cipher suite. This allows the client to avoid having to
compute partial hash transcripts for multiple hashes in the second
ClientHello.  A client which receives a cipher suite that was not
offered MUST abort the handshake.  Servers MUST ensure that they
negotiate the same cipher suite when receiving a conformant updated
ClientHello (if the server selects the cipher suite as the first step
in the negotiation, then this will happen automatically). Upon
receiving the ServerHello, clients MUST check that the cipher suite
supplied in the ServerHello is the same as that in the
HelloRetryRequest and otherwise abort the handshake with an
"illegal_parameter" alert.

##  Extensions

A number of TLS messages contain tag-length-value encoded extensions structures.

%%% Key Exchange Messages

       struct {
           ExtensionType extension_type;
           opaque extension_data<0..2^16-1>;
       } Extension;

       enum {
           supported_groups(10),
           signature_algorithms(13),
           key_share(40),
           pre_shared_key(41),
           early_data(42),
           supported_versions(43),
           cookie(44),
           psk_key_exchange_modes(45),
           certificate_authorities(47),
           oid_filters(48),
           (65535)
       } ExtensionType;

Here:

-  "extension_type" identifies the particular extension type.

-  "extension_data" contains information specific to the particular
  extension type.

The list of extension types is maintained by IANA as described in
{{iana-considerations}}.

Extensions are generally structured in a request/response fashion, though
some extensions are just indications with no corresponding response. The client
sends its extension requests in the ClientHello message and the server sends
its extension responses in the ServerHello, EncryptedExtensions
and HelloRetryRequest messages. The server sends extension requests
in the CertificateRequest message which a client MAY respond to with
a Certificate message. The server MAY also send unsolicited
extensions in the NewSessionTicket, though the client does not respond
directly to these.

Implementations MUST NOT send extension responses
if the remote endpoint did not send the corresponding extension requests,
with the exception of the "cookie" extension in HelloRetryRequest.
Upon receiving such an extension, an endpoint MUST abort the handshake with an
"unsupported_extension" alert.

The table below indicates the messages where a given extension may
appear, using the following notation: CH (ClientHello), SH
(ServerHello), EE (EncryptedExtensions), CT (Certificate), CR
(CertificateRequest), NST (NewSessionTicket) and HRR
(HelloRetryRequest). If an implementation receives an extension which
it recognizes and which is not specified for the message in which it
appears it MUST abort the handshake with an "illegal_parameter" alert.

| Extension                                |   TLS 1.3   |
|:-----------------------------------------|------------:|
| server_name [RFC6066]                    |      CH, EE |
| max_fragment_length [RFC6066]            |      CH, EE |
| client_certificate_url [RFC6066]         |      CH, EE |
| status_request [RFC6066]                 |  CH, CR, CT |
| user_mapping [RFC4681]                   |      CH, EE |
| cert_type [RFC6091]                      |      CH, EE |
| supported_groups [RFC7919]               |      CH, EE |
| signature_algorithms [RFC5246]           |      CH, CR |
| use_srtp [RFC5764]                       |      CH, EE |
| heartbeat [RFC6520]                      |      CH, EE |
| application_layer_protocol_negotiation [RFC7301]|      CH, EE |
| signed_certificate_timestamp [RFC6962]   |  CH, CR, CT |
| client_certificate_type [RFC7250]        |      CH, EE |
| server_certificate_type [RFC7250]        |      CH, CT |
| padding [RFC7685]                        |          CH |
| key_share \[\[this document]]            | CH, SH, HRR |
| pre_shared_key \[\[this document]]       |      CH, SH |
| psk_key_exchange_modes \[\[this document]]|          CH |
| early_data \[\[this document]]           | CH, EE, NST |
| cookie \[\[this document]]               |     CH, HRR |
| supported_versions \[\[this document]]   |          CH |
| certificate_authorities \[\[this document]]|      CH, CR |
| oid_filters \[\[this document]]          |          CR |

When multiple extensions of different types are present, the
extensions MAY appear in any order, with the exception of
"pre_shared_key" {{pre-shared-key-extension}} which MUST be
the last extension in the ClientHello.
There MUST NOT be more than one extension of the same type.

In TLS 1.3, unlike TLS 1.2, extensions are renegotiated with each
handshake even when in resumption-PSK mode. However, 0-RTT parameters are
those negotiated in the previous handshake; mismatches may require
rejecting 0-RTT (see {{early-data-indication}}).

There are subtle (and not so subtle) interactions that may occur in this
protocol between new features and existing features which may result in a
significant reduction in overall security. The following considerations should
be taken into account when designing new extensions:

- Some cases where a server does not agree to an extension are error
  conditions, and some are simply refusals to support particular features. In
  general, error alerts should be used for the former, and a field in the
  server extension response for the latter.

- Extensions should, as far as possible, be designed to prevent any attack that
  forces use (or non-use) of a particular feature by manipulation of handshake
  messages. This principle should be followed regardless of whether the feature
  is believed to cause a security problem.
  Often the fact that the extension fields are included in the inputs to the
  Finished message hashes will be sufficient, but extreme care is needed when
  the extension changes the meaning of messages sent in the handshake phase.
  Designers and implementors should be aware of the fact that until the
  handshake has been authenticated, active attackers can modify messages and
  insert, remove, or replace extensions.

###  Supported Versions

%%% Version Extension

       struct {
           ProtocolVersion versions<2..254>;
       } SupportedVersions;

The "supported_versions" extension is used by the client to indicate
which versions of TLS it supports. The extension contains a list of
supported versions in preference order, with the most preferred
version first. Implementations of this specification MUST send this
extension containing all versions of TLS which they are
prepared to negotiate (for this specification, that means minimally
0x0304, but if previous versions of TLS are supported, they MUST
be present as well).

If this extension is not present, servers which are compliant with
this specification MUST negotiate TLS 1.2 or prior as specified in
{{RFC5246}}, even if ClientHello.legacy_version is 0x0304 or later.

If this extension is present, servers MUST ignore the
ClientHello.legacy_version value and MUST use only the
"supported_versions" extension to determine client
preferences. Servers MUST only select a version of TLS present in that
extension and MUST ignore any unknown versions. Note that this
mechanism makes it possible to negotiate a version prior to TLS 1.2 if
one side supports a sparse range. Implementations of TLS 1.3 which choose
to support prior versions of TLS SHOULD support TLS 1.2.

The server MUST NOT send the "supported_versions" extension. The
server's selected version is contained in the ServerHello.version field as
in previous versions of TLS.

#### Draft Version Indicator

RFC EDITOR: PLEASE REMOVE THIS SECTION

While the eventual version indicator for the RFC version of TLS 1.3 will
be 0x0304, implementations of draft versions of this specification SHOULD
instead advertise 0x7f00 | draft_version
in ServerHello.version, and HelloRetryRequest.server_version.
For instance, draft-17 would be encoded as the 0x7f11.
This allows pre-RFC implementations to safely negotiate with each other,
even if they would otherwise be incompatible.


###  Cookie

%%% Cookie Extension

       struct {
           opaque cookie<1..2^16-1>;
       } Cookie;

Cookies serve two primary purposes:

- Allowing the server to force the client to demonstrate reachability
  at their apparent network address (thus providing a measure of DoS
  protection). This is primarily useful for non-connection-oriented
  transports (see {{?RFC6347}} for an example of this).

- Allowing the server to offload state to the client, thus allowing it to send
  a HelloRetryRequest without storing any state. The server does this by
  storing the hash of the ClientHello in the HelloRetryRequest cookie
  (protected with some suitable integrity algorithm).

When sending a HelloRetryRequest, the server MAY provide a "cookie" extension to the
client (this is an exception to the usual rule that the only extensions that
may be sent are those that appear in the ClientHello). When sending the
new ClientHello, the client MUST echo the value of the extension.
Clients MUST NOT use cookies in subsequent connections.


###  Signature Algorithms

The client uses the "signature_algorithms" extension to indicate to the server
which signature algorithms may be used in digital signatures. Clients which
desire the server to authenticate itself via a certificate MUST send this extension.
If a server
is authenticating via a certificate and the client has not sent a
"signature_algorithms" extension, then the server MUST
abort the handshake with a "missing_extension" alert
(see {{mti-extensions}}).

The "extension_data" field of this extension in a ClientHello contains a
SignatureSchemeList value:

%%% Signature Algorithm Extension

       enum {
           /* RSASSA-PKCS1-v1_5 algorithms */
           rsa_pkcs1_sha1(0x0201),
           rsa_pkcs1_sha256(0x0401),
           rsa_pkcs1_sha384(0x0501),
           rsa_pkcs1_sha512(0x0601),

           /* ECDSA algorithms */
           ecdsa_secp256r1_sha256(0x0403),
           ecdsa_secp384r1_sha384(0x0503),
           ecdsa_secp521r1_sha512(0x0603),

           /* RSASSA-PSS algorithms */
           rsa_pss_sha256(0x0804),
           rsa_pss_sha384(0x0805),
           rsa_pss_sha512(0x0806),

           /* EdDSA algorithms */
           ed25519(0x0807),
           ed448(0x0808),

           /* Reserved Code Points */
           dsa_sha1_RESERVED(0x0202),
           dsa_sha256_RESERVED(0x0402),
           dsa_sha384_RESERVED(0x0502),
           dsa_sha512_RESERVED(0x0602),
           ecdsa_sha1_RESERVED(0x0203),
           obsolete_RESERVED(0x0000..0x0200),
           obsolete_RESERVED(0x0204..0x0400),
           obsolete_RESERVED(0x0404..0x0500),
           obsolete_RESERVED(0x0504..0x0600),
           obsolete_RESERVED(0x0604..0x06FF),
           private_use(0xFE00..0xFFFF),
           (0xFFFF)
       } SignatureScheme;

       struct {
           SignatureScheme supported_signature_algorithms<2..2^16-2>;
       } SignatureSchemeList;

Note: This enum is named "SignatureScheme" because there is already
a "SignatureAlgorithm" type in TLS 1.2, which this replaces.
We use the term "signature algorithm" throughout the text.

Each SignatureScheme value lists a single signature algorithm that the
client is willing to verify. The values are indicated in descending order
of preference. Note that a signature algorithm takes as input an
arbitrary-length message, rather than a digest. Algorithms which
traditionally act on a digest should be defined in TLS to first
hash the input with a specified hash algorithm and then proceed as usual.
The code point groups listed above have the following meanings:

RSASSA-PKCS1-v1_5 algorithms
: Indicates a signature algorithm using RSASSA-PKCS1-v1_5 {{RFC3447}}
  with the corresponding hash algorithm as defined in {{SHS}}. These values
  refer solely to signatures which appear in certificates (see
  {{server-certificate-selection}}) and are not defined for use in signed
  TLS handshake messages.

ECDSA algorithms
: Indicates a signature algorithm using ECDSA {{ECDSA}}, the corresponding
  curve as defined in ANSI X9.62 {{X962}} and FIPS 186-4 {{DSS}}, and the
  corresponding hash algorithm as defined in {{SHS}}. The signature is
  represented as a DER-encoded {{X690}} ECDSA-Sig-Value structure.

RSASSA-PSS algorithms
: Indicates a signature algorithm using RSASSA-PSS {{RFC3447}} with mask
  generation function 1. The
  digest used in the mask generation function and the digest being signed are
  both the corresponding hash algorithm as defined in {{SHS}}. When used in
  signed TLS handshake messages, the length of the salt MUST be equal to the
  length of the digest output.  This codepoint is also
  defined for use with TLS 1.2.

EdDSA algorithms
: Indicates a signature algorithm using EdDSA as defined in
  {{RFC8032}} or its successors. Note that these correspond to the
  "PureEdDSA" algorithms and not the "prehash" variants.
{:br }

rsa_pkcs1_sha1, dsa_sha1, and ecdsa_sha1 SHOULD NOT be offered. Clients
offering these values for backwards compatibility MUST list them as the lowest
priority (listed after all other algorithms in SignatureSchemeList).
TLS 1.3 servers MUST NOT offer a SHA-1
signed certificate unless no valid certificate chain can be produced without it
(see {{server-certificate-selection}}).

The signatures on certificates that are self-signed or certificates that are
trust anchors are not validated since they begin a certification path (see
{{RFC5280}}, Section 3.2).  A certificate that begins a certification
path MAY use a signature algorithm that is not advertised as being supported
in the "signature_algorithms" extension.

Note that TLS 1.2 defines this extension differently. TLS 1.3 implementations
willing to negotiate TLS 1.2 MUST behave in accordance with the requirements of
{{RFC5246}} when negotiating that version. In particular:

* TLS 1.2 ClientHellos MAY omit this extension.

* In TLS 1.2, the extension contained hash/signature pairs. The pairs are
  encoded in two octets, so SignatureScheme values have been allocated to
  align with TLS 1.2's encoding. Some legacy pairs are left unallocated. These
  algorithms are deprecated as of TLS 1.3. They MUST NOT be offered or
  negotiated by any implementation. In particular, MD5 {{SLOTH}} and SHA-224
  MUST NOT be used.

* ECDSA signature schemes align with TLS 1.2's ECDSA hash/signature pairs.
  However, the old semantics did not constrain the signing curve.  If TLS 1.2 is
  negotiated, implementations MUST be prepared to accept a signature that uses
  any curve that they advertised in the "supported_groups" extension.

* Implementations that advertise support for RSASSA-PSS (which is mandatory in
  TLS 1.3), MUST be prepared to accept a signature using that scheme even when
  TLS 1.2 is negotiated. In TLS 1.2, RSASSA-PSS is used with RSA cipher suites.


### Certificate Authorities

The "certificate_authorities" extension is used to indicate the
certificate authorities which an endpoint supports and which SHOULD
be used by the receiving endpoint to guide certificate selection.

The body of the "certificate_authorities" extension consists of a
CertificateAuthoritiesExtension structure.

%%% Server Parameters Messages

       opaque DistinguishedName<1..2^16-1>;

       struct {
           DistinguishedName authorities<3..2^16-1>;
       } CertificateAuthoritiesExtension;

authorities
: A list of the distinguished names {{X501}} of acceptable
  certificate authorities, represented in DER-encoded {{X690}} format.  These
  distinguished names specify a desired distinguished name for trust anchor
  or subordinate CA; thus, this message can be used to
  describe known trust anchors as well as a desired authorization space.
{:br}

The client MAY send the "certificate_authorities" extension in the ClientHello
message. The server MAY send it in the CertificateRequest message.

The "trusted_ca_keys" extension, which serves a similar
purpose {{RFC6066}}, but is more complicated, is not used in TLS 1.3
(although it may appear in ClientHello messages from clients which are
offering prior versions of TLS).

### Negotiated Groups

When sent by the client, the "supported_groups" extension indicates
the named groups which the client supports for key exchange, ordered
from most preferred to least preferred.

Note: In versions of TLS prior to TLS 1.3, this extension was named
"elliptic_curves" and only contained elliptic curve groups. See {{RFC4492}} and
{{RFC7919}}. This extension was also used to negotiate
ECDSA curves. Signature algorithms are now negotiated independently (see
{{signature-algorithms}}).

The "extension_data" field of this extension contains a
"NamedGroupList" value:

%%% Supported Groups Extension

       enum {
           /* Elliptic Curve Groups (ECDHE) */
           obsolete_RESERVED(0x0001..0x0016),
           secp256r1(0x0017), secp384r1(0x0018), secp521r1(0x0019),
           obsolete_RESERVED(0x001A..0x001C),
           x25519(0x001D), x448(0x001E),

           /* Finite Field Groups (DHE) */
           ffdhe2048(0x0100), ffdhe3072(0x0101), ffdhe4096 (0x0102),
           ffdhe6144(0x0103), ffdhe8192(0x0104),

           /* Reserved Code Points */
           ffdhe_private_use(0x01FC..0x01FF),
           ecdhe_private_use(0xFE00..0xFEFF),
           obsolete_RESERVED(0xFF01..0xFF02),
           (0xFFFF)
       } NamedGroup;

       struct {
           NamedGroup named_group_list<2..2^16-1>;
       } NamedGroupList;

Elliptic Curve Groups (ECDHE)
: Indicates support for the corresponding named curve, defined
  either in FIPS 186-4 {{DSS}} or in {{RFC7748}}.
  Values 0xFE00 through 0xFEFF are reserved for private use.

Finite Field Groups (DHE)
: Indicates support of the corresponding finite field
  group, defined in {{RFC7919}}.
  Values 0x01FC through 0x01FF are reserved for private use.
{:br }

Items in named_group_list are ordered according to the client's
preferences (most preferred choice first).

As of TLS 1.3, servers are permitted to send the "supported_groups"
extension to the client. If the server has a group it prefers to the
ones in the "key_share" extension but is still willing to accept the
ClientHello, it SHOULD send "supported_groups" to update the client's
view of its preferences; this extension SHOULD contain all groups
the server supports, regardless of whether they are currently
supported by the client. Clients MUST NOT act upon any information
found in "supported_groups" prior to successful completion of the
handshake, but MAY use the information learned from a successfully
completed handshake to change what groups they use in their
"key_share" extension in subsequent connections.


### Key Share

The "key_share" extension contains the endpoint's cryptographic parameters.

Clients MAY send an empty client_shares vector in order to request
group selection from the server at the cost of an additional round trip.
(see {{hello-retry-request}})

%%% Key Exchange Messages

       struct {
           NamedGroup group;
           opaque key_exchange<1..2^16-1>;
       } KeyShareEntry;

group
: The named group for the key being exchanged.
  Finite Field Diffie-Hellman {{DH}} parameters are described in
  {{ffdhe-param}}; Elliptic Curve Diffie-Hellman parameters are
  described in {{ecdhe-param}}.

key_exchange
: Key exchange information.  The contents of this field are
  determined by the specified group and its corresponding
  definition.
{:br }

The "extension_data" field of this extension contains a
"KeyShare" value:

%%% Key Exchange Messages

       struct {
           select (Handshake.msg_type) {
               case client_hello:
                   KeyShareEntry client_shares<0..2^16-1>;

               case hello_retry_request:
                   NamedGroup selected_group;

               case server_hello:
                   KeyShareEntry server_share;
           };
       } KeyShare;

client_shares
: A list of offered KeyShareEntry values in descending order of client preference.
  This vector MAY be empty if the client is requesting a HelloRetryRequest.
  Each KeyShareEntry value MUST correspond to a group offered in the
  "supported_groups" extension and MUST appear in the same order.  However, the
  values MAY be a non-contiguous subset of the "supported_groups" extension and
  MAY omit the most preferred groups.

selected_group
: The mutually supported group the server intends to negotiate and
  is requesting a retried ClientHello/KeyShare for.

server_share
: A single KeyShareEntry value that is in the same group as one of the
  client's shares.
{:br }

Clients offer an arbitrary number of KeyShareEntry values, each
representing a single set of key exchange parameters. For instance, a
client might offer shares for several elliptic curves or multiple
FFDHE groups.  The key_exchange values for each KeyShareEntry MUST be
generated independently.  Clients MUST NOT offer multiple
KeyShareEntry values for the same group.  Clients MUST NOT offer any
KeyShareEntry values for groups not listed in the client's
"supported_groups" extension.  Servers MAY check for violations of
these rules and abort the handshake with an
"illegal_parameter" alert if one is violated.

Upon receipt of this extension in a HelloRetryRequest, the client MUST
verify that (1) the selected_group field corresponds to a group which was provided
in the "supported_groups" extension in the original ClientHello; and (2)
the selected_group field does not correspond to a group which was
provided in the "key_share" extension in the original ClientHello. If either of
these checks fails, then the client MUST abort the handshake with an
"illegal_parameter" alert.  Otherwise, when sending the new ClientHello, the
client MUST replace the original "key_share" extension with one
containing only a new KeyShareEntry for the group indicated in the
selected_group field of the triggering HelloRetryRequest.

If using (EC)DHE key establishment, servers offer exactly one
KeyShareEntry in the ServerHello. This value MUST correspond to the KeyShareEntry value offered
by the client that the server has selected for the negotiated key exchange.
Servers MUST NOT send a KeyShareEntry for any group not
indicated in the "supported_groups" extension and
MUST NOT send a KeyShareEntry when using the "psk_ke" PskKeyExchangeMode.
If a HelloRetryRequest was received by the client, the client MUST verify that the
selected NamedGroup in the ServerHello is the same as that in the HelloRetryRequest. If this check
fails, the client MUST abort the handshake with an "illegal_parameter" alert.

####  Diffie-Hellman Parameters {#ffdhe-param}

Diffie-Hellman {{DH}} parameters for both clients and servers are encoded in
the opaque key_exchange field of a KeyShareEntry in a KeyShare structure.
The opaque value contains the
Diffie-Hellman public value (Y = g^X mod p) for the specified group
(see {{RFC7919}} for group definitions)
encoded as a big-endian integer and padded with zeros to the size of p in
bytes.

Note: For a given Diffie-Hellman group, the padding results in all public keys
having the same length.

Peers MUST validate each other's public key Y by ensuring that 1 < Y
< p-1. This check ensures that the remote peer is properly behaved and
isn't forcing the local system into a small subgroup.


#### ECDHE Parameters {#ecdhe-param}

ECDHE parameters for both clients and servers are encoded in the
the opaque key_exchange field of a KeyShareEntry in a KeyShare structure.

For secp256r1, secp384r1 and secp521r1, the contents are the byte string
representation of an elliptic curve public value following the conversion
routine in Section 4.3.6 of ANSI X9.62 {{X962}}.

Although X9.62 supports multiple point formats, any given curve
MUST specify only a single point format. All curves currently
specified in this document MUST only be used with the uncompressed
point format (the format for all ECDH functions is considered
uncompressed). Peers MUST validate each other's public value Y by ensuring
that the point is a valid point on the elliptic
curve.

For the curves secp256r1, secp384r1 and secp521r1, the appropriate
validation procedures are defined in Section 4.3.7 of {{X962}}
and alternatively in Section 5.6.2.6  of {{KEYAGREEMENT}}.
This process consists of three steps: (1) verify that Y is not the point at
infinity (O), (2) verify that for Y = (x, y) both integers are in the correct
interval, (3) ensure that (x, y) is a correct solution to the elliptic curve equation.
For these curves, implementers do not need to verify membership in the correct subgroup.

For X25519 and X448, the contents of the public value are the byte string inputs and outputs of the
corresponding functions defined in {{RFC7748}}, 32 bytes for X25519 and 56
bytes for X448.

Note: Versions of TLS prior to 1.3 permitted point format negotiation;
TLS 1.3 removes this feature in favor of a single point format
for each curve.

### Pre-Shared Key Exchange Modes

In order to use PSKs, clients MUST also send a "psk_key_exchange_modes"
extension. The semantics of this extension are that the client only
supports the use of PSKs with these modes, which restricts both the
use of PSKs offered in this ClientHello and those which the server
might supply via NewSessionTicket.

A client MUST provide a "psk_key_exchange_modes" extension if it offers
a "pre_shared_key" extension. If clients offer "pre_shared_key" without
a "psk_key_exchange_modes" extension, servers MUST abort the handshake.
Servers MUST NOT select a key exchange mode that is not listed by the
client. This extension also restricts the modes for use with PSK resumption;
servers SHOULD NOT send NewSessionTicket with tickets that are not
compatible with the advertised modes; however, if a server does so, the impact
will just be that the client's attempts at resumption fail.

The server MUST NOT send a "psk_key_exchange_modes" extension.

%%% Key Exchange Messages

       enum { psk_ke(0), psk_dhe_ke(1), (255) } PskKeyExchangeMode;

       struct {
           PskKeyExchangeMode ke_modes<1..255>;
       } PskKeyExchangeModes;

psk_ke
: PSK-only key establishment. In this mode, the server MUST NOT
supply a "key_share" value.

psk_dhe_ke
: PSK with (EC)DHE key establishment. In this mode,
the client and servers MUST supply "key_share" values as described
in {{key-share}}.
{:br}

### Early Data Indication

When a PSK is used, the client can send application data
in its first flight of messages. If the client opts to do so, it MUST
supply an "early_data" extension as well as the "pre_shared_key"
extension.

The "extension_data" field of this extension contains an
"EarlyDataIndication" value.

%%% Key Exchange Messages

       struct {} Empty;

       struct {
           select (Handshake.msg_type) {
               case new_session_ticket:   uint32 max_early_data_size;
               case client_hello:         Empty;
               case encrypted_extensions: Empty;
           };
       } EarlyDataIndication;

See {{NewSessionTicket}} for the use of the max_early_data_size field.

For PSKs provisioned via NewSessionTicket, a server MUST validate that
the ticket age for the selected PSK identity (computed by subtracting
ticket_age_add from PskIdentity.obfuscated_ticket_age modulo 2^32)
is within a small tolerance of the
time since the ticket was issued (see {{replay-time}}).  If it is not,
the server SHOULD proceed with the handshake but reject 0-RTT, and
SHOULD NOT take any other action that assumes that this ClientHello is
fresh.

The parameters for the 0-RTT data (symmetric cipher suite, ALPN
protocol, etc.) are the same as those which were negotiated in the connection
which established the PSK. The PSK used to encrypt the early data
MUST be the first PSK listed in the client's "pre_shared_key" extension.

0-RTT messages sent in the first flight have the same (encrypted) content types
as their corresponding messages sent in other flights (handshake,
application_data, and alert respectively) but are protected under
different keys.  After receiving the server's Finished message, if the
server has accepted early data, an EndOfEarlyData message
will be sent to indicate the key change. This message will be encrypted
with the 0-RTT traffic keys.

A server which receives an "early_data" extension
MUST behave in one of three ways:

- Ignore the extension and return a regular 1-RTT response.  The server then
  ignores early data using trial decryption until it is able to receive the
  client's second flight and complete an ordinary 1-RTT handshake.

- Request that the client send another ClientHello by responding with a
  HelloRetryRequest.  A client MUST NOT include the "early_data" extension in
  its followup ClientHello.  The server then ignores early data by skipping
  all records with external content type of "application_data" (indicating
  that they are encrypted).

- Return its own extension in EncryptedExtensions,
  indicating that it intends to
  process the early data. It is not possible for the server
  to accept only a subset of the early data messages.

In order to accept early data, the server MUST have accepted a
PSK cipher suite and selected the first key offered in the
client's "pre_shared_key" extension. In addition, it MUST verify that
the following values are consistent with those negotiated in the
connection during which the ticket was established.

- The TLS version number and cipher suite.
- The selected ALPN {{RFC7301}} protocol, if any.

Future extensions MUST define their interaction with 0-RTT.

If any of these checks fail, the server MUST NOT respond
with the extension and must discard all the remaining first
flight data (thus falling back to 1-RTT). If the client attempts
a 0-RTT handshake but the server rejects it, the server will generally
not have the 0-RTT record protection keys and must instead
trial decrypt each record with the 1-RTT handshake keys
until it finds one that decrypts properly, and then pick up
the handshake from that point.

If the server chooses to accept the "early_data" extension,
then it MUST comply with the same error handling requirements
specified for all records when processing early data records.
Specifically, if the server fails to decrypt any 0-RTT record following
an accepted "early_data" extension it MUST terminate the connection
with a "bad_record_mac" alert as per {{record-payload-protection}}.

If the server rejects the "early_data" extension, the client application
MAY opt to retransmit early data once the handshake has been completed.
A TLS implementation SHOULD NOT automatically re-send early data;
applications are in a better position to decide when re-transmission is
appropriate.  Automatic re-transmission of early data could result in
assumptions about the status of the connection being incorrect. In
particular, a TLS implementation MUST NOT automatically re-send early
data unless the negotiated connection selects the same ALPN protocol. An
application might need to construct different messages if a different
protocol is selected. Similarly, if early data assumes anything about
the connection state, it might be sent in error after the handshake
completes.

### Pre-Shared Key Extension

The "pre_shared_key" extension is used to indicate the identity of the
pre-shared key to be used with a given handshake in association
with PSK key establishment.

The "extension_data" field of this extension contains a
"PreSharedKeyExtension" value:

%%% Key Exchange Messages

       struct {
           opaque identity<1..2^16-1>;
           uint32 obfuscated_ticket_age;
       } PskIdentity;

       opaque PskBinderEntry<32..255>;

       struct {
           select (Handshake.msg_type) {
               case client_hello:
                   PskIdentity identities<7..2^16-1>;
                   PskBinderEntry binders<33..2^16-1>;

               case server_hello:
                   uint16 selected_identity;
           };

       } PreSharedKeyExtension;

identity
: A label for a key. For instance, a ticket defined
  in {{ticket-establishment}}, or a label for a pre-shared key
  established externally.

obfuscated_ticket_age
: For each ticket, the time since the client learned about the server
  configuration that it is using, in milliseconds.  This value is
  added modulo 2^32 to the "ticket_age_add" value that was
  included with the ticket, see {{NewSessionTicket}}.  This addition
  prevents passive observers from correlating connections unless tickets
  are reused.  Note: because ticket lifetimes are restricted to a
  week, 32 bits is enough to represent any plausible age, even in
  milliseconds. For identities established externally an obfuscated_ticket_age of
  0 SHOULD be used, and servers MUST ignore the value.

identities
: A list of the identities that the client is willing
  to negotiate with the server. If sent alongside the "early_data"
  extension (see {{early-data-indication}}), the first identity is the
  one used for 0-RTT data.

binders
: A series of HMAC values, one for
  each PSK offered in the "pre_shared_keys" extension and in the same
  order, computed as described below.

selected_identity
: The server's chosen identity expressed as a (0-based) index into
  the identities in the client's list.
{: br}

Each PSK is associated with a single Hash algorithm. For PSKs established
via the ticket mechanism ({{NewSessionTicket}}), this is the Hash used for
the KDF. For externally established PSKs, the Hash algorithm MUST be set when the
PSK is established. The server must ensure that it selects a compatible
PSK (if any) and cipher suites.

Implementor's note: the most straightforward way to implement the
PSK/cipher suite matching requirements is to negotiate the cipher
suite first and then exclude any incompatible PSKs. Any unknown PSKs
(e.g., they are not in the PSK database or are encrypted with an
unknown key) SHOULD simply be ignored. If no acceptable PSKs are
found, the server SHOULD perform a non-PSK handshake if possible.

Prior to accepting PSK key establishment, the server MUST validate the
corresponding binder value (see {{psk-binder}} below). If this value is
not present or does not validate, the server MUST abort the handshake.
Servers SHOULD NOT attempt to validate multiple binders; rather they
SHOULD select a single PSK and validate solely the binder that
corresponds to that PSK. In order to accept PSK key establishment, the
server sends a "pre_shared_key" extension indicating the selected
identity.

Clients MUST verify that the server's selected_identity is within the
range supplied by the client, that the server selected a cipher suite
containing a Hash associated with the PSK and that a server
"key_share" extension is present if required by the
ClientHello "psk_key_exchange_modes". If these values are not
consistent
the client MUST abort the handshake with an "illegal_parameter" alert.

If the server supplies an "early_data" extension, the client MUST
verify that the server's selected_identity is 0. If any
other value is returned, the client MUST abort the handshake
with an "illegal_parameter" alert.

This extension MUST be the last extension in the ClientHello (this
facilitates implementation as described below). Servers MUST check
that it is the last extension and otherwise fail the handshake with an
"illegal_parameter" alert.

#### PSK Binder

The PSK binder value forms a binding between a PSK and the current
handshake, as well as between the handshake in which the PSK was
generated (if via a NewSessionTicket message) and the handshake where
it was used.  Each entry in the binders list is computed as an HMAC
over a transcript hash (see {{the-transcript-hash}}) containing a partial ClientHello
up to and including the PreSharedKeyExtension.identities field. That
is, it includes all of the ClientHello but not the binders list
itself. The length fields for the message (including the overall
length, the length of the extensions block, and the length of the
"pre_shared_key" extension) are all set as if binders of the correct
lengths were present.

The binding_value is computed in the same way as the Finished
message ({{finished}}) but with the BaseKey being the binder_key
derived via the key schedule from the corresponding PSK which
is being offered (see {{key-schedule}}).

If the handshake includes a HelloRetryRequest, the initial ClientHello
and HelloRetryRequest are included in the transcript along with the
new ClientHello.  For instance, if the client sends ClientHello1, its
binder will be computed over:

       Transcript-Hash(ClientHello1[truncated])

If the server responds with HelloRetryRequest, and the client then sends
ClientHello2, its binder will be computed over:

       Transcript-Hash(ClientHello1,
                       HelloRetryRequest,
                       ClientHello2[truncated])

The full ClientHello is included in all other handshake hash computations.
Note that in the first flight, ClientHello1[truncated] is hashed directly,
but in the second flight, it is hashed and then reinjected as a
"handshake_hash" message, as described in {{the-transcript-hash}}.

#### Processing Order

Clients are permitted to "stream" 0-RTT data until they
receive the server's Finished, only then sending the EndOfEarlyData
message. In order to avoid deadlocks, when accepting "early_data",
servers MUST process the client's ClientHello and then immediately
send the ServerHello, rather than waiting for the client's
EndOfEarlyData message.

#### Replay Properties {#replay-time}

As noted in {{zero-rtt-data}}, TLS provides a limited mechanism for
replay protection for data sent by the client in the first flight.

The "obfuscated_ticket_age" parameter in the client's
"pre_shared_key" extension SHOULD be used by
servers to limit the time over which the first flight might be
replayed.  A server can store the time at which it sends a
ticket to the client, or encode the time in the ticket.  Then, each
time it receives an "pre_shared_key" extension, it can subtract the base value and
check to see if the value used by the client matches its expectations.

The ticket age (the value with "ticket_age_add" subtracted) provided by the
client will be shorter than the
actual time elapsed on the server by a single round trip time.  This
difference is comprised of the delay in sending the NewSessionTicket
message to the client, plus the time taken to send the ClientHello to
the server.  For this reason, a server SHOULD measure the round trip
time prior to sending the NewSessionTicket message and account for
that in the value it saves.

To properly validate the ticket age, a server needs to save at least two items:

- The time that the server generated the session ticket and the estimated round
  trip time can be added together to form a baseline time.
- The "ticket_age_add" parameter from the NewSessionTicket is needed to recover
  the ticket age from the "obfuscated_ticket_age" parameter.

There are several potential sources of error that make an exact
measurement of time difficult.  Variations in client and server clock rates
are likely to be minimal, though potentially with gross time corrections.  Network
propagation delays are most likely causes of a mismatch in legitimate
values for elapsed time.  Both the NewSessionTicket and ClientHello
messages might be retransmitted and therefore delayed, which might be
hidden by TCP.

A small allowance for errors in clocks and variations in measurements
is advisable.  However, any allowance also increases the opportunity
for replay.  In this case, it is better to reject early data and fall back
to a full 1-RTT handshake than to risk greater exposure to replay attacks.
In common network topologies for browser clients, small allowances on the
order of ten seconds are reasonable.  Clock skew distributions are not
symmetric, so the optimal tradeoff may involve an asymmetric replay window.


## Server Parameters

The next two messages from the server, EncryptedExtensions and
CertificateRequest, contain information from the server
that determines the rest of the handshake. These messages
are encrypted with keys derived from the server_handshake_traffic_secret.

###  Encrypted Extensions

In all handshakes, the server MUST send the
EncryptedExtensions message immediately after the
ServerHello message. This is the first message that is encrypted
under keys derived from the server_handshake_traffic_secret.

The EncryptedExtensions message contains extensions
which should be protected, i.e., any which are not needed to
establish the cryptographic context, but which are not
associated with individual certificates. The client
MUST check EncryptedExtensions for the presence of any forbidden
extensions and if any are found MUST abort the handshake with an
"illegal_parameter" alert.

Structure of this message:

%%% Server Parameters Messages

       struct {
           Extension extensions<0..2^16-1>;
       } EncryptedExtensions;

extensions
: A list of extensions. For more information, see the table in {{extensions}}.
{:br }

###  Certificate Request

A server which is authenticating with a certificate MAY optionally
request a certificate from the client. This message, if sent, MUST
follow EncryptedExtensions.

Structure of this message:

%%% Server Parameters Messages

       struct {
           opaque certificate_request_context<0..2^8-1>;
           Extension extensions<2..2^16-1>;
       } CertificateRequest;

certificate_request_context
: An opaque string which identifies the certificate request and
  which will be echoed in the client's Certificate message. The
  certificate_request_context MUST be unique within the scope
  of this connection (thus preventing replay of client
  CertificateVerify messages). This field SHALL be zero length
  unless used for the post-handshake authentication exchanges
  described in {{post-handshake-authentication}}.

extensions
: An optional set of extensions describing the parameters of the
  certificate being requested. The "signature_algorithms"
  extension MUST be specified.
  Clients MUST ignore unrecognized extensions.
{:br}

In prior versions of TLS, the CertificateRequest message
carried a list of signature algorithms and certificate authorities
which the server would accept. In TLS 1.3 the former is expressed
by sending the "signature_algorithms" extension. The latter is
expressed by sending the "certificate_authorities" extension
(see {{certificate-authorities}}).

Servers which are authenticating with a PSK MUST NOT send the
CertificateRequest message.


#### OID Filters

The "oid_filters" extension allows servers to provide a set of OID/value
pairs which it would like the client's certificate to match. This
extension MUST only be sent in the CertificateRequest message.

%%% Server Parameters Messages

       struct {
           opaque certificate_extension_oid<1..2^8-1>;
           opaque certificate_extension_values<0..2^16-1>;
       } OIDFilter;

       struct {
           OIDFilter filters<0..2^16-1>;
       } OIDFilterExtension;


filters
: A list of certificate extension OIDs {{RFC5280}} with their allowed
  values, represented in DER-encoded {{X690}} format. Some certificate
  extension OIDs allow multiple values (e.g., Extended Key Usage).
  If the server has included a non-empty certificate_extensions list,
  the client certificate included in the response
  MUST contain all of the specified extension
  OIDs that the client recognizes. For each extension OID recognized
  by the client, all of the specified values MUST be present in the
  client certificate (but the certificate MAY have other values as
  well). However, the client MUST ignore and skip any unrecognized
  certificate extension OIDs. If the client ignored some of the
  required certificate extension OIDs and supplied a certificate
  that does not satisfy the request, the server MAY at its discretion
  either continue the connection without client authentication, or
  abort the handshake with an "unsupported_certificate" alert.

  PKIX RFCs define a variety of certificate extension OIDs and their
  corresponding value types. Depending on the type, matching
  certificate extension values are not necessarily bitwise-equal. It
  is expected that TLS implementations will rely on their PKI
  libraries to perform certificate selection using certificate
  extension OIDs.

  This document defines matching rules for two standard certificate
  extensions defined in {{RFC5280}}:

  - The Key Usage extension in a certificate matches the request when
  all key usage bits asserted in the request are also asserted in the
  Key Usage certificate extension.

  - The Extended Key Usage extension in a certificate matches the
  request when all key purpose OIDs present in the request are also
  found in the Extended Key Usage certificate extension. The special
  anyExtendedKeyUsage OID MUST NOT be used in the request.

  Separate specifications may define matching rules for other certificate
  extensions.
{:br }

## Authentication Messages

As discussed in {{protocol-overview}}, TLS generally uses a common
set of messages for authentication, key confirmation, and handshake
integrity: Certificate, CertificateVerify, and Finished.
(The PreSharedKey binders also perform key confirmation, in a
similar fashion.) These three
messages are always sent as the last messages in their handshake
flight. The Certificate and CertificateVerify messages are only
sent under certain circumstances, as defined below. The Finished
message is always sent as part of the Authentication block.
These messages are encrypted under keys derived from
\[sender]_handshake_traffic_secret.

The computations for the Authentication messages all uniformly
take the following inputs:

- The certificate and signing key to be used.
- A Handshake Context consisting of the set of messages to be
  included in the transcript hash.
- A base key to be used to compute a MAC key.

Based on these inputs, the messages then contain:

Certificate
: The certificate to be used for authentication and any
supporting certificates in the chain. Note that certificate-based
client authentication is not available in the 0-RTT case.

CertificateVerify
: A signature over the value Transcript-Hash(Handshake Context, Certificate)

Finished
: A MAC over the value Transcript-Hash(Handshake Context, Certificate, CertificateVerify)
using a MAC key derived from the base key.
{:br}


The following table defines the Handshake Context and MAC Base Key
for each scenario:

| Mode | Handshake Context | Base Key |
|------|-------------------|----------|
| Server | ClientHello ... later of EncryptedExtensions/CertificateRequest | server_handshake_traffic_secret |
| Client | ClientHello ... later of ServerFinished/EndOfEarlyData | client_handshake_traffic_secret |
| Post-Handshake | ClientHello ... ClientFinished + CertificateRequest | client_traffic_secret_N |


### The Transcript Hash

Many of the cryptographic computations in TLS make use of a transcript
hash. This value is computed by hashing the concatenation of
each included handshake message, including the handshake
message header carrying the handshake message type and length fields,
but not including record layer headers. I.e.,

     Transcript-Hash(M1, M2, ... MN) = Hash(M1 || M2 ... MN)

As an exception to this general rule, when the server responds to a
ClientHello with a HelloRetryRequest, the value of ClientHello1 is
replaced with a special synthetic handshake message of handshake
type "message_hash" containing Hash(ClientHello1). I.e.,

     Transcript-Hash(ClientHello1, HelloRetryRequest, ... MN) =
         Hash(message_hash ||                 // Handshake Type
              00 00 Hash.length ||   // Handshake message length
              Hash(ClientHello1) ||  // Hash of ClientHello1
              HelloRetryRequest ... MN)

The reason for this construction is to allow the server to do a
stateless HelloRetryRequest by storing just the hash of ClientHello1
in the cookie, rather than requiring it to export the entire intermediate
hash state (see {{cookie}}).

For concreteness, the transcript hash is always taken from the
following sequence of handshake messages, starting at the first
ClientHello and including only those messages that were sent:
ClientHello, HelloRetryRequest, ClientHello, ServerHello,
EncryptedExtensions, Server CertificateRequest, Server Certificate,
Server CertificateVerify, Server Finished, EndOfEarlyData, Client
Certificate, Client CertificateVerify, Client Finished.

In general, implementations can implement the transcript by keeping a
running transcript hash value based on the negotiated hash. Note,
however, that subsequent post-handshake authentications do not include
each other, just the messages through the end of the main handshake.

###  Certificate

The server MUST send a Certificate message whenever the agreed-upon
key exchange method uses certificates for authentication (this
includes all key exchange methods defined in this document except PSK).
This message conveys the endpoint's certificate chain to the peer.

The client MUST send a Certificate message if and only if the server has
requested client authentication via a CertificateRequest message
({{certificate-request}}). If the server requests client authentication
but no suitable certificate is available, the client
MUST send a Certificate message containing no certificates (i.e., with
the "certificate_list" field having length 0).

Structure of this message:

%%% Authentication Messages

       opaque ASN1Cert<1..2^24-1>;

       struct {
           ASN1Cert cert_data;
           Extension extensions<0..2^16-1>;
       } CertificateEntry;

       struct {
           opaque certificate_request_context<0..2^8-1>;
           CertificateEntry certificate_list<0..2^24-1>;
       } Certificate;

certificate_request_context
: If this message is in response to a CertificateRequest, the
  value of certificate_request_context in that message. Otherwise
  (in the case of server authentication), this field SHALL be zero length.

certificate_list
: This is a sequence (chain) of CertificateEntry structures, each
  containing a single certificate and set of extensions. The sender's
  certificate MUST come in the first CertificateEntry in the list.
  Each following certificate SHOULD directly certify one preceding it.
  Because certificate validation requires that trust anchors be distributed
  independently, a certificate that specifies a
  trust anchor MAY be omitted from the chain, provided that
  supported peers are known to possess any omitted certificates.

extensions:
: A set of extension values for the CertificateEntry. The "Extension"
  format is defined in {{extensions}}. Valid extensions include
  OCSP Status extensions ({{RFC6066}} and {{!RFC6961}}) and
  SignedCertificateTimestamps ({{!RFC6962}}).  An extension MUST only be present
  in a Certificate message if the corresponding
  ClientHello extension was presented in the initial handshake.
  If an extension applies to the entire chain, it SHOULD be included
  in the first CertificateEntry.
{:br }

Note: Prior to TLS 1.3, "certificate_list" ordering required each certificate
to certify the one immediately preceding it;
however, some implementations allowed some flexibility. Servers sometimes send
both a current and deprecated intermediate for transitional purposes, and others
are simply configured incorrectly, but these cases can nonetheless be validated
properly. For maximum compatibility, all implementations SHOULD be prepared to
handle potentially extraneous certificates and arbitrary orderings from any TLS
version, with the exception of the end-entity certificate which MUST be first.

The server's certificate_list MUST always be non-empty. A client will
send an empty certificate_list if it does not have an appropriate
certificate to send in response to the server's authentication
request.

#### OCSP Status and SCT Extensions

{{RFC6066}} and {{!RFC6961}} provide extensions to negotiate the server
sending OCSP responses to the client. In TLS 1.2 and below, the
server replies with an empty extension to indicate negotiation of this
extension and the OCSP information is carried in a CertificateStatus
message. In TLS 1.3, the server's OCSP information is carried in
an extension in the CertificateEntry containing the associated
certificate. Specifically:
The body of the "status_request" extension
from the server MUST be a CertificateStatus structure as defined
in {{RFC6066}}.

A server MAY request that a client present an OCSP response with its
certificate by sending an empty "status_request" extension in its
CertificateRequest message. If the client opts to send an OCSP response, the
body of its "status_request" extension MUST be a CertificateStatus structure as
defined in {{RFC6066}}.

Similarly, {{!RFC6962}} provides a mechanism for a server to send a
Signed Certificate Timestamp (SCT) as an extension in the ServerHello.
In TLS 1.3, the server's SCT information is carried in an extension in
CertificateEntry.

#### Server Certificate Selection

The following rules apply to the certificates sent by the server:

- The certificate type MUST be X.509v3 {{RFC5280}}, unless explicitly negotiated
  otherwise (e.g., {{RFC5081}}).

- The server's end-entity certificate's public key (and associated
  restrictions) MUST be compatible with the selected authentication
  algorithm (currently RSA or ECDSA).

- The certificate MUST allow the key to be used for signing (i.e., the
  digitalSignature bit MUST be set if the Key Usage extension is present) with
  a signature scheme indicated in the client's "signature_algorithms" extension.

- The "server_name" and "trusted_ca_keys" extensions {{RFC6066}} are used to
  guide certificate selection. As servers MAY require the presence of the "server_name"
  extension, clients SHOULD send this extension, when applicable.

All certificates provided by the server MUST be signed by a
signature algorithm that appears in the "signature_algorithms"
extension provided by the client, if they are able to provide such
a chain (see {{signature-algorithms}}).
Certificates that are self-signed
or certificates that are expected to be trust anchors are not validated as
part of the chain and therefore MAY be signed with any algorithm.

If the server cannot produce a certificate chain that is signed only via the
indicated supported algorithms, then it SHOULD continue the handshake by sending
the client a certificate chain of its choice that may include algorithms
that are not known to be supported by the client. This fallback chain MAY
use the deprecated SHA-1 hash algorithm only if the "signature_algorithms"
extension provided by the client permits it.
If the client cannot construct an acceptable chain using the provided
certificates and decides to abort the handshake, then it MUST abort the
handshake with an "unsupported_certificate" alert.

If the server has multiple certificates, it chooses one of them based on the
above-mentioned criteria (in addition to other criteria, such as transport
layer endpoint, local configuration and preferences).


#### Client Certificate Selection

The following rules apply to certificates sent by the client:

- The certificate type MUST be X.509v3 {{RFC5280}}, unless explicitly negotiated
  otherwise (e.g., {{RFC5081}}).

- If the certificate_authorities list in the CertificateRequest
  message was non-empty, at least one of the certificates in the certificate
  chain SHOULD be issued by one of the listed CAs.

- The certificates MUST be signed using an acceptable signature
  algorithm, as described in {{certificate-request}}.  Note that this
  relaxes the constraints on certificate-signing algorithms found in
  prior versions of TLS.

- If the certificate_extensions list in the CertificateRequest message
  was non-empty, the end-entity certificate MUST match the extension OIDs
  recognized by the client, as described in {{certificate-request}}.

Note that, as with the server certificate, there are certificates that use
algorithm combinations that cannot be currently used with TLS.


#### Receiving a Certificate Message

In general, detailed certificate validation procedures are out of scope for
TLS (see {{RFC5280}}). This section provides TLS-specific requirements.

If the server supplies an empty Certificate message, the client MUST abort
the handshake with a "decode_error" alert.

If the client does not send any certificates,
the server MAY at its discretion either continue the handshake without client
authentication, or abort the handshake with a "certificate_required" alert. Also, if some
aspect of the certificate chain was unacceptable (e.g., it was not signed by a
known, trusted CA), the server MAY at its discretion either continue the
handshake (considering the client unauthenticated) or abort the handshake.

Any endpoint receiving any certificate signed using any signature algorithm
using an MD5 hash MUST abort the handshake with a "bad_certificate" alert.
SHA-1 is deprecated and it is RECOMMENDED that
any endpoint receiving any certificate signed using any signature algorithm
using a SHA-1 hash abort the handshake with a "bad_certificate" alert.
All endpoints are RECOMMENDED to transition to SHA-256 or better as soon
as possible to maintain interoperability with implementations
currently in the process of phasing out SHA-1 support.

Note that a certificate containing a key for one signature algorithm
MAY be signed using a different signature algorithm (for instance,
an RSA key signed with an ECDSA key).


###  Certificate Verify


This message is used to provide explicit proof that an endpoint
possesses the private key corresponding to its certificate
and also provides integrity for the handshake up
to this point. Servers MUST send this message when
authenticating via a certificate.
Clients MUST send this
message whenever authenticating via a certificate (i.e., when
the Certificate message is non-empty). When sent, this message MUST appear immediately
after the Certificate message and immediately prior to the Finished
message.

Structure of this message:

%%% Authentication Messages

       struct {
           SignatureScheme algorithm;
           opaque signature<0..2^16-1>;
       } CertificateVerify;

The algorithm field specifies the signature algorithm used (see
{{signature-algorithms}} for the definition of this field). The
signature is a digital signature using that algorithm. The content
to be signed is the hash output as described in
{{authentication-messages}} namely:

       Transcript-Hash(Handshake Context, Certificate)

The digital signature is then computed over the concatenation of:

- A string that consists of octet 32 (0x20) repeated 64 times
- The context string
- A single 0 byte which serves as the separator
- The content to be signed

This structure is intended to prevent an attack on previous versions
of TLS in which the ServerKeyExchange format meant that
attackers could obtain a signature of a message with a chosen 32-byte
prefix (ClientHello.random). The initial 64-byte pad clears that prefix
along with the server-controlled ServerHello.random.

The context string for a server signature is
"TLS 1.3, server CertificateVerify"
and for a client signature is "TLS 1.3, client
CertificateVerify". It is used to provide separation between signatures
made in different contexts, helping against potential cross-protocol attacks.

For example, if the transcript hash was 32 bytes of
01 (this length would make sense for SHA-256), the content covered by
the digital signature for a server CertificateVerify would be:

       2020202020202020202020202020202020202020202020202020202020202020
       2020202020202020202020202020202020202020202020202020202020202020
       544c5320312e332c207365727665722043657274696669636174655665726966
       79
       00
       0101010101010101010101010101010101010101010101010101010101010101

On the sender side the process for computing the signature field of the
CertificateVerify message takes as input:

- The content covered by the digital signature
- The private signing key corresponding to the certificate sent in the
  previous message

If the CertificateVerify message is sent by a server, the signature
algorithm MUST be one offered in the
client's "signature_algorithms" extension unless no valid certificate chain can be
produced without unsupported algorithms (see {{signature-algorithms}}).

If sent by a client, the signature algorithm used in the signature
MUST be one of those present in the supported_signature_algorithms
field of the CertificateRequest message.

In addition, the signature algorithm MUST be compatible with the key
in the sender's end-entity certificate. RSA signatures MUST use an
RSASSA-PSS algorithm, regardless of whether RSASSA-PKCS1-v1_5 algorithms
appear in "signature_algorithms". SHA-1 MUST NOT be used in any signatures in
CertificateVerify. All SHA-1 signature algorithms in this specification are
defined solely for use in legacy certificates, and are not valid for
CertificateVerify signatures.

The receiver of a CertificateVerify MUST verify the signature field. The
verification process takes as input:

- The content covered by the digital signature
- The public key contained in the end-entity certificate found in the
  associated Certificate message.
- The digital signature received in the signature field of the
  CertificateVerify message

If the verification fails, the receiver MUST terminate the handshake
with a "decrypt_error" alert.

Note: When used with non-certificate-based handshakes (e.g., PSK), the
client's signature does not cover the server's certificate directly.
When the PSK was established through a NewSessionTicket, the client's
signature transitively covers the server's certificate through
the PSK binder. {{PSK-FINISHED}}
describes a concrete attack on constructions that do not bind to
the server's certificate. It is unsafe to use certificate-based client
authentication when the client might potentially share the same
PSK/key-id pair with two different endpoints and implementations
MUST NOT combine external PSKs with certificate-based authentication.

###  Finished

The Finished message is the final message in the authentication
block. It is essential for providing authentication of the handshake
and of the computed keys.

Recipients of Finished messages MUST verify that the contents are
correct and if incorrect MUST terminate the connection
with a "decrypt_error" alert.

Once a side has sent its Finished message and received and
validated the Finished message from its peer, it may begin to send and
receive application data over the connection.
Early data may be sent prior to the receipt of the peer's Finished
message, per {{early-data-indication}}.

The key used to compute the finished message is computed from the
Base key defined in {{authentication-messages}} using HKDF (see
{{key-schedule}}). Specifically:

~~~
finished_key =
    HKDF-Expand-Label(BaseKey, "finished", "", Hash.length)
~~~

Structure of this message:

%%% Authentication Messages

       struct {
           opaque verify_data[Hash.length];
       } Finished;


The verify_data value is computed as follows:

       verify_data =
           HMAC(finished_key,
                Transcript-Hash(Handshake Context,
                                Certificate*, CertificateVerify*))

       * Only included if present.

Where HMAC {{RFC2104}} uses the Hash algorithm for the handshake.
As noted above, the HMAC input can generally be implemented by a running
hash, i.e., just the handshake hash at this point.

In previous versions of TLS, the verify_data was always 12 octets long. In
TLS 1.3, it is the size of the HMAC output for the
Hash used for the handshake.

Note: Alerts and any other record types are not handshake messages
and are not included in the hash computations.

Any records following a 1-RTT Finished message MUST be encrypted under the
appropriate application traffic key as described in {{updating-traffic-keys}}.
In particular, this includes any alerts sent by the
server in response to client Certificate and CertificateVerify messages.

## End of Early Data

%%% Updating Keys

       struct {} EndOfEarlyData;

If the server sent an "early_data" extension, the client MUST send an
EndOfEarlyData after receiving the server Finished. This indicates that all
0-RTT application_data messages, if any, have been transmitted and
that the following records are protected
under handshake traffic keys. Servers MUST NOT send this
message and clients receiving it MUST terminate the connection
with an "unexpected_message" alert. This message is encrypted
under keys derived from the client_early_traffic_secret.

## Post-Handshake Messages

TLS also allows other messages to be sent after the main handshake.
These messages use a handshake content type and are encrypted under the
appropriate application traffic key.

### New Session Ticket Message {#NewSessionTicket}

At any time after the server has received the client Finished message, it MAY send
a NewSessionTicket message. This message creates a pre-shared key
(PSK) binding between the ticket value and the resumption master secret.

The client MAY use this PSK for future handshakes by including the
ticket value in the "pre_shared_key" extension in its ClientHello
({{pre-shared-key-extension}}). Servers MAY send multiple tickets on a
single connection, either immediately after each other or
after specific events. For instance, the server might send
a new ticket after post-handshake
authentication in order to encapsulate the additional client
authentication state. Clients SHOULD attempt to use each
ticket no more than once, with more recent tickets being used
first.

Any ticket MUST only be resumed with a cipher suite that has the
same KDF hash as that used to establish the original connection,
and only if the client provides the same SNI value as in the original
connection, as described in Section 3 of {{RFC6066}}.

Note: Although the resumption master secret depends on the client's second
flight, servers which do not request client authentication MAY compute
the remainder of the transcript independently and then send a
NewSessionTicket immediately upon sending its Finished rather than
waiting for the client Finished.  This might be appropriate in cases
where the client is expected to open multiple TLS connections in
parallel and would benefit from the reduced overhead of a resumption
handshake, for example.


%%% Ticket Establishment

       struct {
           uint32 ticket_lifetime;
           uint32 ticket_age_add;
           opaque ticket<1..2^16-1>;
           Extension extensions<0..2^16-2>;
       } NewSessionTicket;

ticket_lifetime
: Indicates the lifetime in seconds as a 32-bit unsigned integer in
  network byte order from the time of ticket issuance.
  Servers MUST NOT use any value more than 604800 seconds (7 days).
  The value of zero indicates that the ticket should be discarded
  immediately. Clients MUST NOT cache tickets for longer than
  7 days, regardless of the ticket_lifetime, and MAY delete the ticket
  earlier based on local policy. A server MAY treat a ticket as valid
  for a shorter period of time than what is stated in the
  ticket_lifetime.

ticket_age_add
: A securely generated, random 32-bit value that is used to obscure the age of
  the ticket that the client includes in the "pre_shared_key" extension.
  The client-side ticket age is added to this value modulo 2^32 to
  obtain the value that is transmitted by the client.

ticket
: The value of the ticket to be used as the PSK identity.
The ticket itself is an opaque label. It MAY either be a database
lookup key or a self-encrypted and self-authenticated value. Section
4 of {{RFC5077}} describes a recommended ticket construction mechanism.

extensions
: A set of extension values for the ticket. The "Extension"
  format is defined in {{extensions}}. Clients MUST ignore
  unrecognized extensions.
{:br }

The sole extension currently defined for NewSessionTicket is
"early_data", indicating that the ticket may be used to send 0-RTT data
({{early-data-indication}})). It contains the following value:

max_early_data_size
: The maximum amount of 0-RTT data that the client is allowed to send when using
  this ticket, in bytes. Only Application Data payload (i.e., plaintext but
  not padding or the inner content type byte) is counted. A server
  receiving more than max_early_data_size bytes of 0-RTT data
  SHOULD terminate the connection with an "unexpected_message" alert.
{:br }

Note that in principle it is possible to continue issuing new tickets
which continue to indefinitely extend the lifetime of the keying
material originally derived from an initial non-PSK handshake (which
was most likely tied to the peer's certificate). It is RECOMMENDED
that implementations place limits on the total lifetime of such keying
material; these limits should take into account the lifetime of the
peer's certificate, the likelihood of intervening revocation,
and the time since the peer's online CertificateVerify signature.

### Post-Handshake Authentication

The server is permitted to request client authentication at any time
after the handshake has completed by sending a CertificateRequest
message. The client SHOULD respond with the appropriate Authentication
messages. If the client chooses to authenticate, it MUST send
Certificate, CertificateVerify, and Finished. If it declines, it
MUST send a Certificate message containing no certificates followed by Finished.

Note: Because client authentication may require prompting the user,
servers MUST be prepared for some delay, including receiving an
arbitrary number of other messages between sending the
CertificateRequest and receiving a response. In addition, clients which receive multiple
CertificateRequests in close succession MAY respond to them in a
different order than they were received (the
certificate_request_context value allows the server to disambiguate
the responses).


### Key and IV Update {#key-update}

%%% Updating Keys

       enum {
           update_not_requested(0), update_requested(1), (255)
       } KeyUpdateRequest;

       struct {
           KeyUpdateRequest request_update;
       } KeyUpdate;


request_update
: Indicates whether the recipient of the KeyUpdate should respond with its
own KeyUpdate. If an implementation receives any other value, it MUST
terminate the connection with an "illegal_parameter" alert.
{:br }

The KeyUpdate handshake message is used to indicate that the sender is
updating its sending cryptographic keys. This message can be sent by
either peer after it has sent a Finished message.
Implementations that receive a KeyUpdate message
prior to receiving a Finished message
MUST terminate the connection with an "unexpected_message" alert.
After sending a KeyUpdate message, the sender SHALL send all its traffic using the
next generation of keys, computed as described in
{{updating-traffic-keys}}. Upon receiving a KeyUpdate, the receiver
MUST update its receiving keys.

If the request_update field is set to "update_requested" then the receiver MUST
send a KeyUpdate of its own with request_update set to "update_not_requested" prior
to sending its next application data record. This mechanism allows either side to force an update to the
entire connection, but causes an implementation which
receives multiple KeyUpdates while it is silent to respond with
a single update. Note that implementations may receive an arbitrary
number of messages between sending a KeyUpdate with request_update set
to update_requested and receiving the
peer's KeyUpdate, because those messages may already be in flight.
However, because send and receive keys are derived from independent
traffic secrets, retaining the receive traffic secret does not threaten
the forward secrecy of data sent before the sender changed keys.

If implementations independently send their own KeyUpdates with
request_update set to "update_requested", and they cross in flight, then each side
will also send a response, with the result that each side increments
by two generations.

Both sender and receiver MUST encrypt their KeyUpdate
messages with the old keys. Additionally, both sides MUST enforce that
a KeyUpdate with the old key is received before accepting any messages
encrypted with the new key. Failure to do so may allow message truncation
attacks.

#  Record Protocol

The TLS record protocol takes messages to be transmitted, fragments
the data into manageable blocks, protects the records, and transmits
the result. Received data is verified and decrypted, reassembled, and
then delivered to higher-level clients.

TLS records are typed, which allows multiple higher-level protocols to
be multiplexed over the same record layer. This document specifies
three content types: handshake, application data, and alert.
Implementations MUST NOT send record types not defined in this
document unless negotiated by some extension. If a TLS implementation
receives an unexpected record type, it MUST terminate the connection
with an "unexpected_message" alert.  New record content type values are
assigned by IANA in the TLS Content Type Registry as described in
{{iana-considerations}}.

## Record Layer

The record layer fragments information blocks into TLSPlaintext
records carrying data in chunks of 2^14 bytes or less. Message
boundaries are handled differently depending on the underlying
ContentType. Any future content types MUST specify appropriate
rules. Note that these rules are stricter than what was enforced in TLS 1.2.

Handshake messages MAY be coalesced into a single
TLSPlaintext record or fragmented across several records, provided
that:

- Handshake messages MUST NOT be interleaved with other record
  types. That is, if a handshake message is split over two or more
  records, there MUST NOT be any other records between them.

- Handshake messages MUST NOT span key changes. Because
  the ClientHello, EndOfEarlyData, ServerHello, Finished, and KeyUpdate messages
  can arrive immediately prior to a key change,
  upon receiving these messages a receiver MUST verify that the end
  of these messages aligns with a record boundary; if not, then it MUST
  terminate the connection with an "unexpected_message" alert.

Implementations MUST NOT send zero-length fragments of Handshake
types, even if those fragments contain padding.

Alert messages ({{alert-protocol}}) MUST NOT be fragmented across
records and multiple Alert messages MUST NOT be coalesced into a
single TLSPlaintext record. In other words, a record with an Alert
type MUST contain exactly one message.

Application Data messages contain data that is opaque to
TLS. Application Data messages are always protected. Zero-length
fragments of Application Data MAY be sent as they are potentially
useful as a traffic analysis countermeasure.


%%% Record Layer

       enum {
           invalid_RESERVED(0),
           change_cipher_spec_RESERVED(20),
           alert(21),
           handshake(22),
           application_data(23),
           (255)
       } ContentType;

       struct {
           ContentType type;
           ProtocolVersion legacy_record_version;
           uint16 length;
           opaque fragment[TLSPlaintext.length];
       } TLSPlaintext;

type
: The higher-level protocol used to process the enclosed fragment.

legacy_record_version
: This value MUST be set to 0x0301 for all records generated by a
  TLS 1.3 implementation.
  This field is deprecated and MUST be ignored for all purposes.
  Previous versions of TLS would use other values in this field
  under some circumstances.

length
: The length (in bytes) of the following TLSPlaintext.fragment. The
  length MUST NOT exceed 2^14 bytes. An endpoint that receives a record
  that exceeds this length MUST terminate the connection with a
  "record_overflow" alert.

fragment
: The data being transmitted. This value is transparent and is treated as an
  independent block to be dealt with by the higher-level protocol
  specified by the type field.
{:br }

This document describes TLS 1.3, which uses the version 0x0304.
This version value is historical, deriving from the use of 0x0301
for TLS 1.0 and 0x0300 for SSL 3.0. In order to maximize backwards
compatibility, the record layer version identifies as simply TLS 1.0.
Endpoints supporting multiple versions negotiate the version to use
by following the procedure and requirements in {{backward-compatibility}}.

When record protection has not yet been engaged, TLSPlaintext
structures are written directly onto the wire. Once record protection
has started, TLSPlaintext records are protected and sent as
described in the following section.

## Record Payload Protection

The record protection functions translate a TLSPlaintext structure into a
TLSCiphertext. The deprotection functions reverse the process. In TLS 1.3,
as opposed to previous versions of TLS, all ciphers are modeled as
"Authenticated Encryption with Additional Data" (AEAD) {{RFC5116}}.
AEAD functions provide an unified encryption and authentication
operation which turns plaintext into authenticated ciphertext and
back again. Each encrypted record consists of a plaintext header followed
by an encrypted body, which itself contains a type and optional padding.

%%% Record Layer

       struct {
           opaque content[TLSPlaintext.length];
           ContentType type;
           uint8 zeros[length_of_padding];
       } TLSInnerPlaintext;

       struct {
           ContentType opaque_type = 23; /* application_data */
           ProtocolVersion legacy_record_version = 0x0301; /* TLS v1.x */
           uint16 length;
           opaque encrypted_record[length];
       } TLSCiphertext;

content
: The byte encoding of a handshake or an alert message, or the raw bytes of
the application's data to send.

type
: The content type of the record.

zeros
: An arbitrary-length run of zero-valued bytes may
  appear in the cleartext after the type field.  This provides an
  opportunity for senders to pad any TLS record by a chosen amount as
  long as the total stays within record size limits.  See
  {{record-padding}} for more details.

opaque_type
: The outer opaque_type field of a TLSCiphertext record is always set to the
  value 23 (application_data) for outward compatibility with
  middleboxes accustomed to parsing previous versions of TLS.  The
  actual content type of the record is found in TLSInnerPlaintext.type after
  decryption.

legacy_record_version
: The legacy_record_version field is always 0x0301.  TLS 1.3 TLSCiphertexts
  are not generated until after TLS 1.3 has been negotiated, so there are
  no historical compatibility concerns where other values might be received.
  Implementations MAY verify that the legacy_record_version field is 0x0301
  and abort the connection if it is not.
  Note that the handshake protocol including the ClientHello and ServerHello messages authenticates
  the protocol version, so this value is redundant.

length
: The length (in bytes) of the following TLSCiphertext.encrypted_record, which
  is the sum of the lengths of the content and the padding, plus one
  for the inner content type, plus any expansion added by the AEAD algorithm.
  The length MUST NOT exceed 2^14 + 256 bytes.
  An endpoint that receives a record that exceeds this length MUST
  terminate the connection with a "record_overflow" alert.

encrypted_record
: The AEAD-encrypted form of the serialized TLSInnerPlaintext structure.
{:br }


AEAD algorithms take as input a single key, a nonce, a plaintext, and "additional
data" to be included in the authentication check, as described in Section 2.1
of {{RFC5116}}. The key is either the client_write_key or the server_write_key,
the nonce is derived from the sequence number (see {{nonce}}) and the
client_write_iv or server_write_iv, and the additional data input is empty
(zero length).  Derivation of traffic keys is defined in {{traffic-key-calculation}}.

The plaintext is the concatenation of TLSInnerPlaintext.fragment,
TLSInnerPlaintext.type, and any padding bytes (zeros).

The AEAD output consists of the ciphertext output from the AEAD
encryption operation. The length of the plaintext is greater than
TLSInnerPlaintext.length due to the inclusion of TLSInnerPlaintext.type and
any padding supplied by the sender.  The length of the
AEAD output will generally be larger than the plaintext, but by an
amount that varies with the AEAD algorithm. Since the ciphers might
incorporate padding, the amount of overhead could vary with different
lengths of plaintext. Symbolically,

       AEADEncrypted =
           AEAD-Encrypt(write_key, nonce, plaintext of fragment)

In order to decrypt and verify, the cipher takes as input the key,
nonce, and the AEADEncrypted value. The output is either the plaintext
or an error indicating that the decryption failed. There is no
separate integrity check. That is:

       plaintext of encrypted_record =
           AEAD-Decrypt(write_key, nonce, AEADEncrypted)

If the decryption fails, the receiver MUST terminate the connection
with a "bad_record_mac" alert.

An AEAD algorithm used in TLS 1.3 MUST NOT produce an expansion greater than
255 octets.  An endpoint that receives a record from its peer with
TLSCipherText.length larger than 2^14 + 256 octets MUST terminate
the connection with a "record_overflow" alert.  This limit is derived from the maximum
TLSPlaintext length of 2^14 octets + 1 octet for ContentType + the
maximum AEAD expansion of 255 octets.


## Per-Record Nonce {#nonce}

A 64-bit sequence number is maintained separately for reading and writing
records.  Each sequence number is set to zero at the beginning of a connection
and whenever the key is changed.

The sequence number is incremented by one after reading or writing each record.
The first record transmitted under a particular set of traffic keys
MUST use sequence number 0.

Because the size of sequence numbers is 64-bit, they should not
wrap. If a TLS implementation would need to
wrap a sequence number, it MUST either re-key ({{key-update}}) or
terminate the connection.

Each AEAD algorithm will specify a range of possible lengths for the
per-record nonce, from N_MIN bytes to N_MAX bytes of input ({{RFC5116}}).
The length of the TLS per-record nonce (iv_length) is set to the larger of
8 bytes and N_MIN for the AEAD algorithm (see {{RFC5116}} Section 4). An AEAD
algorithm where N_MAX is less than 8 bytes MUST NOT be used with TLS.
The per-record nonce for the AEAD construction is formed as follows:

  1. The 64-bit record sequence number is encoded in network byte order
     and padded to the left with zeros to iv_length.

  2. The padded sequence number is XORed with the static client_write_iv
     or server_write_iv, depending on the role.

The resulting quantity (of length iv_length) is used as the per-record
nonce.

Note: This is a different construction from that in TLS 1.2, which
specified a partially explicit nonce.


## Record Padding

All encrypted TLS records can be padded to inflate the size of the
TLSCipherText.  This allows the sender to hide the size of the
traffic from an observer.

When generating a TLSCiphertext record, implementations MAY choose to
pad.  An unpadded record is just a record with a padding length of
zero.  Padding is a string of zero-valued bytes appended
to the ContentType field before encryption.  Implementations MUST set
the padding octets to all zeros before encrypting.

Application Data records may contain a zero-length TLSInnerPlaintext.content if
the sender desires.  This permits generation of plausibly-sized cover
traffic in contexts where the presence or absence of activity may be
sensitive.  Implementations MUST NOT send Handshake or Alert records
that have a zero-length TLSInnerPlaintext.content; if such a message
is received, the receiving implementation MUST terminate the connection
with an "unexpected_message" alert.

The padding sent is automatically verified by the record protection
mechanism; upon successful decryption of a TLSCiphertext.encrypted_record,
the receiving implementation scans the field from the end toward the
beginning until it finds a non-zero octet. This non-zero octet is the
content type of the message.
This padding scheme was selected because it allows padding of any encrypted
TLS record by an arbitrary size (from zero up to TLS record size
limits) without introducing new content types.  The design also
enforces all-zero padding octets, which allows for quick detection of
padding errors.

Implementations MUST limit their scanning to the cleartext returned
from the AEAD decryption.  If a receiving implementation does not find
a non-zero octet in the cleartext, it MUST terminate the
connection with an "unexpected_message" alert.

The presence of padding does not change the overall record size limitations
- the full fragment plaintext MUST not exceed 2^14 octets. If the maximum
fragment length is reduced, such as by the max_fragment_length extension
from [RFC6066], then the reduced limit applies to the full plaintext,
including the padding.

Selecting a padding policy that suggests when and how much to pad is a
complex topic, and is beyond the scope of this specification. If the
application layer protocol atop TLS has its own padding, it may be
preferable to pad application_data TLS records within the application
layer.  Padding for encrypted handshake and alert TLS records must
still be handled at the TLS layer, though.  Later documents may define
padding selection algorithms, or define a padding policy request
mechanism through TLS extensions or some other means.

## Limits on Key Usage

There are cryptographic limits on the amount of plaintext which can be
safely encrypted under a given set of keys.  {{AEAD-LIMITS}} provides
an analysis of these limits under the assumption that the underlying
primitive (AES or ChaCha20) has no weaknesses. Implementations SHOULD
do a key update as described in {{key-update}} prior to reaching these limits.

For AES-GCM, up to 2^24.5 full-size records (about 24 million)
may be encrypted on a
given connection while keeping a safety margin of approximately
2^-57 for Authenticated Encryption (AE) security. For
ChaCha20/Poly1305, the record sequence number would wrap before the
safety limit is reached.

#  Alert Protocol

One of the content types supported by the TLS record layer is the
alert type.  Like other messages, alert messages are encrypted as
specified by the current connection state.

Alert messages convey a description of the alert and a legacy field
that conveyed the severity of the message in previous versions of
TLS.  In TLS 1.3, the severity is implicit in the type of alert
being sent, and can safely be ignored.
Some alerts are sent to
indicate orderly closure of the connection or the end of
early data (see {{closure-alerts}}).
Upon receiving such an alert, the TLS implementation SHOULD
indicate end-of-data to the application, and if appropriate for
the alert type, send a closure alert in response.

Error alerts indicate abortive closure of the
connection (see {{error-alerts}}). Upon receiving an error alert,
the TLS implementation SHOULD indicate an error to the application and
MUST NOT allow any further data to be sent or received on the
connection.  Servers and clients MUST forget keys and secrets
associated with a failed connection. Stateful implementations of
tickets (as in many clients) SHOULD discard tickets associated
with failed connections.

All the alerts listed in {{error-alerts}} MUST be sent as fatal and
MUST be treated as fatal regardless of the AlertLevel in the
message. Unknown alert types MUST be treated as fatal.

%%% Alert Messages

       enum { warning(1), fatal(2), (255) } AlertLevel;

       enum {
           close_notify(0),
           unexpected_message(10),
           bad_record_mac(20),
           decryption_failed_RESERVED(21),
           record_overflow(22),
           decompression_failure_RESERVED(30),
           handshake_failure(40),
           no_certificate_RESERVED(41),
           bad_certificate(42),
           unsupported_certificate(43),
           certificate_revoked(44),
           certificate_expired(45),
           certificate_unknown(46),
           illegal_parameter(47),
           unknown_ca(48),
           access_denied(49),
           decode_error(50),
           decrypt_error(51),
           export_restriction_RESERVED(60),
           protocol_version(70),
           insufficient_security(71),
           internal_error(80),
           inappropriate_fallback(86),
           user_canceled(90),
           no_renegotiation_RESERVED(100),
           missing_extension(109),
           unsupported_extension(110),
           certificate_unobtainable(111),
           unrecognized_name(112),
           bad_certificate_status_response(113),
           bad_certificate_hash_value(114),
           unknown_psk_identity(115),
           certificate_required(116),
           (255)
       } AlertDescription;

       struct {
           AlertLevel level;
           AlertDescription description;
       } Alert;

##  Closure Alerts

The client and the server must share knowledge that the connection is ending in
order to avoid a truncation attack.

close_notify
: This alert notifies the recipient that the sender will not send
  any more messages on this connection. Any data received after a
  closure MUST be ignored.

user_canceled
: This alert notifies the recipient that the sender is canceling the
  handshake for some reason unrelated to a protocol failure. If a user
  cancels an operation after the handshake is complete, just closing the
  connection by sending a "close_notify" is more appropriate. This alert
  SHOULD be followed by a "close_notify". This alert is generally a warning.
{:br }

Either party MAY initiate a close by sending a "close_notify" alert. Any data
received after a closure alert MUST be ignored. If a transport-level close is
received prior to a "close_notify", the receiver cannot know that all the
data that was sent has been received.

Each party MUST send a "close_notify" alert before closing the write side
of the connection, unless some other fatal alert has been transmitted. The
other party MUST respond with a "close_notify" alert of its own and close down
the connection immediately, discarding any pending writes. The initiator of the
close need not wait for the responding "close_notify" alert before closing the
read side of the connection.

If the application protocol using TLS provides that any data may be carried
over the underlying transport after the TLS connection is closed, the TLS
implementation MUST receive the responding "close_notify" alert before indicating
to the application layer that the TLS connection has ended. If the application
protocol will not transfer any additional data, but will only close the
underlying transport connection, then the implementation MAY choose to close
the transport without waiting for the responding "close_notify". No part of this
standard should be taken to dictate the manner in which a usage profile for TLS
manages its data transport, including when connections are opened or closed.

Note: It is assumed that closing a connection reliably delivers pending data
before destroying the transport.

##  Error Alerts

Error handling in the TLS Handshake Protocol is very simple. When an
error is detected, the detecting party sends a message to its
peer. Upon transmission or receipt of a fatal alert message, both
parties MUST immediately close the connection.

Whenever an implementation encounters a fatal error condition, it
SHOULD send an appropriate fatal alert and MUST close the connection
without sending or receiving any additional data. In the rest of this
specification, when the phrases "terminate the connection" and "abort the
handshake" are used without a specific alert it means that the
implementation SHOULD send the alert indicated by the descriptions
below. The phrases "terminate the connection with a X alert" and
"abort the handshake with a X alert" mean that the implementation
MUST send alert X if it sends any alert. All
alerts defined in this section below, as well as all unknown alerts,
are universally considered fatal as of TLS 1.3 (see
{{alert-protocol}}).

The following error alerts are defined:

unexpected_message
: An inappropriate message (e.g., the wrong handshake message, premature
  application data, etc.) was received. This alert should never be
  observed in communication between proper implementations.

bad_record_mac
: This alert is returned if a record is received which cannot be
  deprotected. Because AEAD algorithms combine decryption and
  verification, and also to avoid side channel attacks,
  this alert is used for all deprotection failures.
  This alert should never be observed in communication between
  proper implementations, except when messages were corrupted
  in the network.

record_overflow
: A TLSCiphertext record was received that had a length more than
  2^14 + 256 bytes, or a record decrypted to a TLSPlaintext record
  with more than 2^14 bytes.
  This alert should never be observed in communication between
  proper implementations, except when messages were corrupted
  in the network.

handshake_failure
: Reception of a "handshake_failure" alert message indicates that the
  sender was unable to negotiate an acceptable set of security
  parameters given the options available.

bad_certificate
: A certificate was corrupt, contained signatures that did not
  verify correctly, etc.

unsupported_certificate
: A certificate was of an unsupported type.

certificate_revoked
: A certificate was revoked by its signer.

certificate_expired
: A certificate has expired or is not currently valid.

certificate_unknown
: Some other (unspecified) issue arose in processing the
  certificate, rendering it unacceptable.

illegal_parameter
: A field in the handshake was incorrect or inconsistent with
  other fields. This alert is used for errors which conform to
  the formal protocol syntax but are otherwise incorrect.

unknown_ca
: A valid certificate chain or partial chain was received, but the
  certificate was not accepted because the CA certificate could not
  be located or could not be matched with a known trust anchor.

access_denied
: A valid certificate or PSK was received, but when access control was
  applied, the sender decided not to proceed with negotiation.

decode_error
: A message could not be decoded because some field was out of the
  specified range or the length of the message was incorrect.
  This alert is used for errors where the message does not conform
  to the formal protocol syntax.
  This alert should never be observed in communication between
  proper implementations, except when messages were corrupted
  in the network.

decrypt_error
: A handshake cryptographic operation failed, including being unable
  to correctly verify a signature or validate a Finished message
  or a PSK binder.

protocol_version
: The protocol version the peer has attempted to negotiate is
  recognized but not supported. (see {{backward-compatibility}})

insufficient_security
: Returned instead of "handshake_failure" when a negotiation has
  failed specifically because the server requires parameters more
  secure than those supported by the client.

internal_error
: An internal error unrelated to the peer or the correctness of the
  protocol (such as a memory allocation failure) makes it impossible
  to continue.

inappropriate_fallback
: Sent by a server in response to an invalid connection retry attempt
  from a client (see {{!RFC7507}}).

missing_extension
: Sent by endpoints that receive a hello message not containing an
  extension that is mandatory to send for the offered TLS version
  or other negotiated parameters.

unsupported_extension
: Sent by endpoints receiving any hello message containing an extension
  known to be prohibited for inclusion in the given hello message, including
  any extensions in a ServerHello or Certificate not first offered in the
  corresponding ClientHello.

certificate_unobtainable
: Sent by servers when unable to obtain a certificate from a URL
  provided by the client via the "client_certificate_url" extension
  (see {{RFC6066}}).

unrecognized_name
: Sent by servers when no server exists identified by the name
  provided by the client via the "server_name" extension
  (see {{RFC6066}}).

bad_certificate_status_response
: Sent by clients when an invalid or unacceptable OCSP response is
  provided by the server via the "status_request" extension
  (see {{RFC6066}}).

bad_certificate_hash_value
: Sent by servers when a retrieved object does not have the correct hash
  provided by the client via the "client_certificate_url" extension
  (see {{RFC6066}}).

unknown_psk_identity
: Sent by servers when PSK key establishment is desired but no
 acceptable PSK identity is provided by the client. Sending this alert
 is OPTIONAL; servers MAY instead choose to send a "decrypt_error"
 alert to merely indicate an invalid PSK identity.

certificate_required
: Sent by servers when a client certificate is desired but none was provided by
  the client.
{:br }

New Alert values are assigned by IANA as described in {{iana-considerations}}.

#  Cryptographic Computations

The TLS handshake establishes one or more input secrets which
are combined to create the actual working keying material, as detailed
below. The key derivation process incorporates both the input secrets
and the handshake transcript. Note that because the handshake
transcript includes the random values in the Hello messages,
any given handshake will have different traffic secrets, even
if the same input secrets are used, as is the case when
the same PSK is used for multiple connections

## Key Schedule

The key derivation process makes use of the HKDF-Extract and HKDF-Expand
functions as defined for HKDF {{RFC5869}}, as well as the functions
defined below:

~~~~
    HKDF-Expand-Label(Secret, Label, HashValue, Length) =
         HKDF-Expand(Secret, HkdfLabel, Length)

    Where HkdfLabel is specified as:

    struct {
        uint16 length = Length;
        opaque label<10..255> = "TLS 1.3, " + Label;
        opaque hash_value<0..255> = HashValue;
    } HkdfLabel;

    Derive-Secret(Secret, Label, Messages) =
         HKDF-Expand-Label(Secret, Label,
                           Transcript-Hash(Messages), Hash.length)
~~~~

The Hash function and the HKDF hash are the cipher suite hash algorithm.
Hash.length is its output length in bytes. Messages are the concatenation of the
indicated handshake messages, including the handshake message type
and length fields, but not including record layer headers. Note that
in some cases a zero-length HashValue (indicated by "") is passed to
HKDF-Expand-Label.

Given a set of n InputSecrets, the final "master secret" is computed
by iteratively invoking HKDF-Extract with InputSecret_1, InputSecret_2,
etc.  The initial secret is simply a string of Hash.length zero bytes.
Concretely, for the
present version of TLS 1.3, secrets are added in the following order:

- PSK (a pre-shared key established externally or a resumption_master_secret
  value from a previous connection)
- (EC)DHE shared secret ({{ecdhe-shared-secret-calculation}})

This produces a full key derivation schedule shown in the diagram below.
In this diagram, the following formatting conventions apply:

- HKDF-Extract is drawn as taking the Salt argument from the top and the IKM argument
  from the left.
- Derive-Secret's Secret argument is indicated by the incoming
  arrow. For instance, the Early Secret is the Secret for
  generating the client_early_traffic_secret.

~~~~
                 0
                 |
                 v
   PSK ->  HKDF-Extract = Early Secret
                 |
                 +-----> Derive-Secret(.,
                 |                     "external psk binder key" |
                 |                     "resumption psk binder key",
                 |                     "")
                 |                     = binder_key
                 |
                 +-----> Derive-Secret(., "client early traffic secret",
                 |                     ClientHello)
                 |                     = client_early_traffic_secret
                 |
                 +-----> Derive-Secret(., "early exporter master secret",
                 |                     ClientHello)
                 |                     = early_exporter_secret
                 v
           Derive-Secret(., "derived secret", "")
                 |
                 v
(EC)DHE -> HKDF-Extract = Handshake Secret
                 |
                 +-----> Derive-Secret(., "client handshake traffic secret",
                 |                     ClientHello...ServerHello)
                 |                     = client_handshake_traffic_secret
                 |
                 +-----> Derive-Secret(., "server handshake traffic secret",
                 |                     ClientHello...ServerHello)
                 |                     = server_handshake_traffic_secret
                 v
           Derive-Secret(., "derived secret", "")
                 |
                 v
      0 -> HKDF-Extract = Master Secret
                 |
                 +-----> Derive-Secret(., "client application traffic secret",
                 |                     ClientHello...Server Finished)
                 |                     = client_traffic_secret_0
                 |
                 +-----> Derive-Secret(., "server application traffic secret",
                 |                     ClientHello...Server Finished)
                 |                     = server_traffic_secret_0
                 |
                 +-----> Derive-Secret(., "exporter master secret",
                 |                     ClientHello...Server Finished)
                 |                     = exporter_secret
                 |
                 +-----> Derive-Secret(., "resumption master secret",
                                       ClientHello...Client Finished)
                                       = resumption_master_secret
~~~~

The general pattern here is that the secrets shown down the left side
of the diagram are just raw entropy without context, whereas the
secrets down the right side include handshake context and therefore
can be used to derive working keys without additional context.
Note that the different
calls to Derive-Secret may take different Messages arguments,
even with the same secret. In a 0-RTT exchange, Derive-Secret is
called with four distinct transcripts; in a 1-RTT-only exchange
with three distinct transcripts.

If a given secret is not available, then the 0-value consisting of
a string of Hash.length zero bytes is used.  Note that this does not mean skipping
rounds, so if PSK is not in use Early Secret will still be
HKDF-Extract(0, 0). For the computation of the binder_secret, the label is "external
psk binder key" for external PSKs (those provisioned outside of TLS)
and "resumption psk binder key" for
resumption PSKs (those provisioned as the resumption master secret of
a previous handshake). The different labels prevent the substitution of one
type of PSK for the other.

There are multiple potential Early Secret values depending on
which PSK the server ultimately selects. The client will need to compute
one for each potential PSK; if no PSK is selected, it will then need to
compute the early secret corresponding to the zero PSK.



## Updating Traffic Keys and IVs {#updating-traffic-keys}

Once the handshake is complete, it is possible for either side to
update its sending traffic keys using the KeyUpdate handshake message
defined in {{key-update}}.  The next generation of traffic keys is computed by
generating client_/server_traffic_secret_N+1 from
client_/server_traffic_secret_N as described in
this section then re-deriving the traffic keys as described in
{{traffic-key-calculation}}.

The next-generation traffic_secret is computed as:

~~~~
    traffic_secret_N+1 = HKDF-Expand-Label(
                             traffic_secret_N,
                             "application traffic secret", "", Hash.length)
~~~~

Once client/server_traffic_secret_N+1 and its associated traffic keys have been computed,
implementations SHOULD delete client_/server_traffic_secret_N and its associated traffic
keys.

## Traffic Key Calculation

The traffic keying material is generated from the following input values:

* A secret value
* A purpose value indicating the specific value being generated
* The length of the key

The traffic keying material is generated from an input traffic secret value using:

~~~~
    [sender]_write_key = HKDF-Expand-Label(Secret, "key", "", key_length)
    [sender]_write_iv = HKDF-Expand-Label(Secret, "iv", "", iv_length)
~~~~

\[sender] denotes the sending side. The Secret value for each record type
is shown in the table below.

| Record Type | Secret |
|:------------|--------|
| 0-RTT Application | client_early_traffic_secret |
| Handshake         | \[sender]_handshake_traffic_secret |
| Application Data  | \[sender]_traffic_secret_N |

All the traffic keying material is recomputed whenever the
underlying Secret changes (e.g., when changing from the handshake to
application data keys or upon a key update).

## (EC)DHE Shared Secret Calculation {#ecdhe-shared-secret-calculation}

###  Finite Field Diffie-Hellman

For finite field groups, a conventional Diffie-Hellman computation is performed.
The negotiated key (Z) is converted to a byte string by encoding in big-endian and
padded with zeros up to the size of the prime. This byte string is used as the
shared secret, and is used in the key schedule as specified above.

Note that this construction differs from previous versions of TLS which remove
leading zeros.

### Elliptic Curve Diffie-Hellman

For secp256r1, secp384r1 and secp521r1, ECDH calculations (including parameter
and key generation as well as the shared secret calculation) are
performed according to {{IEEE1363}} using the ECKAS-DH1 scheme with the identity
map as key derivation function (KDF), so that the shared secret is the
x-coordinate of the ECDH shared secret elliptic curve point represented
as an octet string.  Note that this octet string (Z in IEEE 1363 terminology)
as output by FE2OSP, the Field Element to Octet String Conversion
Primitive, has constant length for any given field; leading zeros
found in this octet string MUST NOT be truncated.

(Note that this use of the identity KDF is a technicality.  The
complete picture is that ECDH is employed with a non-trivial KDF
because TLS does not directly use this secret for anything
other than for computing other secrets.)

ECDH functions are used as follows:

* The public key to put into the KeyShareEntry.key_exchange structure is the
  result of applying the ECDH function to the secret key of appropriate length
  (into scalar input) and the standard public basepoint (into u-coordinate point
  input).
* The ECDH shared secret is the result of applying the ECDH function to the
  secret key (into scalar input) and the peer's public key (into u-coordinate
  point input). The output is used raw, with no processing.

For X25519 and X448, implementations SHOULD use the approach specified
in {{RFC7748}} to calculate the Diffie-Hellman shared
secret. Implementations MUST check whether the computed Diffie-Hellman
shared secret is the all-zero value and abort if so, as described in
Section 6 of {{RFC7748}}. If implementers use an alternative
implementation of these elliptic curves, they SHOULD perform the
additional checks specified in Section 7 of {{RFC7748}}.

## Exporters

{{!RFC5705}} defines keying material exporters for TLS in terms of the TLS
pseudorandom function (PRF). This document replaces the PRF with HKDF, thus
requiring a new construction. The exporter interface remains the same.

The exporter value is computed as:

    HKDF-Expand-Label(Derive-Secret(Secret, label, ""),
                      "exporter", Hash(context_value), key_length)

Where Secret is either the early_exporter_secret or the exporter_secret.
Implementations MUST use the exporter_secret unless explicitly specified by the
application.  A separate interface for the early exporter is RECOMMENDED,
especially on a server where a single interface can make the early exporter
inaccessible.

If no context is provided, the context_value is zero-length. Consequently,
providing no context computes the same value as providing an empty context. This
is a change from previous versions of TLS where an empty context produced a
different output to an absent context. As of this document's publication, no
allocated exporter label is used both with and without a context. Future
specifications MUST NOT define a use of exporters that permit both an empty
context and no context with the same label. New uses of exporters SHOULD provide
a context in all exporter computations, though the value could be empty.

Requirements for the format of exporter labels are defined in section 4
of {{RFC5705}}.

#  Compliance Requirements

##  Mandatory-to-Implement Cipher Suites

In the absence of an application profile standard specifying otherwise, a
TLS-compliant application MUST implement the TLS_AES_128_GCM_SHA256
cipher suite and SHOULD implement the TLS_AES_256_GCM_SHA384 and
TLS_CHACHA20_POLY1305_SHA256 cipher suites. (see {{cipher-suites}})

A TLS-compliant application MUST support digital signatures with
rsa_pkcs1_sha256 (for certificates), rsa_pss_sha256 (for
CertificateVerify and certificates), and ecdsa_secp256r1_sha256. A
TLS-compliant application MUST support key exchange with secp256r1
(NIST P-256) and SHOULD support key exchange with X25519 {{RFC7748}}.

##  Mandatory-to-Implement Extensions {#mti-extensions}

In the absence of an application profile standard specifying otherwise, a
TLS-compliant application MUST implement the following TLS extensions:

  * Supported Versions ("supported_versions"; {{supported-versions}})
  * Cookie ("cookie"; {{cookie}})
  * Signature Algorithms ("signature_algorithms"; {{signature-algorithms}})
  * Negotiated Groups ("supported_groups"; {{negotiated-groups}})
  * Key Share ("key_share"; {{key-share}})
  * Server Name Indication ("server_name"; Section 3 of {{RFC6066}})

All implementations MUST send and use these extensions when offering
applicable features:

  * "supported_versions" is REQUIRED for all ClientHello messages.
  * "signature_algorithms" is REQUIRED for certificate authentication.
  * "supported_groups" and "key_share" are REQUIRED for DHE or ECDHE key exchange.
  * "pre_shared_key" is REQUIRED for PSK key agreement.

A client is considered to be attempting to negotiate using this
specification if the ClientHello contains a "supported_versions"
extension with a version indicating TLS 1.3. Such a ClientHello message
MUST meet the following requirements:

 * If not containing a "pre_shared_key" extension, it MUST contain both
   a "signature_algorithms" extension and a "supported_groups" extension.
 * If containing a "supported_groups" extension, it MUST also contain a
   "key_share" extension, and vice versa. An empty KeyShare.client_shares
   vector is permitted.

Servers receiving a ClientHello which does not conform to these
requirements MUST abort the handshake with a "missing_extension"
alert.

Additionally, all implementations MUST support use of the "server_name"
extension with applications capable of using it.
Servers MAY require clients to send a valid "server_name" extension.
Servers requiring this extension SHOULD respond to a ClientHello
lacking a "server_name" extension by terminating the connection with a
"missing_extension" alert.


#  Security Considerations

Security issues are discussed throughout this memo, especially in
{{implementation-notes}}, {{backward-compatibility}}, and {{security-analysis}}.


#  IANA Considerations

This document uses several registries that were originally created in
{{RFC4346}}. IANA has updated these to reference this document. The registries
and their allocation policies are below:

- TLS Cipher Suite Registry: Values with the first byte in the range
  0-254 (decimal) are assigned via Specification Required {{RFC5226}}.
  Values with the first byte 255 (decimal) are reserved for Private
  Use {{RFC5226}}.

  IANA \[SHALL add/has added] the cipher suites listed in {{cipher-suites}} to
  the registry. The "Value" and "Description" columns are taken from the table.
  The "DTLS-OK" and "Recommended" columns are both marked as "Yes" for each new
  cipher suite. \[\[This assumes {{?I-D.ietf-tls-iana-registry-updates}} has been
  applied.]]

-  TLS ContentType Registry: Future values are allocated via
  Standards Action {{RFC5226}}.

-  TLS Alert Registry: Future values are allocated via Standards
  Action {{RFC5226}}. IANA \[SHALL update/has updated] this registry
  to include values for "missing_extension" and "certificate_required".

-  TLS HandshakeType Registry: Future values are allocated via
  Standards Action {{RFC5226}}. IANA \[SHALL update/has updated] this registry
  to rename item 4 from "NewSessionTicket" to "new_session_ticket"
  and to add the "hello_retry_request", "encrypted_extensions",
  "end_of_early_data", "key_update", and "handshake_hash" values.

This document also uses a registry originally created in {{RFC4366}}. IANA has
updated it to reference this document. The registry and its allocation policy
is listed below:

-  IANA \[SHALL update/has updated] this registry to include the
   "key_share", "pre_shared_key", "psk_key_exchange_modes",
   "early_data", "cookie", "supported_versions",
   "certificate_authorities", and "oid_filters" extensions with the
   values defined in this document and the Recommended value of "Yes".

-  IANA \[SHALL update/has updated] this registry to include a "TLS
   1.3" column which lists the messages in which the extension may
   appear. This column \[SHALL be/has been]
   initially populated from the table in {{extensions}}
   with any extension not listed there marked as "-" to indicate that
   it is not used by TLS 1.3.

In addition, this document defines a new registry to be maintained
by IANA:

-  TLS SignatureScheme Registry: Values with the first byte in the range
  0-254 (decimal) are assigned via Specification Required {{RFC5226}}.
  Values with the first byte 255 (decimal) are reserved for Private
  Use {{RFC5226}}. Values with the first byte in the range 0-6 or with the
  second byte in the range 0-3 that are not currently allocated are reserved for
  backwards compatibility.
  This registry SHALL have a "Recommended" column.
  The registry \[shall be/ has been] initially populated with the values described in
  {{signature-algorithms}}. The following values SHALL be marked as
  "Recommended": ecdsa_secp256r1_sha256, ecdsa_secp384r1_sha384,
  rsa_pss_sha256, rsa_pss_sha384, rsa_pss_sha512, ed25519.

Finally, this document obsoletes the TLS HashAlgorithm Registry and the TLS
SignatureAlgorithm Registry, both originally created in {{RFC5246}}.  IANA
\[SHALL update/has updated] the TLS HashAlgorithm Registry to list values 7-223 as
"Reserved" and the TLS SignatureAlgorithm Registry to list values 4-223 as
"Reserved".

--- back

# State Machine

This section provides a summary of the legal state transitions for the
client and server handshakes.  State names (in all capitals, e.g.,
START) have no formal meaning but are provided for ease of
comprehension.  Messages which are sent only sometimes are indicated
in [].

## Client

~~~~
                           START <----+
            Send ClientHello |        | Recv HelloRetryRequest
         /                   v        |
        |                  WAIT_SH ---+
    Can |                    | Recv ServerHello
   send |                    V
  early |                 WAIT_EE
   data |                    | Recv EncryptedExtensions
        |           +--------+--------+
        |     Using |                 | Using certificate
        |       PSK |                 v
        |           |            WAIT_CERT_CR
        |           |        Recv |       | Recv CertificateRequest
        |           | Certificate |       v
        |           |             |    WAIT_CERT
        |           |             |       | Recv Certificate
        |           |             v       v
        |           |              WAIT_CV
        |           |                 | Recv CertificateVerify
        |           +> WAIT_FINISHED <+
        |                  | Recv Finished
        \                  |
                           | [Send EndOfEarlyData]
                           | [Send Certificate [+ CertificateVerify]]
                           | Send Finished
 Can send                  v
 app data -->          CONNECTED
 after
 here
~~~~

## Server

~~~~
                             START <-----+
              Recv ClientHello |         | Send HelloRetryRequest
                               v         |
                            RECVD_CH ----+
                               | Select parameters
                               v
                            NEGOTIATED
                               | Send ServerHello
                               | Send EncryptedExtensions
                               | [Send CertificateRequest]
Can send                       | [Send Certificate + CertificateVerify]
app data -->                   | Send Finished
after                 +--------+--------+
here         No 0-RTT |                 | 0-RTT
                      |                 v
                      |             WAIT_EOED <---+
                      |            Recv |   |     | Recv
                      |  EndOfEarlyData |   |     | early data
                      |                 |   +-----+
                      +> WAIT_FLIGHT2 <-+
                               |
                      +--------+--------+
              No auth |                 | Client auth
                      |                 |
                      |                 v
                      |             WAIT_CERT
                      |        Recv |       | Recv Certificate
                      |       empty |       v
                      | Certificate |    WAIT_CV
                      |             |       | Recv
                      |             v       | CertificateVerify
                      +-> WAIT_FINISHED <---+
                               | Recv Finished
                               v
                           CONNECTED
~~~~

# Protocol Data Structures and Constant Values

This section describes protocol types and constants. Values listed as
_RESERVED were used in previous versions of TLS and are listed here
for completeness. TLS 1.3 implementations MUST NOT send them but
might receive them from older TLS implementations.

%%## Record Layer
%%## Alert Messages
%%## Handshake Protocol
%%### Key Exchange Messages
%%#### Version Extension
%%#### Cookie Extension
%%#### Signature Algorithm Extension
%%#### Supported Groups Extension

Values within "obsolete_RESERVED" ranges were used in previous versions
of TLS and MUST NOT be offered or negotiated by TLS 1.3 implementations.
The obsolete curves have various known/theoretical weaknesses or have
had very little usage, in some cases only due to unintentional
server configuration issues. They are no longer considered appropriate
for general use and should be assumed to be potentially unsafe. The set
of curves specified here is sufficient for interoperability with all
currently deployed and properly configured TLS implementations.

%%### Server Parameters Messages
%%### Authentication Messages
%%### Ticket Establishment
%%### Updating Keys


## Cipher Suites

A symmetric cipher suite defines the pair of the AEAD algorithm and hash
algorithm to be used with HKDF.
Cipher suite names follow the naming convention:

~~~
   CipherSuite TLS_AEAD_HASH = VALUE;
~~~

| Component | Contents |
|:----------|:---------|
| TLS       | The string "TLS" |
| AEAD      | The AEAD algorithm used for record protection |
| HASH      | The hash algorithm used with HKDF |
| VALUE     | The two byte ID assigned for this cipher suite |

This specification defines the following cipher suites for use with TLS 1.3.

|          Description            |    Value    |
|:--------------------------------|:------------|
| TLS_AES_128_GCM_SHA256          | {0x13,0x01} |
| TLS_AES_256_GCM_SHA384          | {0x13,0x02} |
| TLS_CHACHA20_POLY1305_SHA256    | {0x13,0x03} |
| TLS_AES_128_CCM_SHA256          | {0x13,0x04} |
| TLS_AES_128_CCM_8_SHA256        | {0x13,0x05} |

The corresponding AEAD algorithms AEAD_AES_128_GCM, AEAD_AES_256_GCM, and
AEAD_AES_128_CCM are defined in {{RFC5116}}. AEAD_CHACHA20_POLY1305 is defined
in {{RFC7539}}. AEAD_AES_128_CCM_8 is defined in {{RFC6655}}. The corresponding
hash algorithms are defined in {{SHS}}.

Although TLS 1.3 uses the same cipher suite space as previous versions
of TLS, TLS 1.3 cipher suites are defined differently, only specifying
the symmetric ciphers, and cannot be used for TLS 1.2. Similarly,
TLS 1.2 and lower cipher suites cannot be used with TLS 1.3.

New cipher suite values are assigned by IANA as described in
{{iana-considerations}}.


# Implementation Notes

The TLS protocol cannot prevent many common security mistakes. This section
provides several recommendations to assist implementors.
{{?I-D.ietf-tls-tls13-vectors}} provides test vectors for TLS 1.3 handshakes.

## API considerations for 0-RTT

0-RTT data has very different security properties from data
transmitted after a completed handshake: it can be
replayed. Implementations SHOULD provide different functions for
reading and writing 0-RTT data and data transmitted after the
handshake, and SHOULD NOT automatically resend 0-RTT data if it is
rejected by the server.

## Random Number Generation and Seeding

TLS requires a cryptographically secure pseudorandom number generator (PRNG).
In most cases, the operating system provides an appropriate facility such
as /dev/urandom, which should be used absent other (performance) concerns.
It is generally preferable to use an existing PRNG implementation in
preference to crafting a new one, and many adequate cryptographic libraries
are already available under favorable license terms.  Should those prove
unsatisfactory, {{RFC4086}} provides guidance on the generation of random values.


## Certificates and Authentication

Implementations are responsible for verifying the integrity of certificates and
should generally support certificate revocation messages. Certificates should
always be verified to ensure proper signing by a trusted Certificate Authority
(CA). The selection and addition of trust anchors should be done very carefully.
Users should be able to view information about the certificate and trust anchor.
Applications SHOULD also enforce minimum and maximum key sizes. For example,
certification paths containing keys or signatures weaker than 2048-bit RSA or
224-bit ECDSA are not appropriate for secure applications.


## Implementation Pitfalls

Implementation experience has shown that certain parts of earlier TLS
specifications are not easy to understand, and have been a source of
interoperability and security problems. Many of these areas have been clarified
in this document, but this appendix contains a short list of the most important
things that require special attention from implementors.

TLS protocol issues:

-  Do you correctly handle handshake messages that are fragmented to
  multiple TLS records (see {{record-layer}})? Including corner cases
  like a ClientHello that is split to several small fragments? Do
  you fragment handshake messages that exceed the maximum fragment
  size? In particular, the Certificate and CertificateRequest
  handshake messages can be large enough to require fragmentation.

-  Do you ignore the TLS record layer version number in all unencrypted TLS
  records? (see {{backward-compatibility}})

-  Have you ensured that all support for SSL, RC4, EXPORT ciphers, and
  MD5 (via the "signature_algorithms" extension) is completely removed from
  all possible configurations that support TLS 1.3 or later, and that
  attempts to use these obsolete capabilities fail correctly?
  (see {{backward-compatibility}})

-  Do you handle TLS extensions in ClientHello correctly, including
  unknown extensions?

-  When the server has requested a client certificate, but no
  suitable certificate is available, do you correctly send an empty
  Certificate message, instead of omitting the whole message (see
  {{client-certificate-selection}})?

- When processing the plaintext fragment produced by AEAD-Decrypt and
  scanning from the end for the ContentType, do you avoid scanning
  past the start of the cleartext in the event that the peer has sent
  a malformed plaintext of all-zeros?

- Do you properly ignore unrecognized cipher suites ({{client-hello}}),
  hello extensions ({{extensions}}), named groups ({{negotiated-groups}}),
  and signature algorithms ({{signature-algorithms}})?

- As a server, do you send a HelloRetryRequest to clients which
  support a compatible (EC)DHE group but do not predict it in the
  "key_share" extension? As a client, do you correctly handle a
  HelloRetryRequest from the server?

Cryptographic details:

-  What countermeasures do you use to prevent timing attacks {{TIMING}}?

-  When using Diffie-Hellman key exchange, do you correctly preserve
  leading zero bytes in the negotiated key (see {{finite-field-diffie-hellman}})?

-  Does your TLS client check that the Diffie-Hellman parameters sent
  by the server are acceptable, (see {{ffdhe-param}})?

- Do you use a strong and, most importantly, properly seeded random number
  generator (see {{random-number-generation-and-seeding}}) when generating Diffie-Hellman
  private values, the ECDSA "k" parameter, and other security-critical values?
  It is RECOMMENDED that implementations implement "deterministic ECDSA"
  as specified in {{!RFC6979}}.

- Do you zero-pad Diffie-Hellman public key values to the group size (see
  {{ffdhe-param}})?

- Do you verify signatures after making them to protect against RSA-CRT
  key leaks? {{FW15}}


## Client Tracking Prevention

Clients SHOULD NOT reuse a ticket for multiple connections. Reuse
of a ticket allows passive observers to correlate different connections.
Servers that issue tickets SHOULD offer at least as many tickets
as the number of connections that a client might use; for example, a web browser
using HTTP/1.1 {{RFC7230}} might open six connections to a server. Servers SHOULD
issue new tickets with every connection. This ensures that clients are
always able to use a new ticket when creating a new connection.


## Unauthenticated Operation

Previous versions of TLS offered explicitly unauthenticated cipher suites based
on anonymous Diffie-Hellman. These modes have been deprecated in TLS 1.3.
However, it is still possible to negotiate parameters that do not provide
verifiable server authentication by several methods, including:

- Raw public keys {{RFC7250}}.
- Using a public key contained in a certificate but without
  validation of the certificate chain or any of its contents.

Either technique used alone is vulnerable to man-in-the-middle attacks
and therefore unsafe for general use. However, it is also possible to
bind such connections to an external authentication mechanism via
out-of-band validation of the server's public key, trust on first
use, or channel bindings {{RFC5929}}. \[\[NOTE: TLS 1.3 needs a new
channel binding definition that has not yet been defined.]]
If no such mechanism is used, then the connection has no protection
against active man-in-the-middle attack; applications MUST NOT use TLS
in such a way absent explicit configuration or a specific application
profile.


# Backward Compatibility

The TLS protocol provides a built-in mechanism for version negotiation between
endpoints potentially supporting different versions of TLS.

TLS 1.x and SSL 3.0 use compatible ClientHello messages. Servers can also handle
clients trying to use future versions of TLS as long as the ClientHello format
remains compatible and the client supports the highest protocol version available
in the server.

Prior versions of TLS used the record layer version number for various
purposes. (TLSPlaintext.legacy_record_version and TLSCiphertext.legacy_record_version)
As of TLS 1.3, this field is deprecated. The value of
TLSPlaintext.legacy_record_version MUST be ignored by all
implementations. The value of TLSCiphertext.legacy_record_version MAY be ignored,
or MAY be validated to match the fixed constant value.
Version negotiation is performed using only the handshake versions.
(ClientHello.legacy_version,
ClientHello "supported_versions" extension, and ServerHello.version)
In order to maximize interoperability with older endpoints, implementations
that negotiate the use of TLS 1.0-1.2 SHOULD set the record layer
version number to the negotiated version for the ServerHello and all
records thereafter.

For maximum compatibility with previously non-standard behavior and misconfigured
deployments, all implementations SHOULD support validation of certification paths
based on the expectations in this document, even when handling prior TLS versions'
handshakes. (see {{server-certificate-selection}})

TLS 1.2 and prior supported an "Extended Master Secret" {{RFC7627}} extension
which digested large parts of the handshake transcript into the master secret.
Because TLS 1.3 always hashes in the transcript up to the server CertificateVerify,
implementations which support both TLS 1.3 and earlier versions SHOULD
indicate the use of the Extended Master Secret extension in their APIs
whenever TLS 1.3 is used.

## Negotiating with an older server

A TLS 1.3 client who wishes to negotiate with servers that do not
support TLS 1.3 will send a
normal TLS 1.3 ClientHello containing 0x0303 (TLS 1.2) in
ClientHello.legacy_version but with the correct version in the
"supported_versions" extension. If the server does not support TLS 1.3 it
will respond with a ServerHello containing an older version number. If the
client agrees to use this version, the negotiation will proceed as appropriate
for the negotiated protocol. A client using a ticket for resumption SHOULD initiate the
connection using the version that was previously negotiated.

Note that 0-RTT data is not compatible with older servers and SHOULD NOT
be sent absent knowledge that the server supports TLS 1.3.
See {{zero-rtt-backwards-compatibility}}.

If the version chosen by the server is not supported by the client (or not
acceptable), the client MUST abort the handshake with a "protocol_version" alert.

Some legacy server implementations are known to not implement the TLS
specification properly and might abort connections upon encountering
TLS extensions or versions which they are not aware of. Interoperability
with buggy servers is a complex topic beyond the scope of this document.
Multiple connection attempts may be required in order to negotiate
a backwards compatible connection; however, this practice is vulnerable
to downgrade attacks and is NOT RECOMMENDED.


## Negotiating with an older client

A TLS server can also receive a ClientHello indicating a version number smaller
than its highest supported version. If the "supported_versions" extension
is present, the server MUST negotiate using that extension as described in
{{supported-versions}}. If the "supported_versions" extension is not
present, the server MUST negotiate the minimum of ClientHello.legacy_version
and TLS 1.2. For example, if
the server supports TLS 1.0, 1.1, and 1.2, and legacy_version is TLS 1.0, the
server will proceed with a TLS 1.0 ServerHello. If the server only supports
versions greater than ClientHello.legacy_version, it MUST abort the handshake
with a "protocol_version" alert.

Note that earlier versions of TLS did not clearly specify the record layer
version number value in all cases (TLSPlaintext.legacy_record_version). Servers
will receive various TLS 1.x versions in this field, but its value
MUST always be ignored.


## Zero-RTT backwards compatibility

0-RTT data is not compatible with older servers. An older server will respond
to the ClientHello with an older ServerHello, but it will not correctly skip
the 0-RTT data and will fail to complete the handshake. This can cause issues when
a client attempts to use 0-RTT, particularly against multi-server deployments. For
example, a deployment could deploy TLS 1.3 gradually with some servers
implementing TLS 1.3 and some implementing TLS 1.2, or a TLS 1.3 deployment
could be downgraded to TLS 1.2.

A client that attempts to send 0-RTT data MUST fail a connection if it receives
a ServerHello with TLS 1.2 or older.  A client that attempts to repair this
error SHOULD NOT send a TLS 1.2 ClientHello, but instead send a TLS 1.3
ClientHello without 0-RTT data.

To avoid this error condition, multi-server deployments SHOULD ensure a uniform
and stable deployment of TLS 1.3 without 0-RTT prior to enabling 0-RTT.

## Backwards Compatibility Security Restrictions

Implementations negotiating use of older versions of TLS SHOULD prefer
forward secure and AEAD cipher suites, when available.

The security of RC4 cipher suites is considered insufficient for the reasons
cited in {{RFC7465}}. Implementations MUST NOT offer or negotiate RC4 cipher suites
for any version of TLS for any reason.

Old versions of TLS permitted the use of very low strength ciphers.
Ciphers with a strength less than 112 bits MUST NOT be offered or
negotiated for any version of TLS for any reason.

The security of SSL 3.0 {{SSL3}} is considered insufficient for the reasons enumerated
in {{RFC7568}}, and MUST NOT be negotiated for any reason.

The security of SSL 2.0 {{SSL2}} is considered insufficient for the reasons enumerated
in {{RFC6176}}, and MUST NOT be negotiated for any reason.

Implementations MUST NOT send an SSL version 2.0 compatible CLIENT-HELLO.
Implementations MUST NOT negotiate TLS 1.3 or later using an SSL version 2.0 compatible
CLIENT-HELLO. Implementations are NOT RECOMMENDED to accept an SSL version 2.0 compatible
CLIENT-HELLO in order to negotiate older versions of TLS.

Implementations MUST NOT send a ClientHello.legacy_version or ServerHello.version
set to 0x0300 or less. Any endpoint receiving a Hello message with
ClientHello.legacy_version or ServerHello.version set to 0x0300 MUST
abort the handshake with a "protocol_version" alert.

Implementations MUST NOT send any records with a version less than 0x0300.
Implementations SHOULD NOT accept any records with a version less than 0x0300
(but may inadvertently do so if the record version number is ignored completely).

Implementations MUST NOT use the Truncated HMAC extension, defined in
Section 7 of [RFC6066], as it is not applicable to AEAD algorithms and has
been shown to be insecure in some scenarios.


#  Overview of Security Properties {#security-analysis}

A complete security analysis of TLS is outside the scope of this document.
In this section, we provide an informal description the desired properties
as well as references to more detailed work in the research literature
which provides more formal definitions.

We cover properties of the handshake separately from those of the record layer.

## Handshake {#security-handshake}

The TLS handshake is an Authenticated Key Exchange (AKE) protocol which
is intended to provide both one-way authenticated (server-only) and
mutually authenticated (client and server) functionality. At the completion
of the handshake, each side outputs its view of the following values:

- A set of "session keys" (the various secrets derived from the master secret)
  from which can be derived a set of working keys.
- A set of cryptographic parameters (algorithms, etc.)
- The identities of the communicating parties.

We assume that the attacker has complete control of the network in
between the parties {{RFC3552}}. Even under these conditions, the
handshake should provide the properties listed below. Note that
these properties are not necessarily independent, but reflect
the protocol consumers' needs.

Establishing the same session keys.
: The handshake needs to output the same set of session keys on both sides of
the handshake, provided that it completes successfully on each endpoint
(See {{CK01}}; defn 1, part 1).

Secrecy of the session keys.
: The shared session keys should be known only to the communicating
parties, not to the attacker (See {{CK01}}; defn 1, part 2).  Note that
in a unilaterally authenticated connection, the attacker can establish
its own session keys with the server, but those session keys are
distinct from those established by the client.

Peer Authentication.
: The client's view of the peer identity should reflect the server's
identity. If the client is authenticated, the server's view of the
peer identity should match the client's identity.

Uniqueness of the session keys:
: Any two distinct handshakes should produce distinct, unrelated session
keys. Individual session keys produced by a handshake should also be distinct
and unrelated.

Downgrade protection.
: The cryptographic parameters should be the same on both sides and
should be the same as if the peers had been communicating in the
absence of an attack (See {{BBFKZG16}}; defns 8 and 9}).

Forward secret with respect to long-term keys
: If the long-term keying material (in this case the signature keys in certificate-based
authentication modes or the external/resumption PSK in PSK with (EC)DHE modes) are compromised after
the handshake is complete, this does not compromise the security of the
session key (See {{DOW92}}).  The forward secrecy property is not satisfied
when PSK is used in the "psk_ke" PskKeyExchangeMode.

Key Compromise Impersonation (KCI) resistance
: In a mutually-authenticated connection with certificates, peer authentication
should hold even if the local long-term secret was compromised before the
connection was established (see {{HGFS15}}). For example, if a client's
signature key is compromised, it should not be possible to impersonate
arbitrary servers to that client in subsequent handshakes.

Protection of endpoint identities.
: The server's identity (certificate) should be protected against passive
attackers. The client's identity should be protected against both passive
and active attackers.
{:br}

Informally, the signature-based modes of TLS 1.3 provide for the
establishment of a unique, secret, shared, key established by an
(EC)DHE key exchange and authenticated by the server's signature over
the handshake transcript, as well as tied to the server's identity by
a MAC. If the client is authenticated by a certificate, it also signs
over the handshake transcript and provides a MAC tied to both
identities. {{SIGMA}} describes the analysis of this type of key
exchange protocol. If fresh (EC)DHE keys are used for each connection,
then the output keys are forward secret.

The external PSK and resumption PSK bootstrap from a long-term shared
secret into a unique per-connection set of short-term session keys. This
secret may have been established in a previous handshake. If
PSK with (EC)DHE key establishment is used, these session keys will also be forward
secret. The resumption PSK has been designed so that the
resumption master secret computed by connection N and needed to form
connection N+1 is separate from the traffic keys used by connection N,
thus providing forward secrecy between the connections.

The PSK binder value forms a binding between a PSK
and the current handshake, as well as between the session where the
PSK was established and the session where it was used. This binding
transitively includes the original handshake transcript, because that
transcript is digested into the values which produce the Resumption
Master Secret. This requires that both the KDF used to produce the
resumption master secret and the MAC used to compute the binder be collision
resistant. These are properties of HKDF and HMAC respectively when
used with collision resistant hash functions and producing output of
at least 256 bits.  Any future replacement of these functions MUST
also provide collision resistance.
Note: The binder does not cover the binder values from other
PSKs, though they are included in the Finished MAC.

If an exporter is used, then it produces values which are unique
and secret (because they are generated from a unique session key).
Exporters computed with different labels and contexts are computationally
independent, so it is not feasible to compute one from another or
the session secret from the exported value. Note: exporters can
produce arbitrary-length values. If exporters are to be
used as channel bindings, the exported value MUST be large
enough to provide collision resistance. The exporters provided in
TLS 1.3 are derived from the same handshake contexts as the
early traffic keys and the application traffic keys respectively,
and thus have similar security properties. Note that they do
not include the client's certificate; future applications
which wish to bind to the client's certificate may need
to define a new exporter that includes the full handshake
transcript.

For all handshake modes, the Finished MAC (and where present, the
signature), prevents downgrade attacks. In addition, the use of
certain bytes in the random nonces as described in {{server-hello}}
allows the detection of downgrade to previous TLS versions.

As soon as the client and the server have exchanged enough information
to establish shared keys, the remainder of the handshake is encrypted,
thus providing protection against passive attackers. Because the server
authenticates before the client, the client can ensure that it only
reveals its identity to an authenticated server. Note that implementations
must use the provided record padding mechanism during the handshake
to avoid leaking information about the identities due to length.

A client that has sent authentication data to a server, either in the
main handshake or in post-handshake authentication, cannot be sure if
the server afterwards considers the client to be authenticated or not.
If the client needs to determine if the server considers the connection
to be unilaterally or mutually authenticated, this has to be provisioned
by the application layer. See {{CHHSV17}} for details.

The 0-RTT mode of operation generally provides the same security
properties as 1-RTT data, with the two exceptions that the 0-RTT
encryption keys do not provide full forward secrecy and that the
server is not able to guarantee full uniqueness of the handshake
(non-replayability) without keeping potentially undue amounts of
state. See {{early-data-indication}} for one mechanism to limit
the exposure to replay.

TLS does not provide security for handshakes which take place after the peer's
long-term secret (signature key or external PSK) is compromised. It therefore
does not provide post-compromise security {{CCG16}}, sometimes also referred to
as backwards or future security. This is in contrast to KCI resistance, which
describes the security guarantees that a party has after its own long-term
secret has been compromised.

The reader should refer to the following references for analysis of the
TLS handshake {{CHSV16}} {{FGSW16}} {{LXZFH16}}.

## Record Layer {#security-record-layer}

The record layer depends on the handshake producing strong traffic secrets
which can be used to derive bidirectional encryption keys and nonces.
Assuming that is true, and the keys are used for no more data than
indicated in {{limits-on-key-usage}} then the record layer should provide the following
guarantees:

Confidentiality.
: An attacker should not be able to determine the plaintext contents
of a given record.
{::comment}Cite IND-CPA?{:/comment}

Integrity.
: An attacker should not be able to craft a new record which is
different from an existing record which will be accepted by the receiver.
{::comment}Cite INT-CTXT?{:/comment}

Order protection/non-replayability
: An attacker should not be able to cause the receiver to accept a
record which it has already accepted or cause the receiver to accept
record N+1 without having first processed record N.

Length concealment.
: Given a record with a given external length, the attacker should not be able
to determine the amount of the record that is content versus padding.

Forward security after key change.
: If the traffic key update mechanism described in {{key-update}} has been
used and the previous generation key is deleted, an attacker who compromises
the endpoint should not be able to decrypt traffic encrypted with the old key.
{:br}

Informally, TLS 1.3 provides these properties by AEAD-protecting the
plaintext with a strong key. AEAD encryption {{RFC5116}} provides confidentiality
and integrity for the data. Non-replayability is provided by using
a separate nonce for each record, with the nonce being derived from
the record sequence number ({{nonce}}), with the sequence
number being maintained independently at both sides thus records which
are delivered out of order result in AEAD deprotection failures.

The plaintext protected by the AEAD function consists of content plus
variable-length padding. Because the padding is also encrypted, the
attacker cannot directly determine the length of the padding, but
may be able to measure it indirectly by the use of timing channels
exposed during record processing (i.e., seeing how long it takes to
process a record). In general, it is not known how to remove this
type of channel because even a constant time padding removal
function will then feed the content into data-dependent functions.

The re-keying technique in TLS 1.3 (see {{updating-traffic-keys}}) follows the
construction of the serial generator in [REKEY], which shows that re-keying can
allow keys to be used for a larger number of encryptions than without
re-keying. This relies on the security of the HKDF-Expand-Label function as a
pseudorandom function (PRF).  In addition, as long as this function is truly
one way, it is not possible to compute traffic keys from prior to a key change
(forward secrecy).

TLS does not provide security for data which is communicated on a connection
after a traffic secret of that connection is compromised. That is, TLS does not
provide post-compromise security/future secrecy/backward secrecy with respect
to the traffic secret. Indeed, an attacker who learns a traffic secret can
compute all future traffic secrets on that connection.  Systems which want such
guarantees need to do a fresh handshake and establish a new connection with an
(EC)DHE exchange.

The reader should refer to {{RECORD}} for analysis of the
TLS record layer.

# Working Group Information

The discussion list for the IETF TLS working group is located at the e-mail
address <tls@ietf.org>. Information on the group and information on how to
subscribe to the list is at <https://www.ietf.org/mailman/listinfo/tls>

Archives of the list can be found at:
<https://www.ietf.org/mail-archive/web/tls/current/index.html>


# Contributors

* Martin Abadi \\
  University of California, Santa Cruz \\
  abadi@cs.ucsc.edu

* Christopher Allen (co-editor of TLS 1.0) \\
  Alacrity Ventures \\
  ChristopherA@AlacrityManagement.com

* Steven M. Bellovin \\
  Columbia University \\
  smb@cs.columbia.edu

* David Benjamin \\
  Google \\
  davidben@google.com

* Benjamin Beurdouche \\
  INRIA & Microsoft Research - Joint Center \\
  benjamin.beurdouche@ens.fr

* Karthikeyan Bhargavan (co-author of [RFC7627]) \\
  INRIA \\
  karthikeyan.bhargavan@inria.fr

* Simon Blake-Wilson (co-author of [RFC4492]) \\
  BCI \\
  sblakewilson@bcisse.com

* Nelson Bolyard (co-author of [RFC4492]) \\
  Sun Microsystems, Inc. \\
  nelson@bolyard.com

* Ran Canetti \\
  IBM \\
  canetti@watson.ibm.com

* Pete Chown \\
  Skygate Technology Ltd \\
  pc@skygate.co.uk

* Katriel Cohn-Gordon \\
  University of Oxford \\
  me@katriel.co.uk

* Cas Cremers \\
  University of Oxford \\
  cas.cremers@cs.ox.ac.uk

* Antoine Delignat-Lavaud (co-author of [RFC7627]) \\
  INRIA \\
  antoine.delignat-lavaud@inria.fr

* Tim Dierks (co-editor of TLS 1.0, 1.1, and 1.2) \\
  Independent \\
  tim@dierks.org

* Taher Elgamal \\
  Securify \\
  taher@securify.com

* Pasi Eronen \\
  Nokia \\
  pasi.eronen@nokia.com

* Cedric Fournet \\
  Microsoft \\
  fournet@microsoft.com

* Anil Gangolli \\
  anil@busybuddha.org

* David M. Garrett \\
  dave@nulldereference.com

* Alessandro Ghedini \\
  Cloudflare Inc. \\
  alessandro@cloudflare.com

* Daniel Kahn Gillmor \\
  ACLU \\
  dkg@fifthhorseman.net

* Jens Guballa \\
  ETAS \\
  jens.guballa@etas.com

* Vipul Gupta (co-author of [RFC4492]) \\
  Sun Microsystems Laboratories \\
  vipul.gupta@sun.com

* Chris Hawk (co-author of [RFC4492]) \\
  Corriente Networks LLC \\
  chris@corriente.net

* Kipp Hickman

* Alfred Hoenes

* David Hopwood \\
  Independent Consultant \\
  david.hopwood@blueyonder.co.uk

* Marko Horvat \\
  MPI-SWS \\
  mhorvat@mpi-sws.org

* Jonathan Hoyland \\
  Royal Holloway, University of London

* Subodh Iyengar \\
  Facebook \\
  subodh@fb.com

* Benjamin Kaduk \\
  Akamai \\
  kaduk@mit.edu

* Hubert Kario \\
  Red Hat Inc. \\
  hkario@redhat.com

* Phil Karlton (co-author of SSL 3.0)

* Leon Klingele \\
  Independent \\
  mail@leonklingele.de

* Paul Kocher (co-author of SSL 3.0) \\
  Cryptography Research \\
  paul@cryptography.com

* Hugo Krawczyk \\
  IBM \\
  hugo@ee.technion.ac.il

* Adam Langley (co-author of [RFC7627]) \\
  Google \\
  agl@google.com

* Olivier Levillain \\
  ANSSI \\
  olivier.levillain@ssi.gouv.fr

* Xiaoyin Liu \\
  University of North Carolina at Chapel Hill \\
  xiaoyin.l@outlook.com

* Ilari Liusvaara \\
  Independent \\
  ilariliusvaara@welho.com

* Atul Luykx \\
  K.U. Leuven \\
  atul.luykx@kuleuven.be

* Carl Mehner \\
  USAA \\
  carl.mehner@usaa.com

* Jan Mikkelsen \\
  Transactionware \\
  janm@transactionware.com

* Bodo Moeller (co-author of [RFC4492]) \\
  Google \\
  bodo@openssl.org

* Erik Nygren \\
  Akamai Technologies \\
  erik+ietf@nygren.org

* Magnus Nystrom \\
  Microsoft \\
  mnystrom@microsoft.com

* Kazuho Oku \\
  DeNA Co., Ltd. \\
  kazuhooku@gmail.com

* Kenny Paterson \\
  Royal Holloway, University of London \\
  kenny.paterson@rhul.ac.uk

* Alfredo Pironti (co-author of [RFC7627]) \\
  INRIA \\
  alfredo.pironti@inria.fr

* Andrei Popov \\
  Microsoft \\
  andrei.popov@microsoft.com

* Marsh Ray (co-author of [RFC7627]) \\
  Microsoft \\
  maray@microsoft.com

* Robert Relyea \\
  Netscape Communications \\
  relyea@netscape.com

* Kyle Rose \\
  Akamai Technologies \\
  krose@krose.org

* Jim Roskind \\
  Netscape Communications \\
  jar@netscape.com

* Michael Sabin

* Rich Salz \\
  Akamai \\
  rsalz@akamai.com

* Sam Scott \\
  Royal Holloway, University of London \\
  me@samjs.co.uk

* Dan Simon \\
  Microsoft, Inc. \\
  dansimon@microsoft.com

* Nick Sullivan \\
  Cloudflare Inc. \\
  nick@cloudflare.com

* Bjoern Tackmann \\
  University of California, San Diego \\
  btackmann@eng.ucsd.edu

* Tim Taubert \\
  Mozilla \\
  ttaubert@mozilla.com

* Martin Thomson \\
  Mozilla \\
  mt@mozilla.com

* Filippo Valsorda \\
  Cloudflare Inc. \\
  filippo@cloudflare.com

* Thyla van der Merwe \\
  Royal Holloway, University of London \\
  tjvdmerwe@gmail.com

* Tom Weinstein

* Hoeteck Wee \\
  Ecole Normale Superieure, Paris \\
  hoeteck@alum.mit.edu

* David Wong \\
  NCC Group \\
  david.wong@nccgroup.trust

* Tim Wright \\
  Vodafone \\
  timothy.wright@vodafone.com

* Kazu Yamamoto \\
  Internet Initiative Japan Inc. \\
  kazu@iij.ad.jp
