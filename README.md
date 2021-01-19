# keycloak-theme-template

Base template for developing a Keycloak theme.

## Developing custom Keycloak themes

  * Create a folder for your custom theme within the ``src/main/resources/themes`` directory, if one does not already exist. 
  * Then add a subdirectory for the theme type (e.g. ``admin``, ``login``, etc.).
  * Modify any of the files within your custom theme directory. Assuming you are extending the ``base`` or ``keycloak`` theme, you only need to override the files you want to change.
  * To easily iterate without having to restart the server every time, load keycloak from docker with a script that turns theme caching off:
  ```
  docker run --name keycloak-theme -d -p 9000:8080 -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin --mount type=bind,source=$(pwd)/src/main/resources/theme/example/,target=/opt/jboss/keycloak/themes/example -v $(pwd)/docker/no-cache-theme.cli:/opt/jboss/startup-scripts/no-cache-theme.cli jboss/keycloak:12.0.2
  ```

## Packaging the theme for deployment

  * Run `mvn package` to build a jar that can be placed in the `standalone/deployments` directory of your Keycloak installation.
