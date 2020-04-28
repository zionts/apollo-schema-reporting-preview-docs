# Preview: Apollo Schema Reporting

Welcome to our pre-release documentation for Apollo Schema Reporting, a protocol and implementation for GraphQL servers to automatically report their schema information to the Apollo registry. 

This repository is meant to provide early access users with information about this new project, along with a central place to provide feedback and instructions on getting started.

## Before you start: IMPORTANT DISCLAIMER

The documentation here is currently only a preview of pre-release software. You may use it at will, but this evaluation product is not yet fully supported or considered generally available. While we will try to avoid breaking changes once a feature is in use, until the features discussed herein are taken out of preview we could make breaking changes. Please be aware of the heightened risk of using preview software.

Use of anything described in these preview docs (current as of April 2020) is done at your own risk and is governed by [The Apollo Terms of Service](https://www.apollographql.com/Apollo-Terms-of-Service.pdf).

PREVIEWS ARE PROVIDED "AS-IS," "WITH ALL FAULTS," AND "AS AVAILABLE," AND ARE EXCLUDED FROM ANY SERVICE LEVEL AGREEMENTS AND LIMITED WARRANTY. Previews may not be covered by customer support. Previews may be subject to reduced or different security, compliance and privacy commitments, as further explained in the Terms of Service, Privacy Policy and any additional notices provided with the Preview. We may change or discontinue Previews at any time without notice. We also may choose not to release a Preview into "General Availability."

## Getting started

If you're reading this, you've discovered, either through communication with our team or scouring docs & changelog entries, that we are exploring reporting schema definitions from running servers. This functionality is designed to make it easy and accurate to track the evolution of your GraphQL schema over time, without needing to make changes to your deployment pipeline.

This documentation will cover a few different components of what we're working on in more detail, including:

1. The protocol for schema reporting
2. The Apollo Server reference implementation of schema reporting
3. Automatic schema promotion to the registry

This top-level README will provide an overview, along with information on how to get started today with Apollo Server.

## Overview

Apollo schema reporting is a GraphQL API, by which running servers can report the shape of the schema they're serving to Apollo Graph Manager, in the form of a [GraphQL document (SDL)](https://www.apollographql.com/docs/apollo-server/schema/schema/#the-schema-definition-language). A running GraphQL server needs only have this document and an identifier for this document (we recommend `hex(sha256(document))`) in order to report its schema.