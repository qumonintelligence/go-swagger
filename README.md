Swagger 2.0
===========

[![Build Status](https://travis-ci.org/casualjim/go-swagger.svg?branch=master)](https://travis-ci.org/casualjim/go-swagger)[![Coverage Status](https://coveralls.io/repos/casualjim/go-swagger/badge.svg?branch=master)](https://coveralls.io/r/casualjim/go-swagger?branch=master)[![GoDoc](https://godoc.org/github.com/casualjim/go-swagger?status.svg)](http://godoc.org/github.com/casualjim/go-swagger)[![license](http://img.shields.io/badge/license-Apache%20v2-orange.svg)](https://raw.githubusercontent.com/swagger-api/swagger-spec/master/LICENSE)

This API is not stable yet, when it is stable it will be distributed over gopkg.in

Contains an implementation of Swagger 2.0. It knows how to serialize and deserialize swagger specifications.

Swagger is a simple yet powerful representation of your RESTful API.  
With the largest ecosystem of API tooling on the planet, thousands of developers are supporting Swagger in almost every modern programming language and deployment environment.

With a Swagger-enabled API, you get interactive documentation, client SDK generation and discoverability. We created Swagger to help fulfill the promise of APIs.

Swagger helps companies like Apigee, Getty Images, Intuit, LivingSocial, McKesson, Microsoft, Morningstar, and PayPal build the best possible services with RESTful APIs.Now in version 2.0, Swagger is more enabling than ever. And it's 100% open source software.

Docs
----

http://godoc.org/github.com/casualjim/go-swagger

Install:

		go get -u github.com/casualjim/go-swagger/cmd/swagger

The implementation also provides a number of command line tools to help working with swagger.

Currently there is a spec validator tool:

		swagger validate https://raw.githubusercontent.com/swagger-api/swagger-spec/master/examples/v2.0/json/petstore-expanded.json

You can also serve a swagger document with the swagger UI

		swagger ui ./swagger.json

To generate a server for a swagger spec document:

		swagger generate all -f ./swagger.json -A [application-name] [--principal [principal-name]] --include-main --include-ui


Design
------

For now what exists of documentation on how all the pieces fit together, is described in this [doc](design.md)


What's inside?
--------------

For a V1 I want to have this feature set completed:

-	[x] An object model that serializes to swagger yaml or json
-	[x] A tool to work with swagger:
	-	[x] validate a swagger spec document
	-	[x] validate against jsonschema
	-	[ ] validate extra rules outlined [here](https://github.com/apigee-127/swagger-tools/blob/master/docs/Swagger_Validation.md)
	-	[x] serve swagger UI for any swagger spec file
	-	[x] generate stub api based on swagger spec
	-	[ ] generate client from a swagger spec
	-	[ ] generate "sensible" random data based on swagger spec
	-	[ ] generate tests based on swagger spec for server
	-	[ ] generate tests based on swagger spec for client
-	[x] Middlewares:
	-	[x] serve spec
	-	[x] routing
	-	[x] validation
	-	[x] additional validation through an interface
	-	[ ] authorization
		-	[x] basic auth
		-	[x] api key auth
		-	[ ] oauth2
			-	[ ] implicit
			-	[ ] access code
			-	[ ] password
			-	[ ] application
	-	[x] swagger docs UI
-	[x] Typed JSON Schema implementation
	-	[x] JSON Pointer that knows about structs
	-	[x] JSON Reference that knows about structs
	-	[x] Passes current json schema test suite
-	[x] extended string formats
	-	[x] uuid, uuid3, uuid4, uuid5
	-	[x] email
	-	[x] uri (absolute)
	-	[x] hostname
	-	[x] ipv4
	-	[x] ipv6
	-	[x] credit card
	-	[x] isbn, isbn10, isbn13
	-	[x] social security number
	-	[x] hexcolor
	-	[x] rgbcolor
	-	[x] date
	-	[x] date-time
	-	[x] duration
	-	[x] custom string formats

Later
-----

After the v1 implementation extra transports are on the roadmap

- Formats:
	- [ ] custom serializer for XML to support namespaces and prefixes
	- [ ] optimized serializer for JSON
	- [ ] optimized serializer for YAML
-	Tools:
	-	[ ] generate spec document based on the code
	-	[ ] watch swagger spec file and regenerate when modified
-	Transports:
	-	[ ] swagger socket (swagger over tcp sockets)
	-	[ ] swagger websocket (swagger over websockets)
