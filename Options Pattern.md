%% #-🪴weedy %%
[[Unsorted]]
# Snapshot options
Using [IOptionsSnapshot](https://learn.microsoft.com/en-us/dotnet/api/microsoft.extensions.options.ioptionssnapshot-1):
- Options are computed once per request when accessed and cached for the lifetime of the request.
- May incur a significant performance penalty because it's a [Scoped service](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection#scoped) and is recomputed per request. For more information, see [this GitHub issue](https://github.com/dotnet/runtime/issues/53793) and [Improve the performance of configuration binding](https://github.com/dotnet/runtime/issues/36130).
- Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.
# Sources
https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/options?view=aspnetcore-8.0
