---
title: Rule Technical Notes
description: Technical notes about using "[!DNL Live Search]" rules.
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
---
# Rule Technical Notes

[!DNL Live Search] rules trigger actions based on a variety of query conditions and give merchants the ability to shape the search experience for various scenarios.

The current release of [!DNL Live Search] rules is based on the query string that is entered by the shopper, rather than on the set of returned results. A query string can include alphanumeric characters and capitalization is ignored. As with facets and synonyms, rules are stored in `protobuf dynamo`. At query time, the search service retrieves rules through `grpc` calls to `search-admin-service`.
