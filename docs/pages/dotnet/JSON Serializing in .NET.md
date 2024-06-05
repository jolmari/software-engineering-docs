# System.Text.Json

## Explicit mapping of JSON properties to C# properties

When deserializing JSON to a C# object, you can use the `JsonPropertyName` attribute to map JSON properties to C# properties. This is useful when the JSON property names are vastly different from the C# property names.

```csharp
[JsonPropertyName("example-property_001")]
public string ExampleProperty { get; set; }

...

var myObject = JsonSerializer.Deserialize<MyObjectType>(jsonString);
```