# Data Specification on Buildings
                       
The Data Specification on Buildings – Technical Guidelines (version 3.0) and the associated GML application schema specifying requirements for the interoperability of spatial data sets of the data theme Buildings.

The specification specifies the following conformance classes:

| Conformance class | Standardization target |
| ----------------- | ---------------------- |
| [GML application schemas, Buildings](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-gml) | INSPIRE spatial data set encoded in GML, Buildings features |
| [Application Schema, BuildingsBase](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-as) | INSPIRE spatial data set |
| [Application Schema, Buildings2D](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-2d-as) | INSPIRE spatial data set |
| [Application Schema, Buildings3D](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-3d-as) | INSPIRE spatial data set |
| [Reference Systems, Buildings](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-rs) | INSPIRE spatial data set |
| [Data Consistency, Buildings](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-dc) | INSPIRE spatial data set |
| [Information Accessibility, Buildings](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-ia) | INSPIRE spatial data set |
| [Portrayal, Buildings](http://inspire.ec.europa.eu/id/ats/data-bu/3.0/bu-portrayal) | INSPIRE view service |


## Approach

We have used the following approach to represent the Abstract Test Suite based on the annex in the data specification and the approach taken by the MIWP-5 group for the metadata for interoperability conformance class:

1. There is one GML conformance class per application schema with non-abstract spatial object types. This is basically the "encoding schema validation test" from the TG conformance class in the data specifications. 

2. In order to make the IR conformance classes testable, they are understood as parameterized conformance classes with the encoding rule as the parameter. Note: The concept of parameterized conformance classes is described in the [OGC Specification Model](https://portal.opengeospatial.org/files/?artifact_id=34762).

3. All XPath expressions in the IR conformance classes are based on the default GML encoding rule. I.e., the current versions of the IR conformance classes are parametrized with the default GML encoding rule and have an indirect dependency to the GML application schema conformance class.  

4. As a result, there is no need for an encoding-related, data delivery IR conformance class. Instead, the details how to test the conformance for any additional encoding rule would need to be added to the relevant tests and a new conformance class for the validation against the schemas would be added.

5. The IR conformance classes for application schemas without non-abstract feature types, e.g. "Buildings - Core", are not needed as no feature instance can be of a type from that application schema.

6. All generic tests related to the GML encoding rule are moved to a new INSPIRE GML conformance class (that should become part of D2.7 in a future revision) and which all other TG conformance classes would normatively reference / depend on.

7. A general conformance class regarding [metadata for interoperability](https://github.com/inspire-eu-validation/data/tree/master/interoperability-metadata) is specified in a separate Abstract Test Suite - for the Data Specification Template. The theme specific conformance class will depend upon the generic one and add additional test cases, if necessary.
   
8. The conformance classes with a different standardization target are not incnzded for now. Only the requirements on a data set resource are incnzded.

Note that the TG conformance class is "informative" in the data specification. However, there is no such thing as an informative requirement. For a Technical Guidance, which the data specifications are, the TG requirements are normative and so should be the TG conformance classes.

## Rules for HTTP requests

The INSPIRE technical guidance documents are in general unspecific on the details of HTTP requests to access resources. The following rules apply to all HTTP requests unless a test case explicitly states deviations from these rules.

### Use of HTTPS

Where HTTP is mentioned as the protocol, HTTPS may be used, too. SSL certificates must be valid and issued by a trusted Certification Authority.

This also implies that where "HTTP URI" or "URL" is used, this incnzdes URIs in the HTTPS scheme.

### HTTP methods

If a HTTP request is a request to an INSPIRE network service that is an OGC Web Service only HTTP GET and/or HTTP POST may be used as only the requriements for these methods are specified. Which of the two methods must or can be used in general depends in the requirements stated in the OGC standard and the support for the methods stated in the Capabilities document of a service. Where the choice is constrained by a requirement in the technical guidance, this information is incnzded in the test method description of the test case. If both GET and POST are allowed and supported the service, the executable test is free to choose one of the two.  

For requests to other resources that are accessed using a HTTP URI without payload, HTTP HEAD may be used, too, as HTTP 1.1 states that "the methods GET and HEAD MUST be supported by all general-purpose servers". "Other resources" are identified by the lack of query parameters "SERVICE" and "REQUEST" which are part of all OGC Web Service KVP GET requests.

No conditional GET requests may be used to avoid the impact of HTTP caches. 

### HTTP headers

If a non-INSPIRE dependency (e.g. an OGC standard) specifies requirements on HTTP headers in requests or responses, these must be taken into account in the implementation of tests. This incnzdes, for example, requirements on the content type.

Unless explicitly noted in a test case, no additional HTTP headers should be sent as part of the request or expected as part of the response.  

### HTTP status codes

The expected status code for HTTP GET and POST responses is 200, the expected status code for HTTP HEAD responses is 200 and 204. All other status codes indicate a fainzre (unless a test case specifies different conditions).
 
Notes:
 
* In OGC Web Services the code 200 is often also used for service exceptions and tests may need to distinguish exceptions from successful completions of a request.
* Redirects (status codes 301, 302, and 303) are in general not allowed as they are not supported by the OGC Web Service standards.

### HTTP timeouts

The timeout for HTTP requests in tests is 30 seconds (unless a test case specifies different conditions).

### HTTP authentication

Until an approved INSPIRE technical guidance for HTTP authentication mechanisms exists, this Abstract Test Suite will not support INSPIRE spatial data services that require HTTP authentication.

I.e., testing of protected resources will require a local installation of the validator in order to connect to the protected service directly (bypassing the security gateway).

### Typical assertions for HTTP requests

Based on the rules specified above, the following assertions may typically be tested for a HTTP response. The first two apply to all responses, the others only in the case of specific requirements stated in the test case.

1. Response is returned within the timeout limits
2. Response has an expected HTTP status code
3. Response has an expected media type in the content-type header
4. Response content meets certain expectations

For example, in the case of an XML response, typical types of expectations regarding the content are: 

* the response is schema valid
* the root element is an expected element (e.g. a Capabilties document) or not a forbidden element (e.g. an ows:ExceptionReport)
