# Claims, Roles and Policies

https://www.youtube.com/watch?v=ae3gevt-Im8

https://www.youtube.com/watch?v=cbtK3U2aOlg

https://www.youtube.com/watch?v=kpSwmLlMu9E

https://www.youtube.com/watch?v=hHRFjbGTEOk


---

## HTML Page
---

```html
@page
@using System.Security.Claims;
@model IndexModel
@{
    ViewData["Title"] = "Home page";
    var identity = (ClaimsIdentity)User.Identity;
}
<div class="text-center">
    <h1 class="display-4">User Claims</h1>
    <hr />
    <div>
        <table class="table table-striped">
            <thead>
                <tr>
                    <th>Type</th>
                    <th>Value</th>
                </tr>
            </thead>
            <tbody>
                @foreach (Claim userClaim in identity.Claims)
                {
                    <tr>
                        <td>@userClaim.Type</td>
                        <td>@userClaim.Value</td>
                    </tr>
                }
            </tbody>
        </table>
    </div>
</div>
```

https://stackoverflow.com/questions/22652543/does-new-asp-net-mvc-identity-framework-work-without-entity-framework-and-sql-se

---

Ended up being easier to use IAsyncPageFilter - much cleaner solution.

Store claims in session and transfer to Claims Principal.



