> :rocket: **Try it for free** in the new Phase Two [keycloak managed service](https://phasetwo.io/dashboard/?utm_source=github&utm_medium=readme&utm_campaign=keycloak-theme-template). See the [announcement and demo video](https://phasetwo.io/blog/self-service/) for more information.

# Example themes

This is a repository of example CSS-only themes that can be be used in Phase Two's enhanced Keycloak without installing a custom library.

## tl;dr

The 3 example CSS themes:
- Consumer [consumer/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/consumer/login/resources/css/consumer/login.css)
- Enterprise [enterprise/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/enterprise/login/resources/css/enterprise/login.css)
- SaaS [saas/login.css](https://github.com/p2-inc/keycloak-theme-template/blob/master/src/main/resources/theme/saas/login/resources/css/example/login.css)

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
