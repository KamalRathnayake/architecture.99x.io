# Setup Azure AD B2C
## Azure AD B2C tenant Configuration 
Create an Azure B2C tenant (skip if already created): https://docs.microsoft.com/en-us/azure/active-directory-b2c/tutorial-register-applications?tabs=app-reg-ga  
## Azure AD B2C App registration Configuration
Create app registration with Azure AD B2C: https://docs.microsoft.com/en-us/azure/active-directory-b2c/tutorial-register-applications?tabs=app-reg-ga 
- Add offline_access with admin consent configured 
- To run locally configure  
    - Redirect URI: https://localhost:7055/signin-oidc 
    - Sign-out URL: https://localhost:7055/signout-oidc 
    - Replace values in appsettings.json based on created B2C resource 
    - Add client secret in the app registration used in the web application
- Create sign in sign up user flow (use recommended) with display name

## Azure AD B2C Implementation 
Refer: https://learn.microsoft.com/en-us/aspnet/core/security/authentication/azure-ad-b2c?view=aspnetcore-6.0 
