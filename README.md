# getSAMLInteractive

A set of tools which will allow you to interactively authenticate with a SAML IDP, even if MFA is enabled, and retrieve the SAML Response. SAML Response can then be passed to another app or module for authenticating user. 

Initially created for psPAS CyberArk module, providing a secure and user-friendly way to authenticate to the CyberArk REST API.

# PowerShell Module
The PowerShell module located within folder "PowerShell New-SAMLInteractive Module" is the original incarnation of this project. Module continues to work but does have some limitations, as it it uses the built-in Windows web framework. This framework is based on Internet Explorer, so modern authentication methods likesFIDO2 are not possible.

# getSAMLResponse Executable (New)
The latest version of the project. Built from scratch, this version is built on webView2 (Edge web technology) using C#. Using webView2 modern authentication is now possible, allowing users to use Fido keys, such as a YubiKey. Providing stronger and more convenient authentication options.

Source code for this version can be found in folder "webView2 Modern Source".

You can also download the pre-built binary. This is built specifically with the CyberArk API in mind, for other apps you will need to download from source and build.

### How to use binary ###
Like the PS module you simply need to call executable and pass the IDP sign in URL for your app e.g., CyberArk PVWA. 
Once auth is complete the response if written out to the command line or to the variable assigned.

```
$loginResponse = .\getSAMLResponse.exe $LoginIDP

```

### Testing ###
Tested with Okta and Azure AD with CyberArk PAM v12 and v13.
