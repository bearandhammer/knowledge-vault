## EF Collection Code

Just checking out an issue with EF around `TCollection`

https://github.com/dotnet/efcore/blob/767bc93c6e6fca19868f486c7df8f4235bcf53cd/src/EFCore.Relational/Query/RelationalShapedQueryCompilingExpressionVisitor.ShaperProcessingExpressionVisitor.ClientMethods.cs

`where TCollection : class, ICollection<TElement>`

```csharp
private static TCollection InitializeCollection<TElement, TCollection>(

int collectionId,

QueryContext queryContext,

DbDataReader dbDataReader,

SingleQueryResultCoordinator resultCoordinator,

Func<QueryContext, DbDataReader, object[]> parentIdentifier,

Func<QueryContext, DbDataReader, object[]> outerIdentifier,

IClrCollectionAccessor? clrCollectionAccessor)

where TCollection : class, ICollection<TElement>

{

var collection = clrCollectionAccessor?.Create() ?? new List<TElement>();

var parentKey = parentIdentifier(queryContext, dbDataReader);

var outerKey = outerIdentifier(queryContext, dbDataReader);

var collectionMaterializationContext = new SingleQueryCollectionContext(null, collection, parentKey, outerKey);

resultCoordinator.SetSingleQueryCollectionContext(collectionId, collectionMaterializationContext);

return (TCollection)collection;

}
```
