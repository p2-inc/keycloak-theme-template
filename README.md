# keycloak-theme-template

Base template for developing a Keycloak theme.

## Developing custom Keycloak themes

  * Create a folder for your custom theme within the ``src/main/resources/themes`` directory, if one does not already exist. 
  * Then add a subdirectory for the theme type (e.g. ``admin``, ``login``, etc.).
  * Modify any of the files within your custom theme directory. Assuming you are extending the ``base`` or ``keycloak`` theme, you only need to override the files you want to change.
  * To easily iterate without having to restart the server every time, load keycloak using `start-dev` with the included docker-compose file caching off: `docker-compose up`

## Testing your theme

  * Login to the admin console at `http://localhost:8080/auth/admin` with `admin:admin`
  * Go into `Realm Settings`->`Themes` and select the theme you are working on (e.g. Login->example)
  
## Packaging the theme for deployment

  * Run `mvn package` to build a jar that can be placed in the `provider` (Quarkus) or `standalone/deployments` (Wildfly) directory of your Keycloak installation.
