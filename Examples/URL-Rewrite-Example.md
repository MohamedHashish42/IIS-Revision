# URL Rewrite Example

Here's an example of how to configure a URL rewrite rule in IIS using the `web.config` file.  
This example demonstrates how to rewrite a URL to a different path within the same site.

## Example Scenario
Let's say you want to rewrite requests from `/old-page` to `/new-page`.


## web.config 
```xml
<configuration>
  <system.webServer>
    <rewrite>
      <rules>
        <rule name="Rewrite Old Page to New Page" stopProcessing="true">
          <match url="^old-page$" />
          <action type="Rewrite" url="/new-page" />
        </rule>
      </rules>
    </rewrite>
  </system.webServer>
</configuration>
```

### Explanation:
- **`<rewrite>`**: The section where rewrite rules are defined.
- **`<rules>`**: Container for one or more rewrite rules.
- **`<rule>`**: Defines a single rewrite rule.
  - **`name`**: A descriptive name for the rule.
  - **`stopProcessing`**: If set to `true`, no further rules will be processed if this rule matches.
- **`<match>`**: Defines the URL pattern to match.
  - **`url`**: The regular expression pattern to match the incoming request URL. In this case, it matches exactly 
  "old-page".  
  For example, it would match   
  **http://example.com/old-page**   
  but would not match   
  **http://example.com/old-page/subpage** or **http://example.com/new-old-page**
- **`<action>`**: Defines what action to take when the URL matches the pattern.
  - **`type`**: Specifies the type of action. In this case, "Rewrite" is used to rewrite the URL.
  - **`url`**: The target URL where the request should be rewritten.

### Usage
Place the above configuration in the `web.config` file at the root of your site or application. When someone visits `/old-page`, they'll be served content from `/new-page`.
