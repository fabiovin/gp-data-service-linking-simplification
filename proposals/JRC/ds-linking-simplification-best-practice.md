
# Data Service Linking Simplification Best Practice guidelines

`Version: draft 1.0`
`Date: 2021-10-13`

## Table of Contents

* [1. Introduction](#introduction)
* [2. Scope](#scope)
* [3. Conformance](#conformance)
* [4. Normative references](#normative-references)
* [5. Terms and definitions](#terms-and-definitions)
* [6. Symbols and abbreviated terms](#symbols-and-abbreviated-terms)
* [7. Data Service Linking Simplification](#ds-linking-simplif)
    * [7.1. Main principles](#main-principles)
    * [7.2. From the definition to the data](#def-to-data)
    * [7.3. From the data to the definition](#data-to-def)
* [8. Recommendations](#recs)
    * [8.1. Recommendation “INSPIRE-Dataset-Metadata-ResourceLocator”](#rec-ds-md-resloc)
    * [8.2. Recommendation “INSPIRE-NS-CoupledResource”](#rec-ns-coupled-res)
* [9. Example](#example)
* [10. Bibliography](#bibliography)
* [Annex A: Abstract Test Suite](#ats)
* [Annex B: Mapping the requirements from the IRs to the OGC  API - Features standard (and extensions)](#ir2oapif)
* [Annex C: Mapping between INSPIRE Network services metadata and OpenAPI definitions](#inspire-ns-openapi)
* [Annex D: Supported languages](#supported-lang)

## 1. Introduction <a name="introduction"></a>
_TODO_

## 2. Scope <a name="scope"></a>

This is the best practice document, originated from a consolidated proposal based on the collection and comparison of all the proposals received from the contributing Member State representatives of the MIWP 2.3.2 technical sub-group.

This document implements the recommendations and best-practice actions as initially described in the [Discussion Paper on possible simplification of data-service linking in INSPIRE](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/blob/main/resources/Discussion%20Paper%20on%20data-service%20linking%20v0.5.docx) and further improved by the subsequent proposals [proposals for the simplification approach](https://github.com/INSPIRE-MIF/gp-data-service-linking-simplification/tree/main/proposals) made by the members of the technical sub-group.
The reference for the metadata specification used in this proposal is the [INSPIRE MD TG v2.0.1](https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139). The reference for the INSPIRE Network Service (Download and View) specifications are the [INSPIRE NS - Download Service TG] and [INSPIRE NS - View Service TG].

## 3. Conformance <a name="conformance"></a>

_TODO_

## 4. Normative references <a name="normative-references"></a>

_TO_BE_REVIEW_

- **[ISO 19115-2:2019](https://schemas.isotc211.org/schemas/19115/-2/gmi/1.0/gmi.xsd)** - ISO 19115-2:2019, *Geographic information — Metadata — Part 2: Extensions for acquisition and processing*
- **[ISO/TS 19139:2007](https://www.isotc211.org/2005/gmd/)** - ISO/TS 19139:2007, *Geographic information — Metadata — XML schema implementation*
- **[IRs for NS]** - Commission Regulation (EC) No 976/2009 of 19 October 2009 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards the Network Services
- **[IRs for ISDSS]** - Commission Regulation (EU) No 1089/2010 of 23 November 2010 implementing Directive 2007/2/EC of the European Parliament and of the Council as regards interoperability of spatial data sets and services
- **[INSPIRE MD TG v2.0.1]** - INSPIRE Technical Guidance v2.0.1
- **[INSPIRE NS - Download Service TG]**
- **[INSPIRE NS - View Service TG]**
- **[RFC 4287]** - Internet Engineering Task Force (IETF). RFC 4287, *The Atom Syndication Format*. Initial release December 2005
- **[RFC 7231]** - Internet Engineering Task Force (IETF). RFC 7231, *Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content*. June 2014
- **[OGC API - Features - 1]** - OGC API - Features - Part 1: Core<sup> 2</sup>
- **[OGC API - Features - 2]** - OGC API - Features - Part 2: Coordinate Reference Systems by Reference
- **[OpenAPI 3.0]** - OpenAPI Initiative (OAI). *OpenAPI Specification*. The latest patch version at the time of publication of this document was 3.0.3, published in February 2020.


<sup>2 </sup> The standard is also published as [ISO 19168-1:2020, Geographic information — Geospatial API for features — Part 1: Core](https://www.iso.org/standard/32586.html). Note that a [draft version 1.0.1](http://docs.opengeospatial.org/DRAFTS/17-069r4.html) is available, see the included issues on https://github.com/opengeospatial/ogcapi-features/milestone/4?closed=1.

<!-- Second parts of the reference-style links, see also https://www.markdownguide.org/basic-syntax/#reference-style-links  -->
[IRs for NS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02009R0976-20141231&from=EN "Implementing Rules for Network Services (consolidated version of 31/12/2014)"
[IRs for ISDSS]: https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&from=EN "Implementing Rules for interoperability of spatial data sets and services (consolidated version of 31/12/2014)"
[INSPIRE MD TG v2.0.1]: https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139
[INSPIRE NS - Download Service TG]: https://inspire.ec.europa.eu
[INSPIRE NS - View Service TG]: https://inspire.ec.europa.eu
[OGC API - Features - 1]: http://docs.opengeospatial.org/is/17-069r3/17-069r3.html "OGC API - Features - Part 1: Core"
[OGC API - Features - 2]: http://docs.opengeospatial.org/is/18-058/18-058.html "OGC API - Features - Part 2: Coordinate Reference Systems by Reference"
[OpenAPI 3.0]: http://spec.openapis.org/oas/v3.0.3 "OpenAPI Specification 3.0"
[RFC 4287]: https://www.rfc-editor.org/rfc/rfc4287 "The Atom Syndication Format"
[RFC 7231]: https://www.rfc-editor.org/rfc/rfc7231 "HTTP/1.1: Semantics and Content"

## 5. Terms and definitions <a name="terms-and-definitions"></a>

_TO_BE_REVIEW_

For the purposes of this document, the following terms and definitions apply:

| Term | Definition | Source |
| --- | --- | --- |
| content negotiation | The practice of providing multiple representations available via the same URI | [ISO/IEC 19788](https://www.iso.org/obp/ui/#iso:std:iso-iec:19788:-7:ed-1:v1:en:sec:3.20) |
| data set | Identifiable collection of data. | [ISO 19115](https://www.iso.org/obp/ui/#iso:std:iso:19115:-2:ed-2:v1:en:sec:3.6) |
| distribution (of a data set) | A specific representation of a data set. A data set might be available in multiple serializations that may differ in various ways, including natural language, media-type or format, schematic organization, temporal and spatial resolution, level of detail or profiles (which might specify any or all of the above). | [DCAT](https://www.w3.org/TR/vocab-dcat-2/#Class:Distribution) |
| direct access download service | Download Service which provides access to the Spatial Objects in Spatial Data Sets based upon a query | \[[IRs for NS]\] |
| encoding | Conversion of data into a series of codes. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.13) |
| encoding rule | Identifiable collection of conversion rules that define the encoding for a particular data structure. | [ISO 19118](https://www.iso.org/obp/ui/#iso:std:iso:19118:ed-2:v1:en:term:4.14) |
| feature | Abstraction of real world phenomena. **NOTE** The concept of a `feature` is synonymous to a `spatial object` in INSPIRE | [OGC API - Features - 1](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature) |
| feature collection | A set of features from a data set. | [OGC API - Features - 1](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature_collection) |
| feature type | **NOTE** The concept of a `feature type` is synonymous to a `spatial object type` in INSPIRE | [INSPIRE](https://inspire.ec.europa.eu/glossary/SpatialObject) |
| pre-defined data set download service | Service that enables copies of spatial data sets, or parts of such sets, to be downloaded. | \[[IRs for NS]\] |
| Web API | API using an architectural style that is founded on the technologies of the Web. | [DWBP](https://www.w3.org/TR/dwbp) |


**NOTE** ISO and the European Commission maintain comprehensive terminological databases at the following addresses:
- [ISO Online browsing platform](https://www.iso.org/obp)
- [INSPIRE glossary](http://inspire.ec.europa.eu/glossary)

## 6. Symbols and abbreviated terms <a name="symbols-and-abbreviated-terms"></a>

_TO_BE_REVIEW_

| Abbreviation | Term |
| --- | --- |
| API |    Application Programming Interface |
| GML | Geography Markup Language |
| OAPIF | OGC API - Features |
| URL |    Uniform Resource Locator |
| WFS | Web Feature Service |
| WMS | Web Map Service |
| WMTS | Web Map Tile Service |

## 7. Data Service Linking Simplification <a name="ds-linking-simplif"></a>

### 7.1. Main principles <a name="main-principles"></a>

- A Web API provides data from one data set. This means that one data publisher often will need to provide more than one Web API.<sup> [3](#footnote3)</sup>
- The exact composition of a data set is determined by the data publisher. It may be that the data set contains all that publishers’ information on one INSPIRE theme, but other compositions are allowed.
- A data set is structured into one or several feature collections. Аll feature collections available in one API (under the `/collections` path) are considered to be part of the data set provided by that Web API.
- A feature collection contains features of only one feature type.

For example, two data sets (with their own metadata records), one on buildings and one on addresses will have two landing pages (https://developer.my-org.eu/apis/addresses/ and https://developer.my-org.eu/apis/buildings/) rather than one landing page for the Web API (https://developer.my-org.eu/apis/oapif/) and two feature collections, one for each data set (https://developer.my-org.eu/apis/oapif/collections/addresses and https://developer.my-org.eu/apis/oapif/collections/buildings).

The mapping between INSPIRE resources and [OAPIF resources](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#table_1) is given below, for an example data set containing addresses <sup> [5](#footnote5)</sup>.

| INSPIRE resource | OAPIF resource | Sample path | Document reference |
| ------------- | ------------- | ------------- |-------------: |
| (Distribution<sup> 4</sup> of a) data set | Landing page | `https://developer.my-org.eu/apis/addresses/` | [OAPIF 7.2 API landing page](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_api_landing_page) |
| Data set metadata | Feature collections | `https://developer.my-org.eu/apis/addresses/collections/` | [OAPIF 7.13 Feature collections](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_collections_) |
| -- | Feature collection | `https://developer.my-org.eu/apis/addresses/collections/address` | [OAPIF 7.14 Feature collection](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_collection_) |
| Spatial objects | Features | `https://developer.my-org.eu/apis/addresses/collections/address/items` | [OAPIF 7.15 Features](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_items_) |
| Spatial object | Feature | `https://developer.my-org.eu/apis/addresses/collections/address/items/{featureId}` | [OAPIF 7.16 Feature](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_feature_) |

<sup id="footnote3">3 </sup>The principle that a Web API provides data from one data set is in line with OGC API - Features - Part 1: Core, as illustrated by the quotes below. As long as no other parts for OGC API - Features are defined that support multiple datasets, INSPIRE adheres to this principle.

> By default, every API implementing this standard will provide access to a single dataset.

> A server that implements this conformance class provides access to the features in a dataset. In other words, the API is a distribution of that dataset. A file download, for example, would be another distribution.

<sup>4 </sup>The notion of a distribution is not present in the INSPIRE legislation, the legislation does not make the distinction between a data set and its distribution(s). However, this distinction is relevant, see also section 4 in \[DWBP\].

<sup id="footnote5">5 </sup> See the [overview page of OGC API - Features implementations](https://github.com/opengeospatial/ogcapi-features/blob/master/implementations.md) and the [overview page of the Good Practice implementations](../deployments) for existing implementations.

### 7.2. Resources <a name="resources"></a>

The figures below illustrate the resources defined by OGC API – Features, and links to external resources that are required by the depicted requirements classes, including the link relation types to be used.

![Resources and relations between them for the INSPIRE core requirements class](figures/resources_core.png)

![Resources and relations between them for the INSPIRE bulk download requirements class](figures/resources_bulk.png)

## 8. Recommendations <a name="recs"></a>
 
### 8.1. Requirements class “INSPIRE-pre-defined-data-set-download-OAPIF”  <a name="req-pre-defined"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/oapif-download/1.0/req/pre-defined |
| --- | --- |
| Target type | Web API |
| Dependency | [OAPIF Requirements class "OpenAPI 3.0"](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_openapi_3_0) |

The Web API depends on the [OAPIF Requirements class OpenAPI 3.0](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_openapi_3_0), and therefore also on the [OAPIF Requirements class Core](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_core), for providing access to INSPIRE data.

**NOTE 1** The Web API shall return collections and features in the default OAPIF coordinate reference system (WGS 84 longitude and latitude). However, the `enclosure` link for bulk download could still provide access to a data set in a different CRS.

**NOTE 2** In the OAPIF standard, the [OpenAPI 3.0 Requirements class](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_openapi_3_0) is optional. This specification proposes to make it a mandatory requirement for INSPIRE in order to facilitate the development of client applications, and in particular adding support in the [European INSPIRE geoportal](https://inspire-geoportal.ec.europa.eu). That is why, the Web API SHALL comply with OAPIF requirements class OpenAPI 3.0.


**NOTE 3** In accordance with the security requirements of the [OpenAPI 3.0 Requirements class](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#security), for cases where the operations of the server are access-controlled, the security scheme(s) SHALL be documented in the OpenAPI definition.

**NOTE 4** There are plans to add additional requirements classes for other API description standards (or standard versions) in the future (e.g. for OpenAPI v3.1). When additional requirements classes become available, this specification will be reviewed and possibly revised to include these as additional options.

**NOTE 5** For cases where data sets are too big for retrieval with a single API request, using multiple requests following the `next` links (paging) [TODO: add link that explains paging] is considered to meet the requirements for a download service. This will also help to support frequently updated data sets.

**NOTE 6** To support browser-based applications accessing the API directly, it is common practice to support [cross-origin requests](http://www.opengis.net/doc/IS/ogcapi-features-1/1.0#cross_origin).


#### Metadata elements of the data set

| **Requirement** | **/req/pre-defined/spatial-data-set-metadata** |
| --- | --- |
| A | The response of the `/collections` operation SHALL include a link to the metadata record for the data set. This link SHALL have `rel` link parameter `describedby` and `type` link parameter `application/xml`. |

**NOTE** This is an enforcement of recommendation [http://www.opengis.net/spec/ogcapi-features-1/1.0/rec/core/fc-md-descriptions](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#rec_core_fc-md-descriptions) in [OGC API - Features - 1] for the metadata record.

The data set metadata record must be available in the relevant national geoportal (see https://inspire.ec.europa.eu/INSPIRE-in-your-Country), must be harvested by the [INSPIRE Geoportal](https://inspire-geoportal.ec.europa.eu) and must be INSPIRE-compliant. However, this is out of scope for this specification. Note that often the person responsible for the metadata is not the same as the person responsible for the Web API.

**TEST**
1. Issue an HTTP GET request to {root}/collections.
2. Validate that at least one of the links returned in the response has `rel` link parameter `describedby` and `type` link parameter `application/xml`.
3. For each of the links returned in the response having a `rel` link parameter `describedby` and `type` link parameter `application/xml`, issue an HTTP HEAD request to the path given in the `href` link parameter of that link.
4. Validate that for one of the responses the returned XML document satisfies one of the following:
    - The document has root element `{http://www.opengis.net/cat/csw/2.0.2}GetRecordByIdResponse` followed by element `{http://www.isotc211.org/2005/gmd}MD_Metadata`.
    - The document has root element `{http://www.isotc211.org/2005/gmd}MD_Metadata`.
    - The document has root element `{http://standards.iso.org/iso/19115/-2/gmi/1.0}MI_Metadata`.

| **Recommendation** | **/rec/pre-defined/spatial-data-set-metadata-html** |
| --- | --- |
| A | If the API implements the HTML requirements class, the response of the `/collections` operation SHOULD include a link to the metadata record for the data set with `rel` link parameter `describedby` and `type` link parameter `text/html`. |


**NOTE** If the data set is available in GML, the link to the GML application schema of the data set will also have `rel` link parameter `describedby` and `type` link parameter `application/xml`.

#### Organisation of a data set in feature collections

| **Requirement** | **/req/pre-defined/spatial-object-type** |
| --- | --- |
| A | Every collection SHALL contain features of only one feature type
 
**NOTE** According to the OAPIF standard a collection could also contain more than one feature type.
 
**TEST**
1. Manual check for every collection, that all its features belong to the same feature type.

| **Requirement** | **/req/pre-defined/feature-concept-dictionary** |
| --- | --- |
| A | For each `collection` that provides data that is harmonised according to the \[[IRs for ISDSS]\], a link with the link relation type `tag` to the corresponding entry in the [INSPIRE feature concept dictionary](https://inspire.ec.europa.eu/featureconcept) SHALL be included.

| **Recommendation** | **/rec/pre-defined/collection-naming** |
| --- | --- |
| A | For each `collection` that provides data that is harmonised according to the \[[IRs for ISDSS]\], the id of the collection SHOULD be the lowercase version of the language-neutral name of the feature type as specified in the \[[IRs for ISDSS]\]. | 


**TEST**
1. Check all collections for a valid link to the INSPIRE feature concept dictionary.
2. If no link is available - MANUAL TEST: Check that the collections have not yet been harmonised.

#### Terms of use

| **Requirement** | **/req/pre-defined/licence** |
| --- | --- |
| A | The Web API SHALL contain a link to the licence of the data set in the `links` property of the response of the request to `/collections` (relation: `license`). |

**NOTE** This is an enforcement of subrecommendation B of recommendation http://www.opengis.net/spec/ogcapi-features-1/1.0/rec/core/fc-md-license in [OGC API - Features - 1].



**TEST**
1. Issue an HTTP GET request to `{root}/collections`.
2. Validate that at least one of the links returned in the response has `rel` link parameter `license`.
3. For each of the links returned in the response having a `rel` link parameter equal to `license`, issue an HTTP GET request to the path given in the `href` link parameter of that link.
4. For each of the responses, validate that the HTTP status code is 200.

| **Recommendation** | **/rec/pre-defined/license-openapi** |
| --- | --- |
| A | The licence information for the exposed data set SHOULD be provided in accordance with [OpenAPI 3.0]. |

**NOTE**: A proposal for mapping between INSPIRE NS Metadata elements and OpenAPI definition fields is available in [Annex C.](#inspire-ns-openapi)

### 8.2. Requirements class INSPIRE-multilinguality <a name="req-multilinguality"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/oapif-download/1.0/req/multilinguality |
| --- | --- |
| Target type | Web API |
| Dependency | [INSPIRE-pre-defined-data-set-download-OAPIF](#req-pre-defined) |

This requirements class is mandatory for all data sets that contain information in more than one natural language. For a data set containing textual information, the language used in the data set is given in the [Resource Language metadata element](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02008R1205-20081224&from=EN#tocId19).

**PRECONDITION TESTS**
1. For the document retrieved in the test for /req/pre-defined/spatial-data-set-metadata, check whether more than one Resource Language is provided. See also https://github.com/inspire-eu-validation/metadata/blob/2.0/datasets-and-series/resource-language.md

The requirements from the \[[IRs for NS]\] to support requests in different natural languages are met in the Web API through HTTP language negotiation, using HTTP headers as specified in [RFC 7231], language tags as specified in [RFC 5646] and matching of language tags as specified in [RFC 4647].

| **Requirement** | **/req/multilinguality/accept-language-header** |
| --- | --- |
| A | The Web API SHALL support the `Accept-Language` HTTP header in requests to the landing page (`/`), `/collections`, `/collections/{collectionId}`, `/collections/{collectionId}/items` and `/collections/{collectionId}/items/{featureId}` in accordance with [RFC 7231], [RFC 5646] and [RFC 4647].|

**TEST**
1. Issue an HTTP GET request with an `Accept-Language` HTTP header that contains a valid language priority list (prioritized or weighted list of language ranges, see [RFC 4647]) that does not contain `*;q=0.0` to the following URLs: `{root}/` and `{root}/collections`. For every feature collection identified in the response of `{root}/collections`, issue an HTTP request with an `Accept-Language` HTTP header containing a valid language priority list that does not contain `*;q=0.0` to the following URLs: `{root}/collections/{collectionId}`, `{root}/collections/{collectionId}/items?limit=5`.
2. For every response, validate that the HTTP status code is 200.

| **Recommendation** | **/rec/multilinguality/accept-language-header-no-matching-language-tag** |
| --- | --- |
| A | The Web API SHOULD return either HTTP status code 200 or HTTP status code 406 (Not Acceptable) when none of the available representations for the response have a language tag that matches the `Accept-Language` HTTP header given by the client. |
| B | The Web API SHOULD return a representation in the default language when the returned HTTP status code is 200. |
| C | The Web API SHOULD return a response with a response body containing a list of all supported languages when the returned HTTP status code is 406. |

An `Accept-Language` HTTP header that contains `*;q=0.0`, e.g. `en;q=1.0,*;q=0.0`, tells the server that the client is only willing to accept certain languages, e.g. only English in the given example. According to [RFC 7231], in the case that the server cannot honour the clients request, the server "can either disregard the header field by treating the response as if it is not subject to content negotiation or honor the header field by sending a 406 (Not Acceptable) response". Guidelines on what option to choose depend on the context, see also [Annex D: Supported languages](#supported-lang).



| **Requirement** | **/req/multilinguality/content-language-root** |
| --- | --- |
| A | The Web API SHALL include the `Content-Language` HTTP header in the response for a request to its landing page `(/)` in accordance with [RFC 7231] and [RFC 5646]. |

**TEST**
1. Issue an HTTP GET request with an `Accept-Language` HTTP header containing a valid language priority list to URL `{root}/`.
2. Validate that a response is returned with a `Content-Language` HTTP header.
3. Issue an HTTP GET request without a `Accept-Language` HTTP header to URL `{root}/`.
4. Validate that a response is returned with a `Content-Language` HTTP header.

| **Recommendation** | **/rec/multilinguality/content-negotiation** |
| --- | --- |
| A | The Web API SHOULD take the language specified in the `Accept-Language` HTTP header of a request to all paths into account. The Web API SHOULD include the `Content-Language` HTTP header in the response for a request to all paths in accordance with [RFC 7231] and [RFC 5646]. |

| **Requirement** | **/req/multilinguality/hreflang** |
| --- | --- |
| A | A link with the link relation type `enclosure` SHALL include the `hreflang` link parameter containing the language of that distribution. The value of `hreflang` SHALL be in accordance with [RFC 4647]. |

**TEST**

1. Issue an HTTP GET request to `{root}/collections`.
2. For each of the links returned in the response having a `rel` link parameter equal to `enclosure`, validate that the `hreflang` parameter is present.
3. Check that the `hreflang` parameter contains a language encoded in accordance with [RFC 4647].

### 8.3. Requirements class “INSPIRE-OAPIF-GeoJSON” <a name="req-oapif-json"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/oapif-download/1.0/req/geojson |
| --- | --- |
| Target type | Web API |
| Dependency | [INSPIRE-pre-defined-data-set-download-OAPIF](#req-pre-defined)  |
| Dependency | [OAPIF requirements class GeoJSON](http://docs.opengeospatial.org/is/17-069r3/17-069r3.html#_requirements_class_geojson)  |

This requirements class is relevant when providing access to INSPIRE data encoded as (Geo-)JSON (e.g. by following the approach defined in [INSPIRE action 2017.2](https://webgate.ec.europa.eu/fpfis/wikis/pages/viewpage.action?pageId=277742184) for 'Addresses' and 'Environmental Monitoring Facilities').

| **Recommendation** | **/rec/geojson/geojson-inspire** |
| --- | --- |
| A | The GeoJSON encoding rule used for each feature collection and the features it contains SHOULD be documented in accordance with the guidelines in the [repository for alternative encodings](https://github.com/INSPIRE-MIF/2017.2) and SHOULD be based on model transformations and conversion rules documented in that repository if the feature collection provides data that are harmonised according to the \[[IRs for ISDSS]\]. |

Note that in order to conform to the legal requirements of INSPIRE, any encoding rule used must be properly documented, see also [Article 7](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:02010R1089-20141231&qid=1604512031742&from=EN#tocId9) in the \[[IRs for ISDSS]\].

### 8.4. Requirements class “INSPIRE-bulk-download” <a name="req-bulk-download"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/oapif-download/1.0/req/bulk-download |
| --- | --- |
| Target type | Web API |
| Dependency | [INSPIRE-pre-defined-data-set-download-OAPIF](#req-pre-defined)  |

This requirements class implements the recommendation from \[DWBP\] to provide a [bulk download](https://www.w3.org/TR/dwbp/#BulkAccess) of a dataset, to enable consumers to retrieve the full dataset through a single request. It therefore allows for providing datasets that meet the Open Definition \[OD\] \[Dodd16\].

| **Requirement** | **/req/pre-defined/enclosure** |
| --- | --- |
| A | At least one of the following conditions SHALL be met:<br>1. The response of the `/collections` operation includes at least one `enclosure` link that allows requesting a representation of the entire data set.<br>2. The response of each `/collections/{collectionId}` operation includes at least one `enclosure` link that allows requesting a representation of the entire feature collection. |

**TEST**

1. Issue an HTTP GET request to {root}/collections and to each {root}/collections/{collectionId}.
2. Validate that the Collections response and/or each of the Collection responses have a link with the `rel` link parameter `enclosure`.
3. For each of the links returned in the response having a `rel` link parameter equal to `enclosure`, issue an HTTP HEAD request to the path given in the `href` link parameter of that link.
4. For each of the responses:
    - If the HTTP status code is 405 (Method Not Allowed), the test verdict is inconclusive.
    - If HTTP status code 200 is returned and HTTP header` Content-Length` > 0, the test verdict is “pass”.
    - Otherwise, the test verdict is “fail”.

| **Requirement** | **/req/pre-defined/enclosure-type** |
| --- | --- |
| A | A link with the relation type `enclosure` SHALL include the `type` link parameter containing a type which is included in the [INSPIRE media-types register](https://inspire.ec.europa.eu/media-types). |

**TEST**
1. Issue an HTTP GET request to `{root}/collections`.
2. For each of the links returned in the response having a `rel` link parameter equal to `enclosure`, validate that the `type` parameter is present and the media type is valid according the [INSPIRE media-types register](https://inspire.ec.europa.eu/media-types).


**NOTE** Requirements for downloads of a whole data set available in more than one natural language are included in the requirements class INSPIRE-multilinguality.


| **Recommendation** | **/rec/pre-defined/enclosure-length** |
| --- | --- |
| A | A link with the link relation type `enclosure` SHOULD include the `length` link parameter containing the length in bytes. |

| **Recommendation** | **/rec/pre-defined/enclosure-title** |
| --- | --- |
| A | The link(s) with the link relation type `enclosure` SHOULD include the `title` link parameter. |

### 8.5. Requirements class “INSPIRE-CRS” <a name="req-crs"></a>

| Requirements class | http://inspire.ec.europa.eu/id/spec/oapif-download/1.0/req/inspire-crs |
| --- | --- |
| Target type | Web API |
| Dependency | [INSPIRE-pre-defined-data-set-download-OAPIF](#req-pre-defined)  |
| Dependency | [OAPIF requirements class Coordinate Reference Systems by Reference](https://docs.opengeospatial.org/is/18-058/18-058.html#_requirements_class_coordinate_reference_systems_by_reference)  |

| **Recommendation** | **/rec/inspire-crs/recognised-crs** |
| --- | --- |
| A | For each feature collection in the API at least one of the coordinate reference systems (CRS) listed below SHOULD be included in the list of supported coordinate reference systems. |

**List of supported CRS**
- http://www.opengis.net/def/crs/EPSG/0/4936
- http://www.opengis.net/def/crs/EPSG/0/4937
- http://www.opengis.net/def/crs/EPSG/0/4258
- http://www.opengis.net/def/crs/EPSG/0/3035
- http://www.opengis.net/def/crs/EPSG/0/3034
- http://www.opengis.net/def/crs/EPSG/0/3038
- http://www.opengis.net/def/crs/EPSG/0/3039
- http://www.opengis.net/def/crs/EPSG/0/3040
- http://www.opengis.net/def/crs/EPSG/0/3041
- http://www.opengis.net/def/crs/EPSG/0/3042
- http://www.opengis.net/def/crs/EPSG/0/3043
- http://www.opengis.net/def/crs/EPSG/0/3044
- http://www.opengis.net/def/crs/EPSG/0/3045
- http://www.opengis.net/def/crs/EPSG/0/3046
- http://www.opengis.net/def/crs/EPSG/0/3047
- http://www.opengis.net/def/crs/EPSG/0/3048
- http://www.opengis.net/def/crs/EPSG/0/3049
- http://www.opengis.net/def/crs/EPSG/0/3050
- http://www.opengis.net/def/crs/EPSG/0/3051
- http://www.opengis.net/def/crs/EPSG/0/5730
- http://www.opengis.net/def/crs/EPSG/0/7409


**NOTE** The MIG supported a proposed solution to set up a Coordinate Reference System (CRS) registry and control body to manage the proposal of additional CRS under the governance of the MIG. Once this registry has been established, this requirements class will be updated.


## 9. Example <a name="example"></a>

See Appendix A for complete examples





## 10. Bibliography <a name="bibliography"></a>

- \[Alla10\] ALLAMARAJU, Subbu. *RESTful Web services cookbook*. O’Reilly Media, 2010. ISBN 978-0-596-80168-7.
- \[Dodd16\] DODDS, Leigh. Why are bulk downloads of open data important? *Lost Boy*. 19 September 2016. \[Viewed 4 March 2020\]. Available from: <https://blog.ldodds.com/2016/09/19/why-are-bulk-downloads-of-open-data-important/>
- \[DWBP\] W3C. *Data on the Web Best Practices*. W3C Recommendation. 31 January 2017. Available from: <https://www.w3.org/TR/dwbp/>
- \[GCloud-REST\] *REST Guidelines of Belgian government institutions*. Available from: <https://www.gcloud.belgium.be/rest/>
- [INSPIRE UML-to-GeoJSON encoding rule](https://github.com/INSPIRE-MIF/2017.2/blob/master/GeoJSON/geojson-encoding-rule.md)
- \[MDN\] MDN. *406 Not Acceptable - HTTP \| MDN*.  Available from: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/406>
- \[OD\] *Open Definition*. Version 2.1. Open Knowledge Foundation, November 2015. Available from: <https://opendefinition.org/od/2.1>
- \[SDWBP\] W3C. *Spatial Data on the Web Best Practices*. W3C Working Group Note & OGC Best Practice. 28 September 2017. Available from: <https://www.w3.org/TR/sdw-bp/>
- \[SO1\] How to properly send 406 status code? *Stack Overflow*. \[Viewed 4 March 2020\]. Available from: <https://stackoverflow.com/questions/4422980/how-to-properly-send-406-status-code>
- \[SO2\] Format for 406 Not Acceptable payload? *Stack Overflow*. \[Viewed 4 March 2020\]. Available from: <https://stackoverflow.com/questions/50102277/format-for-406-not-acceptable-payload>
- \[TG Download\] INITIAL OPERATING CAPABILITY TASK FORCE FOR NETWORK SERVICES. *Technical Guidance for the implementation of INSPIRE Download Services*. Version 3.1. Initial Operating Capability Task Force, 9 August 2013. Available from: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services

<!-- Second parts of the reference-style links, see also https://www.markdownguide.org/basic-syntax/#reference-style-links  -->
[Alla10]: https://www.oreilly.com/library/view/restful-web-services/9780596809140/ "RESTful Web services cookbook"
[GCloud-REST]: https://www.gcloud.belgium.be/rest/ "REST Guidelines of Belgian government institutions"
[MDN]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/406 "406 Not Acceptable - HTTP | MDN"
[SO1]: https://stackoverflow.com/questions/4422980/how-to-properly-send-406-status-code "How to properly send 406 status code? (Stack Overflow)"
[SO2]: https://stackoverflow.com/questions/50102277/format-for-406-not-acceptable-payload "Format for 406 Not Acceptable payload? (Stack Overflow)"
[RFC 7807]: https://www.rfc-editor.org/info/rfc7807 "Problem Details for HTTP APIs"
[TG Download]: https://inspire.ec.europa.eu/documents/technical-guidance-implementation-inspire-download-services "Technical Guidance for the implementation of INSPIRE Download Services"

# Annex A: Examples <a name="inspire-examples"></a>
## Examples (XML encoded)

#### Example of Resource Locator of a dataset metadata linking to an INSPIRE View Service - WM(T)S - Get View Service Metadata

_Note: for the definition of a WMTS service, use the proper codelist defined before inside the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetCapabilities&amp;service=WMS&amp;version=1.3.0</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">wms</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">View Service</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### View - WM(T)S - Get Map

_Note: for the definition of a WMTS service, use the proper codelist defined before inside the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wms?request=GetMap&amp;service=WMS&amp;version=1.3.0&amp;layers=1&amp;styles=default&amp;CRS=EPSG:4258&amp;format=image/png&amp;bbox=0.87,43.26,11.68,48.13&amp;width=600&amp;height=400</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wms">OGC:WMS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/view">view</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE WMS</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - ATOM feed - Get Download Service Metadata

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_2021</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - ATOM feed - Get Spatial Data Set (subfeed)

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../atom/INSPIRE_DW_2021_Dataset.gml</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="https://tools.ietf.org/html/rfc4287">ATOM Syndication Format</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (ATOM)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - OGC service - Get Download Service Metadata

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist defined before inside the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetCapabilities</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

#### Download - OGC service - Get Spatial Data Set

_Note: this example covers the WFS definition. For a WCS/SOS service, use the proper codelist defined before inside the `protocol` element_

```xml
<gmd:transferOptions>
  <gmd:MD_DigitalTransferOptions>
      [...]
    <gmd:onLine>
      <gmd:CI_OnlineResource>
        <gmd:linkage>
          <gmd:URL>http://.../wfs?service=wfs&amp;version=2.0.0&amp;request=GetFeature&amp;storedquery_id=http://inspire.ec.europa.eu/operation/download/GetSpatialDataSet&amp;DataSetIdCode=mycode&amp;DataSetIdNamespace=mynamespace&amp;CRS=EPSG:4326&amp;Language=eng</gmd:URL>
        </gmd:linkage>
        <gmd:protocol>
          <gmx:Anchor xlink:href="http://www.opengis.net/def/serviceType/ogc/wfs">OGC:WFS</gmx:Anchor>
        </gmd:protocol>
        <gmd:applicationProfile>
          <gmx:Anchor xlink:href="http://inspire.ec.europa.eu/metadata-codelist/SpatialDataServiceType/download">download</gmx:Anchor>
        </gmd:applicationProfile>
        <gmd:name>
          <gco:CharacterString>INSPIRE Download Service (WFS)</gco:CharacterString>
        </gmd:name>
      </gmd:CI_OnlineResource>
    </gmd:onLine>
      [...]
  </gmd:MD_DigitalTransferOptions>
</gmd:transferOptions>
```

# Annex B: template <a name="annex-b"></a>
_TO_BE_DONE_

# Annex C: template  <a name="annex-c"></a>
_TO_BE_DONE_
