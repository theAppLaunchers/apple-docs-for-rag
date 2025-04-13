

- TVMLKit JS
- XMLHttpRequest
-  getResponseHeader 

Instance Method

# getResponseHeader

Retrieves the field value from the response that is contained in the specified header.

TVMLKit JSWebKit JStvOS 9.0+Safari Desktop 4.0+Safari Mobile 3.0+

**tvOS**

``` source
String getResponseHeader(
    in String header
);
```

**Safari Desktop, Safari Mobile**

``` source
DOMString? getResponseHeader(
    DOMString header
);
```

## Parameters 

`header`  

The header field name. An exception is raised if this value is not `null` or `String`.

## Return Value

The header field value.

## Discussion

If the header value is `Set-Cookie` or `Set-Cookie2`, the value inside the header will not be returned. This method returns `null` if no response has been received or if the specified header doesn’t exist.

## See Also

### Manipulating the Header List

getAllResponseHeaders

Returns all of the response headers.

setRequestHeader

Appends a header to the list of request headers.

