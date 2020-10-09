
# SonarQube en Windows

1. Descargar la versión de java desde [aquí](https://www.java.com/en/download/) ya que SonarQube esta hecho en este lenguaje.
2. Instalar java
3. Agregar el directorio bin ubicado en la instalación de java a las variables de entorno
4. Descargar SonarQube community desde [aquí](https://www.sonarqube.org/downloads/)
5. Descomprimir SonarQube (preferiblemente en la raíz del sistema c:/)

## Ejecutar SonarQube

1. Abrir una terminal
2. Ir al directorio \bin\windows-x86-64 donde esta SonarQube
3. Ejecutar el archivo StartSonar.bat desde la consola

Si todo ha ido bien cuando finalice de levantarse el servicio de SonarQube podríamos ver la plataforma de SonarQube en la url http;//localhost:9000. Los datos de autenticación son user: admin
password: admin

Para poder el análisis de un proyecto debemos crear uno en la plataforma de SonarQube y seguir los siguientes pasos para obtener el análisis

### .Net Clasico
Para usar SonarQube con .Net Clasico debemos descargar la herramienta [SonnarScaner for MSBuild](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-msbuild/)

1. Descomprimir SonarScanner (preferiblemente en la raíz del sistema c:/)
2. Modificar el archivo SonarQube.Analysis.xml agregando los datos de acceso a SonarQube
3. En la plataforma de SonarQube generar un token para el proyecto creado anteriormente
4. Abrir una terminal
5. Ubicarse en la raíz del proyecto a analizar
6. Ejecutar SonarScanner a través del siguiente comando:
- `C:/Sonar/Scanner/SonarScanner.MSBuild.exe begin /k:"[Proejct Name]" /d:sonar.host.url="http://localhost:9000" /d:sonar.login="[Give your project token ]"`
- `MsBuild.exe /t:Rebuild`
- `SonarScanner.MSBuild.exe end /d:sonar.login="Give your project token"`

Después que termine, vamos al dashboard de SonarQube y veremos lo que arrojó el análisis.
    
