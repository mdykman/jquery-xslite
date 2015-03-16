jquery.xslite extends 4 jquery ajax related methods. An application responding with XML containing an xsl-stylesheet processing instruction will have that transformation applied automatically.

  * `ajax(settings)`  - all jquery.ajax parameters are supported
```
  $.xslite.ajax({
        url:"some.xml",
        method:"GET",
        success: function (doc,st,jqxhr) {
// if 'some.xml' a contains an xsl-stylesheet processing instruction, 
// doc will be the post transformation document, otherwise, it will be 'some.xml' 
        }
   });
```

  * `load(url [, data][,success [, error]])`
    * url - the url to query
    * data - any request arguments
    * a callback routine called if the request is successfull
    * a callback routine called if the request fails

```
  $('#header').xslite.load('/rq/tour/header');
```

  * `get(url [, data][,success [, error]])`
    * url - the url to query
    * data - any request arguments
    * a callback routine called if the request is successfull
    * a callback routine called if the request fails

  * `post(url [, data][,success [, error]])`
    * url - the url to query
    * data - any request arguments
    * a callback routine called if the request is successfull
    * a callback routine called if the request fails

the success callback should expect the same callback parameters as those provided by jquery.    `function(data, textStatus, jqXHR)`

the error callback should expect the same callback parameters as those provided by jquery. `function(jqXHR, textStatus, errorThrown)`

Note that, when an XML response is returned containing processing instruction, execution of the success or error callbacks is deferred until that transformation has taken place.
When that is the case, the value of `data` in the success callback will be the result of the transform.  The XMLHttpObject will still have a reference to the pre-transformation XML.

If XML is not returned or no processing instruction is found, the effects of xslite should be transparent, allow requests to proceed normally.