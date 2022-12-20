# Full project listing

Angular Okta Enterprise listing 

* Authnticate user via okta [public app with fingerprint](https://developer.okta.com/docs/reference/api/authn/#response-parameters) to get the session token
```
curl -v -X POST \
-H "Accept: application/json" \
-H "Content-Type: application/json" \
-H "Authorization: SSWS ${api_token}" \
-H "User-Agent: Mozilla/5.0 (${systemInformation}) ${platform} (${platformDetails}) ${extensions}" \
-H "X-Forwarded-For: 23.235.46.133" \
-d '{
  "username": "dade.murphy@example.com",
  "password": "correcthorsebatterystaple",
  "options": {
    "multiOptionalFactorEnroll": false,
    "warnBeforePasswordExpired": false
  },
  "context": {
    "deviceToken": "26q43Ak9Eh04p7H6Nnx0m69JqYOrfVBY"
  }
}' "https://${yourOktaDomain}/api/v1/authn"

Response 
{
  "expiresAt": "2015-11-03T10:15:57.000Z",
  "status": "SUCCESS",
  "sessionToken": "00Fpzf4en68pCXTsMjcX8JPMctzN2Wiw4LDOBL_9pe",
  "_embedded": {
    "user": {
      "id": "00ub0oNGTSWTBKOLGLNR",
      "passwordChanged": "2015-09-08T20:14:45.000Z",
      "profile": {
        "login": "dade.murphy@example.com",
        "firstName": "Dade",
        "lastName": "Murphy",
        "locale": "en_US",
        "timeZone": "America/Los_Angeles"
      }
    }
  }
}

```
* Overall we use okta widget for custom login [self hosted okta widget](https://developer.okta.com/docs/guides/custom-widget/main/ ) to get the session token which is ephemeral to get the session created  
* More help [here](https://github.com/okta/okta-signin-widget#spa-application) and [here](https://devforum.okta.com/t/custom-login-using-pkce-flow/7697/2)
* Flow is first to get the sessiontoken and then PKCE flow to get the access token , more details on the authorise endpoint [here](https://developer.okta.com/docs/reference/api/oidc/#authorize) 
* Use accesstoken [here](https://developer.okta.com/blog/2020/08/07/spring-boot-remote-vs-local-tokens) more details on [verify access token](https://developer.okta.com/docs/guides/validate-access-tokens/java/main/)
* 10 mins [widget](https://developer.okta.com/blog/2018/06/08/add-authentication-to-any-web-page-in-10-minutes)
* Claims permisssions and scope in access token [here](https://auth0.com/docs/secure/tokens/access-tokens/validate-access-tokens)
* Udemy Angular + springboot + Okta [here](https://tcsglobal.udemy.com/course/full-stack-angular-spring-boot-tutorial/learn/lecture/13616930#overview) and [here](https://tcsglobal.udemy.com/course/enterprise-oauth-for-developers/learn/lecture/24845718#overview)
* Sample Apigee integration [here](https://toolkit.okta.com/apps/generator-okta-oidc-apigee/) and [here](https://www.youtube.com/watch?v=SrNy7P6Atf8) and [opa](https://www.styra.com/blog/api-authorization-apigee-okta-opa-part-1/) and [here](https://github.com/apigee/apigee-okta) and [here](https://github.com/StyraInc/opa-apigee-demo)
