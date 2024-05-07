# Proyecto Curso: Architectural Debt (Parte 1)
_Teniendo en cuenta los enfoque vistos en clase:_
1. _identificar algunos Architectural Smells_
2. _documentar en un archivo ArchitecturalSmells.md (integrando con la versión unificada del proyecto)_
3. _debe identificar y documentar adecuadamente algunas malas prácticas de arquitectura. Puede utilizar las referencias recomendadas o alguna otra que considere._


## Herramienta de Análisis Designite 🚀
_Designite es una herramienta de análisis de código y calidad de software que permite identificar y resolver problemas de calidad en el proyecto. Proporciona una serie de características útiles, incluyendo la detección de "olores de código", "olores de arquitectura" y "olores de implementación", que son patrones problemáticos en el diseño y la implementación del software._

_Designite puede analizar código en varios lenguajes, incluyendo C# y Java, lo que lo hace adecuado para este proyecto. Identificar problemas potenciales en el módulo de C# y Java es el objetivo, como dependencias cíclicas, complejidad excesiva, duplicación de código, entre otros. Además, Designite proporciona visualizaciones útiles para entender la estructura y la calidad de el código.
Para usar Designite en el proyecto, se debe instalar las 2 versiones de la herramienta, una para java y otra para C#._
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/b6bff503-48e3-4726-870b-9c2f5eace87f)


### Analisis del proyecto
_El proyecto está estructurado por 2 modulos, uno de java y otro de C#, debido a esto debemos instalar 2 versiones diferentes de la herramienta para cada modulo en especifico:_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/97437a68-c215-4e60-af2f-b61d37b7ac7a)
#### Analisis C# :
_La interfaz de la aplicación se ve de esta manera, realizaremos un analisis de solución_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/c51dfe54-9c64-4804-811a-a1ac22174055)
_El análisis de solución en este contexto se refiere a la acción de examinar y evaluar la estructura y el contenido de una solución de Visual Studio. Esto puede implicar la revisión de los proyectos individuales, las dependencias entre ellos, la configuración de la solución y otros aspectos. Esto se analiza desde un archivo .sln generado automaticamente por VisualStudio_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/6eb806ea-e9c7-4cc4-8aa6-4920bc715079)
_Una vez cargado el archivo .sln la aplicación reconoce el proyecto , procederemos a analizarlo_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/5369fd36-1d1d-416a-aeb9-bc5bb16c6071)
_La herramienta nos hace un analisis de el proyecto , en este caso analizó todo el modulo de C# , aqui se proponen los arquitecture smells , Design Smells e implementation Smells , adicionalmente se propone un apartado de HotSpots para revisar rapidamente las clases que tienen smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/2caa256e-8414-4148-8633-68510b6c1f4b)
_Según la herramienta no se evidenciaron Arquitecture smells, recuerde que este es el análisis para el modulo C# , revisemos las otras metricas_
_Aqui tenemos el apartado de Design smells, hay diferentes Smells detectados y estos se representan con colores, como podemos observar en la parte exterior del circulo están de manera filtrada por clases los smells detectados_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/e30fa4ca-88bb-4c2e-a622-70df67b4fe31)
_Aqui nos especifica en que parte de la clase está siendo detectado los smells por cada clase_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/cc468bb0-830d-41f4-8198-1d56ded55a50)
_Aqui el Smell de modularidad y nos especifica en que parte de la clase está siendo detectado el smell_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/75991df2-82e0-426f-b31f-8a8bff09e6c5)
_Ahora analicemos el siguiente apartado, Implementation smells se identifica solo uno que es el Magic Number este se localiza en 25 issues._
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/9e05d2cb-d970-492a-81ac-923bdb71bd08)
_Finalmente aqui encontramos un resumen o una forma rapida de identificar todos los smell codes por clases_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/4966248f-ef77-454b-b652-7326717057d2)
#### Analisis Java :
_Para el analisis de este debemos usar la terminal de comandos , primero colocamos el .jar descargado en una nueva carpeta y abrimos la terminal de comandos en este directorio_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/7bb2eb72-31f1-4d9b-a94d-ed4a290d0e0b)
_Ahora revisando la documentación debemos usar el siguiente comando para generar un analisis : "java -jar DesigniteJava.jar -i <path of the input source folder> -o <path of the output folder> -d"_
_Modificamos el input con el directorio del modulo java y el output con un directorio donde almacenar el análisis_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/83488469-2622-440e-b000-b08c95a6bb65)
_El analisis ya fue generado y podemos encontrarlo en el directorio que especificamos, se generan archivos XML, donde a manera de tablas se especifican estos smells._
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/50c8a17d-a70b-4179-84c6-c7d70a59029f)
_Revisamos cada archivo con excel ya que está en formato CVS, iniciamos con los Arquitecture Smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/94bf89a5-7049-45be-ba92-aad54f177465)
_Como podemos observar el archivo está vacio por lo que no se dectectaron Olores en la arquitectura, revisemos el siguiente archivo : Design Smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/0545ac9f-ae46-4221-a7c0-8d16cba16273)
_En este archivo contienen los Olores de diseño filtrados en una tabla indicando , el proyecto , la clase , el olor de diseño y su razón, entre estos encontramos olores en abstracción, Encapsulamiento y Modularización , sigamos con el archivo de Implementation Smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/6e046bc8-23f8-40f5-9300-5db90fc1fc21)
_Aqui se especifican los olores de implementación en los metodos de las clases citadas , adicionalmente se otorga el tipo de olor y la razón por la cual está siendo detectado, A diferencia del analisis de C# obtenemos un nuevo olor que es Long Statement ,lo que significa que este metodo está generando valores muy largos y esto puede ser debido a que no tiene una unica responsabilidad, abramos el archivo que sigue, Testability Smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/bcde2f78-9205-4a40-90c1-80c509038674)
_Se analizan las clases y se logra evidenciar que algunas de ellas las cuales están listadas pertenecen a un grupo donde tienen demasiadas dependencias y se listan cuantas exactamente están siendo usadas._
_Finalmente miremos el ultimo archivo relacionado al analisis del proyecto , Test Smells_
![image](https://github.com/CSDT-ECI/Juan_alvarez_Ferry-Legacy/assets/98127586/d30e0ece-bbc5-4f33-8714-71987c8ad325)
_En este analisis los test que se tienen son evaluados y se listan los que posean Smells, en este caso se listan 3 los cuales tienen el Smell "Assertion Rulette" el cual ocurre cuando se hacen multiples assertions sin documentar haciendo que sea demasiado dificil encontrar el porque de el test falle o su refactorización futura._










