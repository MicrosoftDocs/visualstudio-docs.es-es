---
title: "Acerca de los lenguajes espec&#237;ficos de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio"
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 26
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 26
---
# Acerca de los lenguajes espec&#237;ficos de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A diferencia de un lenguaje de uso general como C\# o UML, un lenguaje específico \(DSL\) está diseñado para expresar instrucciones en un espacio del problema, o el dominio.  
  
 Expresiones regulares conocidas y SQL de inclusión del dominio \(ADSL\).  Cada DSL es mucho mejor que un lenguaje de propósito general para describir operaciones en cadenas de texto o una base de datos, pero mucho peor para describir las ideas que están fuera de su propio ámbito.  Las industrias individuales tienen su propio dominio \(ADSL\).  Por ejemplo, en la industria de las telecomunicaciones, los idiomas descriptivos de llamada son ampliamente utilizados especificar la secuencia de estados en una llamada telefónica, y en la industria de ciclos aérea una norma ADSL se utiliza para describir reservaciones del vuelo.  
  
 El negocio y el proyecto también se ocupan de conjuntos especiales de conceptos que se puede describir con ADSL.  Por ejemplo, podría definir un DSL para una de estas aplicaciones:  
  
-   Plan de rutas de navegación de un sitio Web.  
  
-   Esquemas eléctricos para componentes electrónicos.  
  
-   Redes de las bandas transportadoras y de equipaje que administran el equipo de un aeropuerto.  
  
 Cuando diseñe DSL, defina *una clase de dominio* para cada uno de los conceptos importantes en el dominio, como una página Web, una lámpara, o un mostrador de facturación de aeropuerto.  Al definir las *relaciones de dominio* como hipervínculo, conexión, o una banda transportadora para vincular los conceptos juntos.  
  
 Los usuarios ADSL crean *modelos.* Los modelos son *instancias* de ADSL.  Por ejemplo, describen un sitio Web concreto, o la conexión de un dispositivo determinado, o de equipaje controlando el sistema de un aeropuerto determinado.  
  
 Los usuarios pueden ver un modelo como diagrama o como Windows form.  Los modelos se pueden ver como XML, que es cómo se almacena.  Cuando se define un DSL, define cómo las instancias de cada clase y relación de dominio aparecen en la pantalla del usuario.  DSL normal se muestra como una colección de iconos o de rectángulos conectados mediante flechas.  
  
 La ilustración siguiente muestra un modelo en ADSL en forma de diagrama:  
  
 ![Modelo de árbol de familia Tudor](../modeling/media/tudor_familytreemodel.png "Tudor\_FamilyTreeModel")  
  
## Qué se puede hacer con el dominio \(ADSL\)  
 Una aplicación típica ADSL es generar código de programa u otros artefactos.  Cuando se define un DSL, puede definir *las plantillas de texto* que leen un modelo ADSL y generan archivos de texto.  
  
 Por ejemplo, podría escribir plantillas que toman un plan de aeropuerto y generan la parte del software del equipaje que administra, así como algunas documentos del usuario que describen el plan.  
  
 Cuando tenga definido un DSL, puede distribuirlo a otros usuarios que puedan instalarlo en sus propios equipos.  Los usuarios ADSL pueden crear y editar modelos en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 También puede definir los comandos de menú y otras herramientas que ayudan a los usuarios editar DSL, restricciones de validación de ayudar las plantillas asegúrese de que ADSL se utiliza correctamente, y elementos que ayudan a los usuarios a crear nuevas instancias.  Puede ajustar uno o más el dominio \(ADSL\) con sus herramientas y otras extensiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como paquete integrado.  
  
 Normalmente, se crea un lenguaje específico cuando un equipo de desarrollo tiene que escribir código similar para varios productos.  Por ejemplo, una compañía especializado en el equipaje que administra los sistemas podría definir una pista ADSL de equipaje de la que pueden generar parte de código para cada instalación.  Las ventajas de ADSL se pueden ser comprensible para los clientes, que el código generado de es confiable, y que el sistema se puede actualizar rápidamente si el cambio de los requisitos de clientes.  
  
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] permite crear un lenguaje específico de dominio que tenga poseer el diseñador gráfico y dispone de la notación del diagrama, y después utiliza el lenguaje para generar el código fuente adecuado para cada proyecto.  
  
## Desarrollo específico  
 el desarrollo específico es el proceso de identificar las partes de las aplicaciones que se pueden modelar mediante un lenguaje específico de dominio, y después de crear el lenguaje e implementarlo en los desarrolladores de aplicaciones.  Los desarrolladores utilizan el lenguaje específico para construir los modelos específicos de las aplicaciones, utilizan modelos para generar código fuente, y usan el código fuente para desarrollar aplicaciones.  
  
## Aspectos de desarrollo gráfico específico de dominio  
 Un lenguaje específico de gráfico debe incluir las siguientes características:  
  
-   Notation  
  
-   modelo de dominio  
  
-   Compilación de artefacto  
  
-   Serialización  
  
-   Integración con Visual Studio  
  
### Notation  
 Un lenguaje específico de dominio debe tener un conjunto razonablemente pequeño de elementos que pueden ser fácilmente definido y extendidos representar construcciones específicas.  Una notación consta de las formas, que representan los elementos, y conectores, que representan las relaciones entre los elementos, en una superficie gráfica del diagrama.  En [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], formas se pueden extender y refinar para representar los elementos de lenguaje específico.  
  
### modelo de dominio  
 Un lenguaje específico debe combinar el conjunto de elementos y relaciones entre ellas en una gramática coherente.  También debe definir si las combinaciones de elementos y relaciones son válidas.  Por ejemplo, los lenguajes de programación evitan normalmente herencia circular, donde la clase es derivada de una segunda clase y la segunda clase es derivada de primera clase.  Las restricciones se pueden utilizar para expresar la lógica de negocios, por ejemplo, una persona no puede ser un dependiente de.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utiliza restricciones para expresar las clases de restricciones que la mayoría de los lenguajes específicos necesarios.  
  
### Compilación de artefacto  
 Uno de los propósitos principales de un lenguaje específico del dominio es generar un artefacto, por ejemplo, código fuente, un archivo XML, o algún otro datos utilizable.  Normalmente, un cambio en el modelo significa un cambio en el artefacto.  Puede utilizar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar los artefactos y para regenerarlas cuando cambia el modelo.  
  
### Serialización  
 Un lenguaje específico de dominio se debe conservar en algún formulario que puede editarse, guardarse, cerrar, y se vuelva a cargar.  [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utiliza un formato XML que permite definir y personalizar cómo el lenguaje específico es serializado o conservado.  
  
### Integración con Visual Studio  
 Dado que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] se hospeda en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], extiende muchas ventanas y controles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  También le permite personalizar el comportamiento de los comandos de menú, elementos de cuadro de herramientas, y otros elementos de la interfaz de usuario.  
  
 También puede crear un adaptador modelo de bus del lenguaje específico.  Este adaptador permite hacer referencia a un modelo y los elementos dentro de un modelo, y le permite escribir código que tenga acceso y actualizar a una instancia de ADSL.  Mediante el mecanismo modelo eficaz de bus, puede escribir las extensiones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que ejecutan los varios modelos.  También puede escribir aplicaciones independientes que funcionan con modelos.  Para obtener más información, vea [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## Ventajas de desarrollo específico de dominio  
 Un lenguaje específico puede proporcionar las siguientes ventajas:  
  
-   Contiene las construcciones que se ajuste a exactamente el espacio del problema.  
  
     A diferencia de lenguajes de uso general, un lenguaje específico consta de los elementos y las relaciones que representan directamente la lógica del espacio del problema.  Por ejemplo, una aplicación de la póliza de seguros debe incluir los elementos para las directivas y las peticiones.  Un lenguaje específico facilita diseñar la aplicación, y encuentra y corregir errores de lógica.  
  
-   Permite a los no\-desarrolladores de software y las personas que no conocen el dominio entienden el diseño global.  
  
     Mediante un lenguaje específico del gráfico, puede crear una representación visual del dominio de modo que los no\-desarrolladores de software pueden fácilmente entender el diseño de la aplicación.  
  
-   Facilita la creación un prototipo de la aplicación final.  
  
     Los desarrolladores pueden utilizar el código que el modelo genera para crear una aplicación de prototipo que pueden mostrar a los clientes.  
  
## El proceso de desarrollo específico de dominio  
 La mayoría de los equipos de desarrollo de software que utilizan lenguajes específicos de dominio siga estos pasos para crear y utilizar los modelos:  
  
-   El equipo distingue las partes variables del dominio de los elementos que no cambian.  
  
-   Los desarrolladores escriben el código para las partes fijas y los puntos de extensión de licencia para las partes variables.  
  
-   El desarrollador de software iniciales o el arquitecto crea un lenguaje específico que escriba los modelos de diseño de las partes fijas de dominio y la extensión designado para las partes variables.  
  
-   El desarrollador de software iniciales o el arquitecto implementa el lenguaje específico a los desarrolladores las aplicaciones diferentes que el equipo genera.  
  
-   Cada desarrollador crea un modelo que se aplican a la aplicación concreta.