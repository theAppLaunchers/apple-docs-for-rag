

- Security
- Certificate, Key, and Trust Services
- Trust
-  Configuring a Trust 

Article

# Configuring a Trust

Work around a recoverable trust failure.

## Overview

The default procedure described in Evaluating a Trust and Parsing the Result is often sufficient for evaluating trust, but sometimes you need finer-grained control. Whether in response to a recoverable trust failure or based on prior knowledge of the situation, the certificate, key, and trust services API allows you to customize trust evaluation to deal with certain common scenarios.

For example, by default, trust evaluation compares the validity dates of a certificate against the current date to see whether a certificate is operative. If a certificate used to sign a document is currently expired, trust fails. But if the same certificate was valid at the time the document was signed, you might want to consider the certificate valid for this purpose. If you know the signing date, you can use the SecTrustSetVerifyDate(_:_:) function to change the evaluation date to match. Do this after creating the trust but before running the evaluation (or rerunning it after a recoverable failure). For example, if the document is exactly one year old:

- Swift
- Objective-C

```
let newDate = Date.init(timeIntervalSinceNow: -60*60*24*365)
SecTrustSetVerifyDate(trust, newDate as CFDate)
```

```
NSDate* newDate = [NSDate dateWithTimeIntervalSinceNow:-60*60*24*365];SecTrustSetVerifyDate(trust, (__bridge CFDateRef)newDate);
```

Running the evaluation now may succeed if the evaluation date is within the window of the certificate’s validity period. Or it may fail for some other reason that you need to investigate.

Besides the problem of expiration dates, another common trust evaluation problem arises from using a custom, self-signed root certificate as an anchor. By default, the system trusts as an anchor only the root certificates packaged with the operating system (see the lists for iOS and macOS), but you can supplement this list. If you bundle a self-signed certificate with your app, you can indicate to the system that you trust it for use as an anchor by making a call to the SecTrustSetAnchorCertificates(_:_:) function:

- Swift
- Objective-C

```
let anchorCert = 
let anchors = [ anchorCert ]
SecTrustSetAnchorCertificates(trust, anchors as CFArray)
```

```
SecCertificateRef anchorCert = ;
NSArray* anchors = @[ (__bridge id)anchorCert ];
SecTrustSetAnchorCertificates(trust,(__bridge CFTypeRef)anchors);
```

When you make this call, you tell the system to consider only the named certificate or certificates as potential anchors for this trust. If you want to enable the usual set of anchors as well, you use an additional call to the SecTrustSetAnchorCertificatesOnly(_:_:) function, with a value of false for the second argument. Note that these calls affect only the referenced trust. Other trust evaluations, both in your app and elsewhere on the device, are unaffected.

When you approve an anchor certificate for a trust using the SecTrustSetAnchorCertificates(_:_:) function, you don’t need to name it explicitly in the certificate array passed to the SecTrustCreateWithCertificates(_:_:_:) function, because the system automatically adds it to the certificate chain.

