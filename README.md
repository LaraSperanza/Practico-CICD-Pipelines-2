Crear un flujo CI/CD en Github Actions que se autentique en AWS mediante OIDC (sin llaves estáticas) para subir un archivo a S3. El workflow debe ejecutarse automáticamente al realizar un push al branch principal (y de forma manual por workflow_dispatch), consumir un Environment para imprimir los secrets y variables dentro del archivo generado para subir a s3. 
El flujo debe:
 (1) asumir un role en AWS un usando aws-actions/configure-aws-credentials@v4,
 (2) crear un archivo de salida que incluya el valor del Secret y metadatos de la ejecución, (timestamp por ej)
 (3) El rol debe filtrar, como mínimo, por aud = sts.amazonaws.com y por el repositorio.
Se deberá tener en cuenta que la autenticación por OIDC permitan exclusivamente las acciones necesarias sobre el bucket/prefijo definidos(iam policy), que el objeto se cree correctamente en S3 con el contenido esperado. Tambien que el workflow consuma el Environment configurado y que todo el flujo se ejecute al detectar cambios en el código fuente(push). 
