# PS-SAML-Interactive

A PowerShell module which allows you to interactively authenticate to your SAML IDP, including most MFA options, and return the SAML Response for use in other calls.

Primary use case for creation is the CyberArk PAS API but can be utilised by any service that uses a SAML response to authenticate.

# Usage

1. Import the module
2. Pass the login URL for a federated app, typically the URL for an IDP initiated login
3. Form will open, login to your SAML IDP as normal
4. SAML Response returned


### Example: ###

```
import-module -name 'C:\PS-SAML-Response.ps1'

$LoginURL = 'https://myapps.microsoft.com/signin/App1/2aba-4df5-8fc2-cdf9034d7191?tenantId=-d5be-49ea-j988-fdd74c91f8ad'

New-SAMLInteractive -LoginIDP $LoginURL
```

![LoginExample](https://user-images.githubusercontent.com/17259178/124187208-64340a80-dab5-11eb-884b-ef581cf1007c.gif)


### MFA ###
Most MFA solutions used by IDPs will be supported e.g. Push Authentication or OTP.
Some forms of MFA will not work, these include FIDO and WebAuthN (FIDO2).

Not tested = PIV smart card auth
