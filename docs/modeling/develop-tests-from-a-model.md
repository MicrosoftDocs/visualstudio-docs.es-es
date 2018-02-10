---
title: Desarrollar pruebas en un modelo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- tests and requirements
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a2937edee2040d8e48938b9cbbf8e78e48780884
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="develop-tests-from-a-model"></a>Desarrollar pruebas en un modelo
Puede usar modelos arquitectónicos y modelos de requisitos que le ayuden a organizar las pruebas del sistema y sus componentes. Con esta práctica, tendrá la certeza de que incluye en la prueba los requisitos que son importantes para los usuarios y otras partes interesadas, y podrá actualizar las pruebas rápidamente cuando cambien los requisitos. Si usa [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], también puede mantener vínculos entre los modelos y las pruebas.  
  
 Para ver qué versiones de Visual Studio admite estas características, vea [compatibilidad con la versión de arquitectura y herramientas de modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="system-and-subsystem-testing"></a>Pruebas del sistema y de los subsistemas  
 *Pruebas del sistema,* también conocido como *las pruebas de aceptación*, significa que prueba si se satisfacen las necesidades de los usuarios. En lugar de comprobar el diseño interno, estas pruebas se centran en el comportamiento del sistema que se aprecia desde el exterior.  
  
 Las pruebas del sistema son muy útiles cuando se amplía o rediseña un sistema, y ayudan a evitar que introduzca errores al cambiar el código.  
  
 Cuando tiene previsto realizar cambios en un sistema o ampliarlo, es útil empezar con un conjunto de pruebas del sistema que se ejecuten en el sistema actual. Después podrá ampliar o ajustar las pruebas para probar los nuevos requisitos, realizar cambios en el código y volver a ejecutar el conjunto completo de pruebas.  
  
 Cuando desarrolla un nuevo sistema, puede empezar a crear pruebas desde las primeras fases de desarrollo. Si define las pruebas antes de desarrollar cada característica, podrá recopilar las discusiones sobre los requisitos de una manera muy específica.  
  
 En las pruebas de los subsistemas se aplican los mismos principios a los componentes principales de un sistema. Cada componente se prueba por separado de los otros componentes. Las pruebas de los subsistemas se centran en el comportamiento visible de las interfaces de usuario o la API de los componentes.  
  
## <a name="deriving-system-tests-from-a-requirements-model"></a>Derivar pruebas del sistema de un modelo de requisitos  
 Puede crear y mantener una relación entre las pruebas del sistema y un modelo de requisitos. Para establecer esta relación, escriba las pruebas que correspondan a los elementos principales del modelo de requisitos. Visual Studio le permitirá crear vínculos entre las pruebas y los elementos del modelo para ayudarle a mantener esa relación. Para obtener más información acerca de los modelos de requisitos, consulte [modelar los requisitos de usuario](../modeling/model-user-requirements.md).  
  
### <a name="write-tests-for-each-use-case"></a>Escribir pruebas para cada caso de uso  
 Si usa [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)], puede crear un grupo de pruebas para cada caso de uso definido en el modelo de requisitos. Por ejemplo, si tiene un caso de uso para pedir un menú que incluye crear un pedido y agregar un elemento al pedido, puede crear pruebas tanto para el caso general como para los casos de uso más detallados. 
  
 Estas directrices pueden resultar útiles:  
  
-   Cada caso de uso debería tener varias pruebas, tanto para las operaciones principales como para los resultados excepcionales.  
  
-   Al describir un caso de uso del modelo de requisitos, es más importante definir su condición posterior, es decir, el objetivo que se consigue, que describir en detalle los procedimientos que el usuario sigue para lograr el objetivo. Por ejemplo, la condición posterior de pedir un menú podría ser que un restaurante prepare una comida para un cliente y que el cliente pague. La condición posterior es el criterio que las pruebas deben comprobar.  
  
-   Cree pruebas independientes basadas en las distintas cláusulas de la condición posterior. Por ejemplo, cree pruebas distintas para notificar el pedido al restaurante y para realizar el pago del cliente. Esta separación tiene las siguientes ventajas:  
  
    -   Los cambios en los distintos aspectos de los requisitos suelen producirse de forma independiente. Al dividir las pruebas en diferentes aspectos de esta manera, resulta más sencillo actualizar las pruebas cuando cambian los requisitos.  
  
    -   Si el plan de desarrollo implementa un aspecto del caso de uso antes que otro, puede habilitar las pruebas de forma independiente a medida que progresa el desarrollo.  
  
-   Cuando diseñe las pruebas, separe los datos de la prueba que ha elegido del código o del script que determina si se ha logrado la condición posterior. Por ejemplo, la prueba de una función aritmética sencilla podría ser: escribir 4; comprobar que el resultado es 2. En lugar de ello, diseñe el script del siguiente modo: elegir una entrada; multiplicar la salida por sí misma y comprobar que el resultado es la entrada original. Este estilo permite variar las entradas de prueba sin cambiar el cuerpo principal de la prueba.  
  
#### <a name="linking-tests-to-use-cases"></a>Vincular pruebas a casos de uso  
 Si utilizas [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] para diseñar y ejecutar las pruebas, puede organizar las pruebas en el requisito, caso de uso o los elementos de trabajo de caso de usuario. Puede vincular estos elementos de trabajo a casos de uso en el modelo. Esto le permite realizar un seguimiento rápido de los cambios en los requisitos de las pruebas y le ayuda a supervisar el progreso de cada caso de uso.  
  
###### <a name="to-link-tests-to-a-use-case"></a>Para vincular las pruebas a un caso de uso  
  
1.  En [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], cree un requisito y base en él un conjunto de pruebas.
  
     El requisito que cree será un elemento de trabajo de [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Puede ser un elemento de trabajo de caso de usuario, requisito o caso de uso según la plantilla de proceso que use el proyecto con [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obtener más información, consulte [seguimiento del trabajo mediante Visual Studio Team Services o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule el elemento de trabajo de requisito a uno o varios casos de uso del modelo.  
  
     En un diagrama de casos de uso, haga clic en un caso de uso y, a continuación, haga clic en **vínculo al elemento de trabajo**. 
  
3.  Agregue casos de prueba que comprueben los casos de uso al conjunto de pruebas.  
  
 Normalmente, cada elemento de trabajo de requisito o caso de usuario se vinculará a varios casos de uso en el modelo y cada caso de uso se vinculará a varios casos de usuario o requisitos. Esto ocurre porque cada caso de usuario o requisito comprende un conjunto de tareas que desarrollan varios casos de uso. Por ejemplo, en una iteración temprana del proyecto, podría desarrollar el caso de usuario básico en el que un cliente puede seleccionar elementos de un catálogo y recibirlos. En una iteración posterior, el caso podría ser que el usuario paga al completar el pedido y el proveedor recibe el dinero después de enviar los productos.  Cada caso agrega una cláusula a la condición posterior del caso de uso de pedir artículos.  
  
 Puede crear vínculos independientes desde los requisitos a las cláusulas de la condición posterior escribiendo estas cláusulas en comentarios independientes en el diagrama de casos de uso. Puede vincular cada comentario a un elemento de trabajo de requisito y vincular el comentario al caso de uso en el diagrama.  
  
### <a name="base-tests-on-the-requirements-types"></a>Cree pruebas basadas en los tipos de requisitos  
 Los tipos, es decir, las clases, interfaces y enumeraciones de un modelo de requisitos describen los conceptos y relaciones en términos de cómo los usuarios conciben y transmiten el concepto de su negocio. Se excluyen los tipos que se ocupan únicamente del diseño interno del sistema.  
  
 Diseñe las pruebas atendiendo a estos tipos de requisitos. Esta práctica ayuda a garantizar que, cuando se analizan los cambios en los requisitos, resulte fácil relacionar estos cambios con los cambios necesarios en las pruebas. Es posible estudiar las pruebas y sus resultados deseados directamente con los usuarios finales y otras partes interesadas. Esto significa que es posible mantener las necesidades de los usuarios fuera del proceso de desarrollo, lo cual evita que las pruebas se diseñen por error en torno a posibles errores de diseño.  
  
 Para las pruebas manuales, esta práctica implica seguir el vocabulario del modelo de requisitos de los scripts de prueba. En las pruebas automatizadas, esta práctica implica usar los diagramas de clases de requisitos como base para el código de prueba y crear funciones de descriptor de acceso y actualizador para vincular el modelo de requisitos al código.  
  
 Por ejemplo, un modelo de requisitos puede incluir los tipos Menú, Elemento de menú, Pedido y las asociaciones que hay entre ellos. Este modelo representa la información que el sistema de pedidos de comida almacena y administra, pero no representa las complejidades de su implementación. En el sistema activo podría haber realizaciones diferentes de cada tipo en bases de datos, interfaces de usuario y varias API. En un sistema distribuido es posible que haya distintas variantes de cada instancia almacenadas en diferentes partes del sistema al mismo tiempo.  
  
 Para probar un caso de uso como el de agregar un elemento al pedido, un método de prueba podría incluir código similar a este:  
  
```  
Order order = ... ; // set up an order  
// Store prior state:  
int countBefore = order.MenuItems.Count;   
// Perform use case:  
MenuItem chosenItem = ...; // choose an item  
AddItemToOrder (chosenItem, order);   
// Verify part of postcondition:  
int countAfter = order.MenuItems.Count;  
Assert (countAfter == countBefore = 1);   
```  
  
 Fíjese en que este método de prueba usa las clases del modelo de requisitos. Las asociaciones y los atributos se realizan como propiedades de. NET.  
  
 Para que esto funcione, las propiedades de las clases deben definirse como funciones de solo lectura o descriptores de acceso que tengan acceso al sistema para recuperar información sobre su estado actual. Los métodos que simulan casos de uso, como AddItemToOrder, deben dirigir el sistema a través de su API o a través de una capa debajo de su interfaz de usuario. Los constructores de objetos de prueba, como Order y MenuItem, también deben controlar el sistema para crear los elementos correspondientes dentro del sistema.  
  
 Muchos de los descriptores de acceso y actualizadores ya estarán disponibles a través de la API normal de la aplicación. Pero, para habilitar las pruebas, es posible que tenga que escribir algunas funciones adicionales. Estos descriptores de acceso adicionales y actualizadores a veces se conocen como “instrumentación de pruebas”. Dado que dependen del diseño interno del sistema, proporcionarlos es responsabilidad de los desarrolladores del mismo, mientras que los evaluadores escriben el código de las pruebas en términos del modelo de requisitos.  
  
 Al escribir pruebas automatizadas, puede usar pruebas genéricas para encapsular los descriptores de acceso y actualizadores.
  
### <a name="tests-for-business-rules"></a>Pruebas para reglas de negocios  
 Algunos requisitos no están relacionados directamente con ningún caso de uso. Por ejemplo, el negocio DinnerNow permite a los clientes elegir entre un gran número de menús pero requiere que en cada pedido todos los elementos elegidos provengan de un único menú. Esta regla de negocios puede expresarse como una invariante acerca de las asociaciones entre pedidos, menús y elementos en el modelo de clase de requisitos.  
  
 Una regla invariable de este tipo rige no sólo todos los casos de uso que están definidos actualmente, sino también los casos de uso que se definirán en el futuro. Por lo tanto, resulta útil escribirla por separado de cualquier caso de uso y probarla independientemente de los casos de uso.  
  
## <a name="deriving-subsystem-tests-from-models"></a>Derivar pruebas de subsistemas a partir modelos  
 En el diseño de alto nivel de un sistema grande, puede identificar componentes o subsistemas. Se trata de componentes que pueden diseñarse de forma independiente o que se encuentran en equipos distintos o son módulos reusables que pueden combinarse de muchas maneras. 
  
 Puede aplicar a cada componente principal los mismos principios que usa para todo el sistema. En un proyecto grande, cada componente puede tener su propio modelo de requisitos. En proyectos más pequeños, se puede crear un modelo arquitectónico o un diseño de alto nivel para mostrar los principales componentes y sus interacciones. Para obtener más información, consulte [modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md).  
  
 En cualquier caso, puede establecer una relación entre los elementos del modelo y las pruebas del subsistema del mismo modo que puede hacerlo entre el modelo de requisitos y las pruebas del sistema.  
  
### <a name="isolate-components-with-provided-and-required-interfaces"></a>Aislar componentes con interfaces proporcionadas y necesarias  
 Resulta útil para identificar todas las dependencias que un componente tiene sobre servicios externos u otras partes del sistema y representarlas como interfaces necesarias. Este ejercicio normalmente lleva a un rediseño que hace que el componente quede mucho más desacoplado y fácil de separar del resto de su diseño.  
  
 Una ventaja de esta desvinculación es que el componente se puede ejecutar para probarlo reemplazándolo con objetos ficticios que normalmente usan los servicios. Estos son los componentes que se han configurado para los propósitos de pruebas. Un componente ficticio proporciona la interfaz que requiere el componente y responde a las consultas con datos simulados. Los componentes ficticios forman parte de un agente de prueba completo que puede conectar a todas las interfaces del componente.  
  
 Una ventaja de las pruebas ficticias es que puede desarrollar el componente mientras otros componentes cuyos servicios usará el suyo aún están en desarrollo.  
  
## <a name="maintain-the-relationships-between-tests-and-model"></a>Mantener las relaciones entre las pruebas y el modelo  
 En un proyecto típico que realiza una iteración cada pocas semanas, se realiza una revisión de los requisitos al principio de cada iteración. La reunión describe las características que se deben incluir en la siguiente iteración. Un modelo de requisitos puede usarse para ayudar a explicar los conceptos, escenarios y secuencias de acciones que se van a desarrollar. Las partes interesadas establecen prioridades, los desarrolladores realizan estimaciones y los evaluadores garantizan que se ha capturado de manera correcta el comportamiento esperado de cada característica.  
  
 Escribir pruebas es la manera más eficaz para definir un requisito y también es una forma eficaz de garantizar que una persona tiene un conocimiento claro de lo que se necesita. Sin embargo, aunque la elaboración de pruebas lleva mucho tiempo durante un taller de especificación, crear modelos es un proceso que puede realizarse mucho más rápidamente.  
  
 Desde el punto de vista de las pruebas, un modelo de requisitos puede considerarse como una forma abreviada de realizar pruebas. Por ello, es importante mantener la relación entre las pruebas y el modelo a lo largo del proyecto.  
  
##  <a name="Attaching"></a>Adjuntar casos de prueba a elementos del modelo  
 Si el proyecto usa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], puede vincular las pruebas a los elementos del modelo. Esto le permite buscar rápidamente las pruebas afectadas por un cambio en los requisitos y le ayuda a controlar en qué medida se ha completado un requisito.  
  
 Puede vincular las pruebas a todos los tipos de elemento. A continuación se muestran algunos ejemplos:  
  
-   Vincule un caso de uso a las pruebas que lo verifican.  
  
-   Escriba las cláusulas de una condición posterior del caso de uso, u objetivo, en los comentarios que están vinculados al caso de uso y, después, vincule las pruebas a cada comentario.  
  
-   Escriba reglas invariantes en los comentarios de los diagramas de clases o de actividades y vincúlelas a las pruebas.  
  
-   Vincule las pruebas a un diagrama de actividades o a actividades individuales.  
  
-   Vincule un conjunto de pruebas al componente o subsistema que verifica.  
  
#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Para vincular las pruebas a un elemento del modelo o la relación  
  
1.  En [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)], cree un requisito y base en él un conjunto de pruebas. 
  
     El requisito que cree será un elemento de trabajo de [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)]. Puede ser un elemento de trabajo de caso de usuario, requisito o caso de uso según la plantilla de proceso que use el proyecto con [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Para obtener más información, consulte [seguimiento del trabajo mediante Visual Studio Team Services o Team Foundation Server](http://msdn.microsoft.com/Library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).  
  
2.  Vincule el elemento de trabajo de requisito a uno o varios elementos del modelo.  
  
     En un diagrama de modelado, haga clic en un elemento, comentario o relación y, a continuación, haga clic en **vínculo al elemento de trabajo**.
  
3.  Agregue al conjunto de pruebas casos de prueba que verifiquen el requisito expresado en el elemento de modelo.  
  
## <a name="see-also"></a>Vea también  
 [Crear modelos para la aplicación](../modeling/create-models-for-your-app.md)   
 [Requisitos de usuario del modelo](../modeling/model-user-requirements.md)   
 [Modelar la arquitectura de la aplicación](../modeling/model-your-app-s-architecture.md)   
 [Analizar y modelar la arquitectura](../modeling/analyze-and-model-your-architecture.md)
