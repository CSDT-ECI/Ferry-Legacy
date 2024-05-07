# Proyecto Curso: Deuda técnica en procesos
1. _Configurar un proceso de IC utilizando github actions con steps que incluyan mínimo:_
  - Build
  - Unit test
  - Code Analysis (Reportando en Sonar)
2. _Incluir algún step adicional que consideren pueden generar valor para su proyecto, por ejemplo: ChatOps (Teams, slack), bot de github, Owasp, dependecy check, AI. Bienvenida la imaginación._
3. _Documentar en la bitácora del proyecto_

## Configuración Git Actions & SonarCloud 🚀

### Creación de Archivo YML Build , unit test y Sonarcloud
#### **SonarCloud** : 
- Iniciaremos sesión en SonarCloud con nuestro GitHub , en este caso como no tenemos permisos de la organización para crear un pipeline, clonaremos el repo y lo analizaremos en la cuenta personal:
Una vez iniciada sesión crearemos un nuevo proyecto a analizar : 
![actions1](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/c982611b-c3fc-46e6-b8d9-a041d34412ec)

- Seleccionamos el repo y procedemos a configurarlo : 
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/884798db-0251-4179-af3e-21dd56e2e795)
- Tenemos que crear un secreto de github en nuestro repo para que SonarCloud tenga acceso a nuestro proyecto , dentro de este pegamos el token generado:
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/81b32fe2-7e71-45b8-86d9-2a500836cbd0)
- En nuestro caso el proyecto está estructurado con Gradle , asi que debemos modificar el build.gradle con el pluggin de SonarCloud
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/971de941-6dbe-4467-9f16-c7b8fa269b18)
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/b0f093d9-bb88-4f68-826e-ea2abbbc601b)
- Ahora tenemos que modificar o crear un Archivo YML para nuestras GitActions y modificarlo de la siguiente manera:
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/706ad827-3382-4c6a-986a-1b3728d8d2c0)
- Como podemos ver este ya nos trae un Job BUILD que se requiere en los items de entrega , adicionalmente debemos añadir un job para los test unitarios :
agregamos la configuración que propone SonarCloud:
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/e4d4eeae-4e4c-4929-842e-336e71d28532)
- Añadimos un trabajo para los test y adicionamos un job Dependency check. La acción OWASP/Dependency-Check_Action genera informes de análisis de dependencias en varios formatos. Cuando se configura el parámetro format: 'ALL', se generan informes en todos los formatos disponibles. Los formatos disponibles son: XML , HTML , JSON , entre otros  
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/4b249fcd-287b-4def-bb9b-bb11c4daf227)
- Una vez terminado compilamos y tenemos el siguiente error, el cual indica que la versión de GRADLE del proyecto es bastante antigua para usar JAVA 17 , por lo que tenemos que migrar a una versión más actualizada.
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/e970360b-afe7-47fb-958a-df7669eaa410)
- La actualizamos : 
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/ab3deca4-2e9a-4dbe-8eef-ac943807f826)
- volvemos a correr las actions . Al parecer la estructura de los test que tiene el proyecto no es correcta para el JOB de los test , revisando el proyecto más a fondo estos test poseen errores de importación imposibilitanto que estos puedan correr : 
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/ad1fdac4-22c2-4f66-a83d-8b6d28298b39)
- Desahbilitaremos por un momento el job de test: 
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/a0d5b7c7-d968-4b67-8d26-27e2443876ad)
- concluimos que el proyecto aun posee errores que al intentar compilarse estos generan excepciones provocando que el analisis del proyecto no conluya debido a que este no compila.

