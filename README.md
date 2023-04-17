POC-OpenId
==========

Proof of concept for integrating OpenID Connect authentication with a .NET application.

Requirements
------------

-   .NET 5.0 SDK or higher
-   `Microsoft.AspNetCore.Authentication.OpenIdConnect` NuGet package
-   `Microsoft.AspNetCore.Authentication.Cookies` NuGet package

Usage
-----

1.  Clone the repository: `git clone https://github.com/<username>/POC-OpenId.git`.
2.  Open the solution in Visual Studio or your preferred IDE.
3.  Create a project in the Google Cloud Console and enable the OpenID Connect API. See [these instructions](https://developers.google.com/identity/protocols/oauth2/openid-connect#appsetup).
4.  Configure the OpenID Connect options in `appsettings.json`:
    -   `ClientId`: the client ID for your project.
    -   `ClientSecret`: the client secret for your project.
    -   `Authority`: the authorization server endpoint.
    -   `CallbackPath`: the callback path for the OpenID Connect middleware.
5.  Start the application.
6.  Navigate to the home page and click the "Login" button.
7.  You will be redirected to the Google login page. Enter your credentials to authenticate.
8.  Upon successful authentication, you will be redirected back to the application's home page.

Anti-Forgery State Token
------------------------

To protect against request forgery attacks, this POC generates a unique session token that holds state between the application and the user's client. This token is often referred to as a cross-site request forgery (CSRF) token.

The token is generated using the `RandomNumberGenerator` class and has a length of 32 characters.

References
----------

-   [OpenID Connect documentation](https://developers.google.com/identity/protocols/oauth2/openid-connect)
-   [`Microsoft.AspNetCore.Authentication.OpenIdConnect` documentation](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/openid-connect?view=aspnetcore-5.0)
-   [`Microsoft.AspNetCore.Authentication.Cookies` documentation](https://docs.microsoft.com/en-us/aspnet/core/security/authentication/cookie?view=aspnetcore-5.0)
