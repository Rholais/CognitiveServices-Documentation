# Web API Interface
The model files built by the Knowledge Exploration Service can be hosted and accessed via a set of web APIs.  The APIs may be hosted on the local machine using the [`host_service`](CommandLine.md#host_service) command or be deployed to an Azure cloud service using the [`deploy_service`](CommandLine.md#deploy_service) command.  Both techniques expose the following API endpoints:
* [*interpret*](interpret.md) – Interprets a natural language query string. Returns annotated interpretations which can enable rich search-box auto-completion experiences that anticipate what the user is typing.
* [*evaluate*](evaluate.md) – Evaluates and returns the output of a structured query expression.
* [*calchistogram*](calchistogram.md) – Calculates a histogram of attribute values for objects returned by a structured query expression.

Used together, these API methods allow the creation of a rich semantic search experience.  Given a natural language query string, the *interpret* method provides annotated versions of the input query with structured query expressions, based on the underlying grammar and index data.  The *evaluate* method evaluates the structured query expression and returns the matching index objects for display.  The *calchistogram* method computes the attribute value distributions to enable filtering and refinement.

**Example**

In an academic publications domain, if a user types the string "latent s", the *interpret* method can provide a set of ranked interpretations, suggesting that the user might be searching for the keyword "latent semantic analysis", the title "latent structure analysis", or other expressions starting with "latent s".  This information can be used to quickly guide the user to the desired search results.

Based on the above interpretations, the *evaluate* method can be used to retrieve a set of matching publications from the academic index, and the *calchistogram* method can be used to calculate the distribution of attribute values for the matching publications which can be used to further filter and refine the search results.