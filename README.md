# probable-palm-tree

Links
- https://learn.microsoft.com/en-us/azure/static-web-apps/authentication-authorization
- https://learn.microsoft.com/en-us/azure/static-web-apps/authentication-custom?tabs=aad%2Cinvitations

Steps on high level in Entra ID
- Create new app reg
    - Redirect URI: 
        - web
        - `https://thankful-grass-0cfea5003.6.azurestaticapps.net/.auth/login/aad/callback`
    - Check ID tokens (used for implicit and hybrid flows)
    - Create secret
- Go to enterprise apps -> to your app
    - Properties, turn on "Assignment required?"
        - Turn off visible to users (optional)
    - Users and Groups, add users who are eligible for signing in to the static web app

Steps on high level in Azure
- Create Static Web App
    - STANDARD HOSTING PLAN! You cannot use custom authentication (entra id) with free hosting plan
    - Connect CI/CD to your repository
- Go to your SWA
- Add environment variables
    - Client ID
    - Client secret
- Authentication, select Custom for Mode
- Modify `staticwebapp.config.json` to match your env
    - environent variables (CLIENTID, SECRET)
    - Tenant id to `openIdIssuer`