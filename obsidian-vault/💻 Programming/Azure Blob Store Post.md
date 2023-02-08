Connect to Azure Blob store - .NET interactive notebook sample.

Using `.dib` file.

Create a new repo for this work.

---

In order to interact with Azure Storage and upload objects you'll need to reference two specific packages:

- `Azure.Storage.Blobs` - the physical Azure SDK that contains the raw types to connect to and write to storage.
- `Azure.Identity` - to be checked.

Start by bringing these libraries into scope:

---

The samples rely on types in the following namespaces:

- `Azure.Blob.Storage`.
- `Azure.Blob.Storage.Models` 
- `System.IO` - use to read a sample file from disk.

Execute the following using statements to ensure the later snippets compile and function as expected.