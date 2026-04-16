# AspNetCore.Playground

Collection a ASP.NET Core samples that can be run in a Codespace

## JSON Patch

Playground for JSON Patch as described in the article [JSON Patch support in ASP.NET Core web API].

[JSON Patch support in ASP.NET Core web API]: https://learn.microsoft.com/aspnet/core/web-api/jsonpatch?view=aspnetcore-10.0

To run, open this repo in a codespace and then

```sh
cd web-api/jsonpatch/JsonPatch
dotnet run
```

Then open the [JsonPatch.http file]

[JsonPatch.http file]: web-api/jsonpatch/JsonPatch/JsonPatch.http

and issue the sample requests to explore the behavior.

## WebMinOpenApi

Playgrounds for [OpenAPI support in ASP.NET Core API apps][openapi-overview].
The sample app lives in [`fundamentals/openapi/10.x/WebMinOpenApi`](fundamentals/openapi/10.x/WebMinOpenApi)
(a .NET 9 variant is in `9.x/`).

Each scenario is gated by a `#define` at the top of
[`Program.cs`](fundamentals/openapi/10.x/WebMinOpenApi/Program.cs).
Uncomment **one** `#define` at a time, then build and run:

```sh
cd fundamentals/openapi/10.x/WebMinOpenApi
dotnet run
```

Then open the [WebMinOpenApi.http file] and issue the sample requests to explore
the behavior.

[WebMinOpenApi.http file]: fundamentals/openapi/10.x/WebMinOpenApi/WebMinOpenApi.http

### Getting started

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `FIRST` | Minimal OpenAPI setup — just `AddOpenApi()` and `MapOpenApi()` with a single `GET /` endpoint. | [Configure OpenAPI document generation][aspnetcore-openapi] |
| `DEFAULT` | The ASP.NET Core Minimal API template with a `GET /weatherforecast` endpoint and OpenAPI enabled. | [OpenAPI overview][openapi-overview] |

### OpenAPI document UIs

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `SWAGGERUI` | Integrates **Swagger UI** via the `Swashbuckle.AspNetCore.SwaggerUi` package. Browse to `/swagger` to see the UI. | [Use Swagger UI][using-swagger-ui] |
| `OPENAPIWITHSCALAR` | Integrates the **Scalar** interactive API reference. Browse to `/scalar` to see the UI. | [Use Scalar for interactive API documentation][using-scalar] |

### OpenAPI endpoint configuration

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `MAPOPENAPIWITHAUTH` | Protects the OpenAPI endpoint with JWT Bearer authentication and a `tester` role policy. | [Limit OpenAPI document access to authorized users][openapi-auth] |
| `MAPOPENAPIWITHCACHING` | Caches the generated OpenAPI document using output caching with a 10-minute expiration. | [Cache generated OpenAPI document][openapi-caching] |

### Document transformers

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `DOCUMENTtransformer1` | Uses an **inline delegate** to set the document title, version, and description. | [Use document transformers][doc-transformers] |
| `DOCUMENTtransformer2` | Uses a **class-based `IOpenApiDocumentTransformer`** to add a JWT Bearer security scheme to the document. | [Use document transformers][doc-transformers] |

### Operation transformers

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `OPERATIONtransformer1` | Adds a `500 Internal Server Error` response to **every** operation via a global operation transformer delegate. | [Use operation transformers][op-transformers] |
| `OPERATIONtransformer2` | Marks a specific endpoint (`GET /old`) as **deprecated** using a per-endpoint `AddOpenApiOperationTransformer`. Also defines `GET /new` as its replacement. | [Use operation transformers][op-transformers] |

### Schema transformers

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `SCHEMAtransformer1` | Sets the `format` of `decimal` types to `"decimal"` instead of the default. Returns a JSON body from `GET /`. | [Use schema transformers][schema-transformers] |

### Advanced / combined scenarios

| `#define` | What it demonstrates | Learn docs |
|---|---|---|
| `DOCUMENTtransformerUse999` | Shows **all nine ways** to register transformers: inline delegate, instance, and DI-activated generic — for document, operation, and schema transformers. | [OpenAPI document transformers][transformers-overview] |
| `DOCUMENTtransformerInOut` | Demonstrates **transformer execution order**: schema transformers run first, then operation transformers, then document transformers. | [Execution order for transformers][transformer-order] |
| `MULTIDOC_OPERATIONtransformer1` | Generates **two separate OpenAPI documents** (`internal` with Bearer security and `public`) using `WithGroupName()` to assign endpoints. Fetch them at `/openapi/internal.json` and `/openapi/public.json`. | [Generate multiple OpenAPI documents][multidoc] |

<!-- reference-style links -->
[openapi-overview]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/overview?view=aspnetcore-10.0
[aspnetcore-openapi]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-10.0
[using-swagger-ui]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/using-openapi-documents?view=aspnetcore-10.0
[using-scalar]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/using-openapi-documents?view=aspnetcore-10.0#use-scalar-for-interactive-api-documentation
[openapi-auth]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-10.0#limit-openapi-document-access-to-authorized-users
[openapi-caching]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-10.0#cache-generated-openapi-document
[doc-transformers]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/customize-openapi?view=aspnetcore-10.0#use-document-transformers
[op-transformers]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/customize-openapi?view=aspnetcore-10.0#use-operation-transformers
[schema-transformers]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/customize-openapi?view=aspnetcore-10.0#use-schema-transformers
[transformers-overview]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/customize-openapi?view=aspnetcore-10.0#openapi-document-transformers
[transformer-order]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/customize-openapi?view=aspnetcore-10.0#execution-order-for-transformers
[multidoc]: https://learn.microsoft.com/aspnet/core/fundamentals/openapi/aspnetcore-openapi?view=aspnetcore-10.0#generate-multiple-openapi-documents
