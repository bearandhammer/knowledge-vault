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

---

To push a sample object to storage we require some test data, which we will construct using a test `ValueTuple` . There are a few facets that need to be completed here manually in order for the future code elements to work:
- `"<CONNECTION_STRING>"` - this should be completed with a generated Shared Access Token from the Azure Portal with the following permissions:
	- Permission A
	- Permission B
	- etc
- `"<CONTAINER_NAME"` - the name of the container in Azure Storage (under `Containers`) that you wish to write the test object.

You'll need to add a `.jpg` file to a local directory (at `C:\TestImage`) called `test-image.jpg`. The requirement, when this was constructed, was to illustrate how a base 64 string could be transferred to storage (via a `MemoryStream`), so this conversion is done inside the `GetSampleRequestSetting` method, for illustration only. Lastly, a random blob named is generated with the use of a new `Guid`. This reflects the file name that will appear in the container.

Execute the snippet to create the method called `GetSampleRequestSettings` :

---

Run the following code to generate a sample request object based on executing the `GetSampleRequestSettings` method:

---

To see all of the current request values, run the next snippet. Of particular importance is the `BlobResourceName` . You'll want to check the relevant container for this file, after upload, via the Azure Portal, Azure CLI or Azure Storage Explorer.

---

To break down the process, we start by creating a client scoped to the container we wish to write to. This type is the `BlobContainerClient` . We create this use the `BlobServiceClient` type, with the Shared Access Signature connection string in tow. The `GetBlobContainerClient` method, supplied with the correct container name, allows us to later retrieve a `BlobClient` for writing to the container:

---

The following allows us to inspect a couple of facets of the constructed `containerClient` (`BlobContainerClient`), for reference:

---

Lastly, a `BlobClient` is created from the `BlobContainerClient` (constructed with the resource name that you wish to generated). The sample shows how a base 64 string is used to construct a `MemoryStream` , which is ultimated used to call the `UploadAsync` method on the `BlobClient` . A key point here is that a `BlobHttpHeaders` type must be supplied to the `UploadAsync` method to control the content type of the uploaded object:

---

This content can be pushed into the markdown (and tidied) tomorrow. New blog post for the weekend!


