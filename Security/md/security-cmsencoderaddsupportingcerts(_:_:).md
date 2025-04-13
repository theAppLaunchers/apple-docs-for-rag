

- Security
-  CMSEncoderAddSupportingCerts(\_:\_:) 

Function

# CMSEncoderAddSupportingCerts(\_:\_:)

Adds certificates to a message.

macOS 10.5+

``` source
func CMSEncoderAddSupportingCerts(
    _ cmsEncoder: CMSEncoder,
    _ certOrArray: CFTypeRef
) -> OSStatus
```

## Parameters 

`cmsEncoder`  

The CMSEncoder reference returned by the `CMSEncoderCreate` function.

`certOrArray`  

Either a single certificate, specified as a certificate object (type `SecCertificateRef`), or a set of certificates specified as a `CFArray` of certificate objects.

## Return Value

A result code. See Security Framework Result Codes.

## Discussion

A CMS message can contain arbitrary sets of certificates other than or in addition to those indicating the identity of signers. You can use this function to add such certificates to a message. It is not necessary to call this function for a normal signed message. When you create a signed message, Cryptographic Message Services automatically adds the signer certificates and any intermediate certificates needed to verify the signers.

You can use this function even if you don’t sign or encrypt the message, in order to transport one or more certificates. To do so, call `CMSEncoderCreate` to obtain a `CMSEncoderRef` reference, call `CMSEncoderAddSupportingCerts` one or more times, and then call `CMSEncoderCopyEncodedContent` to complete the message. No additional content need be specified.

If you do add content to the message in addition to the certificates, you must call this function before the first call to the `CMSEncoderUpdateContent` function.

## See Also

### Related Documentation

func CMSEncoderUpdateContent(CMSEncoder, UnsafeRawPointer, Int) -> OSStatus

Feeds content bytes into the encoder.

func CMSEncoderCreate(UnsafeMutablePointer&lt;CMSEncoder?>) -> OSStatus

Creates a CMSEncoder reference.

func CMSDecoderCopyAllCerts(CMSDecoder, UnsafeMutablePointer&lt;CFArray?>) -> OSStatus

Obtains an array of all of the certificates in a message.

func CMSEncoderCopyEncodedContent(CMSEncoder, UnsafeMutablePointer&lt;CFData?>) -> OSStatus

Finishes encoding the message and obtains the encoded result.

func CMSEncoderCopySupportingCerts(CMSEncoder, UnsafeMutablePointer&lt;CFArray?>) -> OSStatus

Obtains the certificates added to a message with `CMSEncoderAddSupportingCerts`.

