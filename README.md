## SSL OR TLS Which is good?
We use to believe that TLS 1.0 is a Successor of SSL 3.0. As we know SSL3.0 are very old and recent attacks like POODLE, BEAST, and other attack vectors made SSL3.0 lifeless as a security protocol.

CSN
Due to POODLE attack, SSL v3 is being completely disabled on web sites around the world.
Then the BEAST attack which completely break web sites running on older SSL v3.0 and TLS v1.0 protocols.
Sadly still some of the websites do not use TLS, you can check your website configuration using the Comodo SSL analyzer.

TLS Handshake Protocol
When a TLS client and server first start communicating, they agree on a protocol version, select cryptographic algorithms, optionally authenticate each other, and use public-key encryption techniques to generate shared secrets.

The TLS Handshake Protocol involves the following steps:

Exchange hello messages to agree on algorithms, exchange random values and check for session resumption.
Exchange the necessary cryptographic parameters to allow the client and server to agree on a premaster secret.
Exchange certificates and cryptographic information to allow the client and server to authenticate them.
Generate a master secret from the premaster secret and exchange random values.
Provide security parameters to the recording layer.
Allow the client and server to verify that their peer has calculated the same security parameters and that the handshake occurred without tampering with an attacker.

TLS and SSL Protocol Notifications
If any problem’s encountered in the connection any one of the parties who discover the issue will trigger an alert message. You can find some cheap wildcard SSL Certificates here.

SSL Alert Descriptions
Close_Notify

This message notifies the recipient that the sender will not send any more messages on this connection.

Unexpected_message

An inappropriate message was received. This alert is always fatal and should never be observed in communication between proper implementations.

Bad_record_mac

This alert is returned if a record is received with an incorrect MAC.

This alert will be returned if an alert is sent because a TLSCiphertext decrypted in an invalid way: either it wasn’t an even multiple of the block length, or its padding values, when
checked, weren’t correct.

Decryption_failed_RESERVED

This alert was used in some earlier versions of TLS and may have permitted certain attacks against the CBC mode.

Record_overflow

A TLSCiphertext record was received that had a length of more than 2^14+2048 bytes or a record decrypted to a TLSCompressed record with more than 2^14+1024 bytes.

Decompression_failure

The decompression function received improper input (e.g., data that would expand to excessive length).

This message is always fatal and should never be observed in communication between proper implementations.

Handshake_failure

The reception of a handshake_failure alert message indicates that the sender was unable to negotiate an acceptable set of security parameters given the options available. This is a fatal error.

No_certificate_RESERVED

This alert was used in SSLv3 but not any version of TLS. It MUST NOT be sent by compliant implementations.

Bad_certificate

A certificate was corrupt, contained signatures that did not verify correctly, etc.

Unsupported_certificate

A certificate was of an unsupported type.

Certificate_revoked

A certificate was revoked by its signer.

Also Read:  Fast and Complete SSL Scanner to Find Mis-configurations Affecting TLS/SSL Severs-A Detailed Analysis

Additional TLS alert Descriptions
Certificate_expired

A certificate has expired or is not currently valid.

Certificate_unknown

Some other (unspecified) issues arose in processing the certificate, rendering it unacceptable.

Illegal_parameter

A field in the handshake was out of range or inconsistent with other fields. This message is always fatal.

Unknown_ca

A valid certificate chain or partial chain was received, but the certificate was not accepted because the CA certificate could not be located or couldn’t be matched with a known, trusted CA. This message is always fatal.

Access_denied

A valid certificate was received, but when access control was applied, the sender decided not to proceed with the negotiation. This message is always fatal.

Decode_error

A message could not be decoded because some field was out of the specified range or the length of the message was incorrect.

This message is always fatal and should never be observed in communication between proper implementations (except when messages were corrupted in the network).

Decrypt_error

A handshake cryptographic operation failed, including being unable to correctly verify a signature or validate a Finished message. This message is always fatal.

Export_restriction_RESERVED

This alert was used in some earlier versions of TLS. It MUST NOT be sent by compliant implementations.

Protocol_version

The protocol version the client has attempted to negotiate is recognized but not supported. (For example, old protocol versions might be avoided for security reasons.) This message is always fatal.

Insufficient_security

Returned instead of handshake_failure when a negotiation has failed specifically because the server requires ciphers more secure than those supported by the client. This message is always fatal.

Internal_error

An internal error unrelated to the peer or the correctness of the protocol (such as a memory allocation failure) makes it impossible to continue. This message is always fatal.

User_canceled

This handshake is being canceled for some reason unrelated to a protocol failure. If the user cancels an operation after the handshake is complete, just closing the connection by sending a close_notify is more appropriate.

This alert should be followed by a close_notify. This message is generally a warning.

No_renegotiation

Sent by the client in response to a hello request or by the server in response to a client hello after initial handshaking.

Either of these would normally lead to renegotiation; when that is not appropriate, the recipient should respond with this alert. At that point, the original requester can decide whether to proceed with the connection.

One case where this would be appropriate is where a server has spawned a process to satisfy a request; the process might receive security parameters (key length, authentication, etc.) at startup, and it might be difficult to communicate changes to these parameters after that point. This message is always a warning.

Unsupported_extension

sent by clients that receive an extended server hello containing an extension that they did not put in the corresponding client hello. This message is always fatal.

Compatibility with TLS and SSL
tls ssl
Since there are various versions of TLS (1.0, 1.1, 1.2, and any future versions) and SSL (2.0 and 3.0), means are needed to negotiate the specific protocol version to use.

The TLS protocol provides a built-in mechanism for version negotiation so as not to bother other protocol components with the complexities of version selection.

 A TLS 1.2 client who wishes to negotiate with such older servers will send a normal TLS 1.2 ClientHello, containing { 3, 3 } (TLS 1.2) in ClientHello.client_version.

If the server does not support this version, it will respond with a ServerHello containing an older version number. If the client agrees to use this version, the negotiation will proceed as appropriate for the negotiated protocol

If a TLS server receives a ClientHello containing a version number greater than the highest version supported by the server, it MUST reply according to the highest version supported by the server.

For example, if the server supports TLS 1.0, 1.1, and 1.2, and client_version is TLS 1.0, the server will proceed with a TLS 1.0 ServerHello. If the server supports (or is willing to use) only versions greater than client_version, it MUST send a “protocol_version” alert message and close the connection.

Whenever a client already knows the highest protocol version known to a server (for example, when resuming a session), it SHOULD initiate the connection in that native protocol.

I’m sure there are several other functions and differences than this, for more information on TLS protocol Attributes & functions you can refer to RFC5246.

Download: Free GDPR Comics Book – Importance of Following General Data Protection Regulation (GDPR) to Protect your Company Data and user privacy

You can follow us on Linkedin, Twitter, and Facebook for daily Cybersecurity updates also you can take the Best Cybersecurity course online to keep yourself updated.
