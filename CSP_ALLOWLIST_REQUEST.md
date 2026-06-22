Request: Add Power Platform domains to Content-Security-Policy connect-src

Hi Admin,

The published app at https://csusteph.github.io/ITProjectAutomation/ is blocked
from reaching Power Automate endpoints by the published host's Content-Security-Policy.
Preview works because the preview host does not apply the same CSP.

Please add the following to the server's `Content-Security-Policy` header `connect-src` directive
so the app can call Power Platform flows directly from the browser:

    Content-Security-Policy: connect-src 'self' https: https://*.powerplatform.com https://*.environment.api.powerplatform.com https://*.powerautomate.com https://*.logic.azure.com https://*.azure-apim.net;

If you prefer a minimal change, at least allow:

    https://*.environment.api.powerplatform.com

Notes:
- A CSP set via HTTP header on the host overrides any `<meta http-equiv="Content-Security-Policy">` in the page.
- Alternative: update the app to use the native SharePoint connector for the `IT Automation Project Request` list — connector traffic is allow-listed inside Power Platform and avoids cross-origin CSP issues.

Thanks,
IT Automation
