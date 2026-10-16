<!-- phasetwo:banner:start - managed by p2-inc/shared-github-actions, edit there -->
[![license](https://img.shields.io/badge/license-Apache--2.0-blue)](COPYING) [![docs](https://img.shields.io/badge/docs-phasetwo.io-blue)](https://phasetwo.io/docs/getting-started/customizing-ui/)

📚 [Documentation](https://phasetwo.io/docs/getting-started/customizing-ui/) • 🚀 [Hosted Keycloak](https://dash.phasetwo.io/?utm_source=github&utm_medium=readme&utm_campaign=keycloak-theme-template) • 🤖 [Keycloak Skills](https://github.com/p2-inc/keycloak-skills) • 💬 [Support](mailto:support@phasetwo.io)

> [!TIP]
> **Run this in our cloud, no setup needed.** Phase Two hosts Keycloak with all of our extensions built in. [Try it free with your own cluster →](https://dash.phasetwo.io/?utm_source=github&utm_medium=readme&utm_campaign=keycloak-theme-template)
>
> **Using a coding agent?** Add the Phase Two Keycloak skills ([launch post](https://phasetwo.io/blog/keycloak-skills-mcp-launch)) to Claude Code, Cursor or Codex so your agent can set up passwordless login, SSO, organizations and clusters for you:
>
> ```sh
> # Install the skills (connects to our hosted MCP server)
> claude plugin marketplace add p2-inc/keycloak-skills
> claude plugin install phasetwo@keycloak-skills
> # Or connect to the MCP server directly
> claude mcp add --transport http keycloak https://mcp.phasetwo.io/mcp
> ```
<!-- phasetwo:banner:end -->

This repository contains examples for developing a Keycloak login theme locally. You can use the examples directly, customize them and package them with the included Maven project, or use the CSS directly if you are using the [Phase Two Themes extension](https://github.com/p2-inc/keycloak-themes).

## Sample themes

The 3 example CSS themes that can be be used in Phase Two's enhanced Keycloak without installing a custom library:
- Consumer [consumer/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/consumer/login/resources/css/consumer/login.css)
- Enterprise [enterprise/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/enterprise/login/resources/css/enterprise/login.css)
- SaaS [saas/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/saas/login/resources/css/saas/login.css)

Look at the [article](https://phasetwo.io/blog/customizing-login-pages) for more information on using the CSS directly with the [Phase Two Themes extension](https://github.com/p2-inc/keycloak-themes).

Install them in the Phase Two Admin UI console by navigating to the **Styles** section and selecting the **Login** tab. Paste the style into the *CSS* field and click *Save*.
![Screenshot from 2023-01-12 21-20-30](https://user-images.githubusercontent.com/244253/212172497-0b8f3548-cbc3-49b1-9d20-65d631b7baa2.png)

You must have the `Attributes` login theme selected in **Realm settings** -> **Themes** for the changes to take effect.
![Screenshot from 2023-01-12 21-18-58](https://user-images.githubusercontent.com/244253/212172476-3266318a-358c-452e-ade3-746a0787bb69.png)

## Keycloak theme template

You can also use these as base template for developing a Keycloak theme locally.

### Developing custom Keycloak themes

  * Create a folder for your custom theme within the ``src/main/resources/themes`` directory, if one does not already exist. 
  * Then add a subdirectory for the theme type (e.g. ``admin``, ``login``, etc.).
  * Modify any of the files within your custom theme directory. Assuming you are extending the ``base`` or ``keycloak`` theme, you only need to override the files you want to change.
  * To easily iterate without having to restart the server every time, load keycloak using `start-dev` with the included docker-compose file caching off: `docker compose up`

### Testing your theme

  * Login to the admin console at `http://localhost:8080/auth/admin` with `admin:admin`
  * Go into `Realm Settings`->`Themes` and select the theme you are working on (e.g. Login->example)
  
### Packaging the theme for deployment

  * Run `mvn package` to build a jar that can be placed in the `provider` (Quarkus) or `standalone/deployments` (Wildfly) directory of your Keycloak installation.
