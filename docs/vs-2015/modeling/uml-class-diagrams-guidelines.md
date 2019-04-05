---
title: 'Diagramas de clases UML: Instrucciones | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 608b5c37975c49e4e90cdf9edd923121350735e5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995361"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramas de clases UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede usar un *diagrama de clases UML* para describir los tipos de datos y sus relaciones con independencia de su implementación. El diagrama se utiliza para que la atención se centre en los aspectos lógicos de las clases en lugar de en su implementación.  
  
 Para crear un diagrama de clases UML, en el **arquitectura** menú, elija **nuevo diagrama UML o diagrama de capas**.  
  
 Para ver qué versiones de Visual Studio admiten esta característica, vea [Compatibilidad de versiones con las herramientas de arquitectura y modelado](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  En este tema se analizan los diagramas de clases de UML. Existe otro tipo de diagrama de clases, que se crea y utiliza para visualizar el código del programa. Consulte [diseñar y ver clases y tipos](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="Using"></a> Uso de diagramas de clases UML  
 Los diagramas de clases de UML pueden utilizarse para una gran variedad de propósitos:  
  
-   Para proporcionar una descripción de los tipos que se utilizan en un sistema y se pasan entre sus componentes que no tenga nada que ver con su implementación.  
  
     Por ejemplo, en el código .NET, el tipo Pedido de menú podría implementarse en la capa del negocio; en XML, en las interfaces entre los componentes; en SQL, en la base de datos, y en HTML, en la interfaz de usuario. Aunque estas implementaciones tengan un nivel de detalle diferente, la relación entre el tipo Pedido de menú y otros tipos, como Menú y Pago, es siempre la misma. El diagrama de clases de UML permite analizar estas relaciones con independencia de las implementaciones.  
  
-   Para clarificar el glosario de términos que se utiliza en la comunicación entre la aplicación y los usuarios y en las descripciones de las necesidades de los usuarios. Consulte [modelar los requisitos del usuario](../modeling/model-user-requirements.md).  
  
     Por ejemplo, piense en los casos de usuario, los casos de uso y otras descripciones de los requisitos de la aplicación de un restaurante. En este tipo de descripción, encontrará términos como Menú, Pedido, Comida, Precio, Pago, etc. Puede dibujar un diagrama de clases de UML en el que se definan las relaciones entre estos términos. De este modo, se reducirá el riesgo de inconsistencias en las descripciones de los requisitos, así como en la interfaz de usuario y los documentos de ayuda.  
  
### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas  
 Un diagrama de clases de UML normalmente se crea junto con otros diagramas de modelado para proporcionar descripciones de los tipos que utilizan. En cada caso, la representación física de los tipos no está implícita en ninguno de los diagramas.  
  
 Diagrama de actividades  
  
 Tipos de datos que pasan por un nodo de objeto.  
  
 Tipos de terminales de entrada (Input Pin) y de salida (Output Pin) de nodos de parámetros de actividad.  
  
 Consulte [diagramas de actividades UML: Directrices](../modeling/uml-activity-diagrams-guidelines.md).  
  
 Diagrama de secuencia  
  
 Tipos de parámetros y valores devueltos de mensajes.  
  
 Tipos de líneas de vida. La clase de una línea de vida debe incluir las operaciones de todos los mensajes que puede recibir.  
  
 Consulte [diagramas de secuencia UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 Diagrama de componentes  
  
 Interfaces de componentes, con un listado de sus operaciones.  
  
 Consulte [diagramas de componentes UML: Directrices](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagrama de casos de uso  
  
 Tipos mencionados en las descripciones de los objetivos y los pasos de un caso de uso.  
  
 Consulte [diagramas de casos de uso UML: Directrices](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Pasos básicos para dibujar diagramas de clases  
 Para obtener información de referencia sobre los elementos de diagramas de clases UML, vea [diagramas de clases UML: referencia](../modeling/uml-class-diagrams-reference.md).  
  
> [!NOTE]
>  Se describen los pasos detallados para crear cualquiera de los diagramas de modelado en [modelos y diagramas UML editar](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-uml-class-diagram"></a>Para crear un diagrama de clases de UML  
  
1.  En el **arquitectura** menú, elija **nuevo UML o diagrama de capas**.  
  
2.  En **plantillas**, elija **diagrama de clases UML**.  
  
3.  Especifique un nombre para el diagrama.  
  
4.  En **agregar a proyecto de modelado**, seleccione un proyecto de modelado existente de la solución, o **crear un nuevo proyecto de modelado**y, a continuación, elija **Aceptar**.  
  
     Aparece un nuevo diagrama de clase con el **UMLClass diagrama** cuadro de herramientas. El cuadro de herramientas contiene las relaciones y elementos necesarios.  
  
#### <a name="to-draw-a-uml-class-diagram"></a>Para dibujar un diagrama de clases de UML  
  
1.  Para crear un tipo, elija el **clase**, **interfaz** o **enumeración** herramienta en el cuadro de herramientas y, a continuación, haga clic en una parte en blanco del diagrama. (Si no puede ver el cuadro de herramientas, presione CTRL+ALT+X).  
  
2.  Para agregar atributos u operaciones a los tipos o literales a una enumeración, elija el **atributos**, **operaciones** o **literales** encabezado en el tipo y presione ENTRAR.  
  
     Puede escribir una firma, como por ejemplo `f(x:Boolean):Integer`. Consulte [atributos y operaciones](#AttributesAndOperations).  
  
     Para agregar rápidamente varios elementos, presione ENTRAR dos veces al final de cada elemento. Puede utilizar las teclas de dirección para subir y bajar la lista.  
  
3.  Para expandir o contraer un tipo, elija el icono de botón de contenido adicional situado en la parte superior izquierda. También puede expandir y contraer la **atributos** y **operaciones** sección de una clase o interfaz.  
  
4.  Para dibujar vínculos de asociación, herencia o dependencia entre los tipos, haga clic en la herramienta adecuada, a continuación, en el tipo de origen y, por último, en el tipo de destino.  
  
5.  Para crear tipos en un paquete, cree un paquete mediante el **paquete** herramienta y, a continuación, crear nuevos tipos y paquetes dentro del paquete. También puede copiarlos con el comando Copiar y pegarlos después en un paquete.  
  
6.  Cada diagrama es una vista de un modelo que comparten otros diagramas del mismo proyecto. Para ver una vista de árbol del modelo completo, elija **vista**, **Other Windows**, **Explorador de modelos UML**.  
  
##  <a name="UsingTypes"></a> Uso de clases, Interfaces y enumeraciones  
 Hay tres tipos estándar de clasificadores disponibles en el cuadro de herramientas. Estos se conocen como *tipos* a lo largo de este documento.  
  
 ![Una clase, una enumeración y una interfaz](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")  
  
- Use **clases** (1) para representar tipos de datos u objeto para la mayoría de los casos.  
  
- Use **Interfaces** (2) en un contexto donde es necesario diferenciar entre interfaces puras y clases concretas que tienen implementaciones internas. Esta diferencia resulta útil cuando el propósito del diagrama es describir una implementación de software. Resulta menos útil, sin embargo, cuando se modelan datos pasivos o cuando se definen contextos que se utilizan para describir los requisitos del usuario.  
  
- Use un **enumeración** (3) para representar un tipo que tiene un número limitado de valores literales, por ejemplo `Stop` y `Go`.  
  
  -   Agregue los valores literales a la enumeración. Asigne a cada uno un nombre diferente.  
  
  -   Si lo desea, también puede proporcionar un valor numérico para cada valor literal. Abra el menú contextual del literal de la enumeración, elija **propiedades**y, a continuación, escriba un número en el **valor** campo el **propiedades** ventana.  
  
  Asigne un nombre único a cada tipo.  
  
### <a name="getting-types-from-other-diagrams"></a>Obtener tipos de otros diagramas  
 Puede hacer que los tipos de otro diagrama aparezcan en su diagrama de clases de UML.  
  
 Diagrama de clases de UML  
  
 Puede hacer que una clase aparezca en varios diagramas de clases de UML. Cuando haya creado una clase en un diagrama, arrastre la clase del **Explorador de modelos UML** al otro diagrama.  
  
 Esto resulta útil si desea que cada diagrama se concentre en un grupo de relaciones determinado.  
  
 Por ejemplo, puede mostrar las asociaciones entre un Pedido de menú y el Menú del restaurante en un diagrama y las asociaciones entre Pedido de menú y Pago en otro diagrama.  
  
 Diagrama de componentes  
  
 Si ha definido interfaces en los componentes de un diagrama de componentes, puede arrastrar una interfaz de **Explorador de modelos UML** al diagrama de clases. En el diagrama de clases, puede definir los métodos que la interfaz incluye.  
  
 Consulte [diagramas de componentes UML: Directrices](../modeling/uml-component-diagrams-guidelines.md).  
  
 Diagrama de secuencia UML  
  
 Puede crear clases e interfaces de líneas de vida en un diagrama de secuencia y, a continuación, arrastre la clase de **Explorador de modelos UML** a un diagrama de clases UML. Cada línea de vida de un diagrama de secuencia representa una instancia de un objeto, componente o actor.  
  
 Para crear una clase desde una línea de vida, abra el menú contextual de la línea de vida y, a continuación, elija **crear clase** o **crear interfaz**. Consulte [diagramas de secuencia UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md).  
  
##  <a name="AttributesAndOperations"></a> Atributos y operaciones  
 Un atributo (4) es un valor con nombre que todas las instancias de un tipo pueden tener. Cuando se obtiene acceso a un atributo, no se modifica el estado de la instancia.  
  
 Una operación (5) es un método o función que las instancias del tipo pueden realizar. Puede devolver un valor. Si su **isQuery** propiedad es true, no puede cambiar el estado de la instancia.  
  
 Para agregar un atributo u operación a un tipo, abra el menú contextual para el tipo, elija **agregar**y, a continuación, elija **atributo** o **operación**.  
  
 Para ver sus propiedades, abra el menú contextual para el atributo u operación y, a continuación, elija **propiedades**. Las propiedades aparecen en la **propiedades** ventana.  
  
 Para ver las propiedades de parámetros de la operación, elija <strong>[...]</strong> en el **parámetros** propiedad. Aparece un nuevo cuadro de diálogo Propiedades.  
  
 Para obtener información detallada sobre todas las propiedades que puede establecer, consulte:  
  
-   [Propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
### <a name="types-of-attributes-and-operations"></a>Tipos de atributos y operaciones  
 Cada *tipo* de un atributo u operación y cada tipo de parámetro, puede ser uno de los siguientes:  
  
- **(ninguno)**  -Puede dejar un tipo no especificado en la firma omitiendo el signo de dos puntos anterior (`:`).  
  
- Uno de los tipos primitivos estándares: **Booleano**, **entero**, **cadena**.  
  
- Un tipo que esté definido en el modelo.  
  
- Un valor parametrizado de un tipo de plantilla, formato plantilla\<parámetro >. Consulte [tipos de plantilla](#Templates).  
  
  También puede escribir el nombre de un tipo que aún no haya definido en el modelo. El nombre aparecerá en la lista **tipos sin especificar** en el Explorador de modelos UML.  
  
> [!NOTE]
>  Si posteriormente define una clase o interfaz con ese nombre en el modelo, los atributos y operaciones anteriores todavía harán referencia al elemento en Tipos sin especificar. Si desea cambiarlos para que hagan referencia a la nueva clase, deberá visitar cada atributo u operación y restablecer el tipo, seleccionando la nueva clase en el menú desplegable.  
  
#### <a name="multiple-types"></a>Tipos múltiples  
 Puede establecer la multiplicidad de cualquier tipo de parámetro, atributo u operación.  
  
 Los valores permitidos son los siguientes:  
  
 `[1]`  
  
 Un valor del tipo especificado. Este es el valor predeterminado.  
  
 `[0..1]`  
  
 **NULL** o un valor del tipo especificado.  
  
 `[*]`  
  
 Una colección con un número de instancias del tipo especificado.  
  
 `[1..*]`  
  
 Una colección de al menos una instancia del tipo especificado.  
  
 `[n..m]`  
  
 Una colección de entre `n` y `m` instancias del tipo especificado.  
  
 Si la multiplicidad es mayor que 1, también puede establecer estas propiedades:  
  
-   **IsOrdered** : si es true, la colección tiene un orden definido.  
  
-   **IsUnique** : si es true, no hay ningún valor duplicado en la colección.  
  
### <a name="visibility"></a>Visibility  
 *Visibilidad* indica si el atributo u operación es accesible fuera de la definición de clase. Los valores permitidos son los siguientes:  
  
 **Public**  
  
 **+**  
  
 Accesible desde todos los demás tipos.  
  
 **Private**  
  
 **-**  
  
 Solamente se puede obtener acceso a la definición interna de este tipo.  
  
 **Paquete**  
  
 **~**  
  
 Solamente se puede obtener acceso dentro del paquete que contiene este tipo y en los paquetes que lo importan explícitamente. Consulte [definir espacios de nombres y paquetes](#Packages).  
  
 **Protected**  
  
 **#**  
  
 Solamente se puede obtener acceso a este tipo y sus tipos heredados. Consulte [herencia](#Inheritance).  
  
### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Establecer la firma de un atributo u operación  
 La firma de un atributo u operación es una colección de propiedades entre las que se incluyen la visibilidad, el nombre, los parámetros (en las operaciones) y el tipo.  
  
 Puede escribir directamente una firma en el diagrama. Haga clic en el atributo u operación para seleccionarlo y, a continuación, vuelva a hacer clic.  
  
 Escriba la firma con el formato:  
  
```  
visibility attribute-name : Type  
```  
  
 \- o -  
  
```  
visibility operation-name (parameter1 : Type1, ...) : Type  
```  
  
 Por ejemplo:  
  
```  
+ AddItem (item : MenuItem, quantity : Integer) : Boolean  
```  
  
 Utilice la forma abreviada de visibilidad. El valor predeterminado es `+` (public).  
  
 Los tipos pueden ser tipos definidos en el modelo, tipos estándar, como Entero o Cadena, o el nombre de un nuevo tipo que no se haya definido todavía.  
  
> [!NOTE]
>  Si escribe un nombre sin tipo en una lista de parámetros, especificará el nombre del parámetro, en lugar de su tipo. En este ejemplo, MenuItem e Integer resultan ser los nombres de dos parámetros con tipos no especificados:  
>   
>  `AddItem(MenuItem, Integer) /* parameter names, not types! */`  
  
 Para establecer la multiplicidad de un tipo en una firma, escriba la multiplicidad entre corchetes tras el nombre de tipo, por ejemplo:  
  
```  
+ AddItems (items : MenuItem [1..*])  
+ MenuContent : MenuItem [*]  
```  
  
 Si el atributo u operación es estático, su nombre aparecerá subrayado en la firma. Si es abstracto, el nombre aparecerá en cursiva.  
  
 Sin embargo, solo se puede establecer el **Is Static** y **Is Abstract** propiedades en el **propiedades** ventana.  
  
#### <a name="full-signature"></a>Firma completa  
 Al modificar la firma de un atributo u operación, algunas propiedades adicionales pueden aparecer al final de la línea y después de cada parámetro. Aparecen entre llaves {...}. Puede editar o agregar estas propiedades. Por ejemplo:  
  
```  
+ AddItems (items: MenuItem [1..*] {unique, ordered})  
+ GetItems (filter: String) : MenuItem [*] {ordered, query}  
```  
  
 Estas propiedades son las siguientes:  
  
 `unique`  
  
 **Es único**  
  
 No hay valores duplicados en la colección. Se aplica a tipos cuya multiplicidad es mayor que 1.  
  
 `ordered`  
  
 **Se ha pedido**  
  
 La colección es una secuencia. Si es false, no está definido el primer elemento. Se aplica a tipos cuya multiplicidad es mayor que 1.  
  
 `query`  
  
 **Es la consulta**  
  
 La operación no cambia el estado de la instancia. Solo se aplica a las operaciones.  
  
 `/`  
  
 **Se deriva**  
  
 El atributo se calcula a partir de los valores de otros atributos o asociaciones.  
  
 "/" precede al nombre de un atributo. Por ejemplo:  
  
```  
/TotalPrice: Integer  
```  
  
 Normalmente, la firma completa solamente aparece en el diagrama mientras se está editando. Al finalizar la edición, las propiedades adicionales quedan ocultas. Si desea ver todo el tiempo de la firma completa, abra el menú contextual para el tipo y, a continuación, elija **Mostrar firma completa**.  
  
##  <a name="Associations"></a> Dibujar y utilizar asociaciones  
 Utilice una asociación para representar cualquier tipo de vinculación entre dos elementos, con independencia del modo en que esta vinculación se implemente en el software. Puede utilizar, por ejemplo, una asociación para representar un puntero en C#, una relación de una base de datos o una referencia cruzada que asocie una parte de un archivo XML con otra. Puede representar una asociación entre objetos en el mundo real, como la tierra y el sol. La asociación no indica cómo se representa el vínculo, solo que existe la información.  
  
### <a name="properties-of-an-association"></a>Propiedades de una asociación  
 Después de crear una asociación, establezca sus propiedades. Abra el menú contextual para la asociación y, a continuación, elija **propiedades**.  
  
 Además de las propiedades de la asociación como un todo, cada *rol*, es decir, cada extremo de la asociación, tiene algunas propiedades propias. Para verlas, expanda el **primer rol** y **segundo rol** propiedades.  
  
 Algunas propiedades de cada uno de los roles pueden verse directamente en el diagrama. Son las siguientes:  
  
- El nombre del rol. Aparece en el extremo correspondiente de la asociación del diagrama. Puede establecer en el diagrama o en el **propiedades** ventana.  
  
- **Multiplicidad**, cuyo valor predeterminado es **1**. También aparece en el diagrama situado junto al extremo correspondiente de la asociación.  
  
- **Agregación**. Aparece en un extremo del conector y tiene forma de diamante. Puede utilizarse para indicar que las instancias del rol que se están agregando poseen o contienen instancias del otro rol.  
  
- **Es navegable**. Si es true solamente en uno de los roles, aparece una flecha en la dirección navegable. Puede utilizarse para indicar la navegabilidad de vínculos y relaciones de base de datos en el software.  
  
  Para obtener los detalles completos de estas y otras propiedades, vea [diagramas de clases de propiedades de las asociaciones de UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).  
  
### <a name="navigability"></a>Navegabilidad  
 Cuando se dibuja una asociación, tiene una flecha en un extremo, lo que significa que la asociación es navegable en esa dirección. Esto resulta útil si el diagrama de clases representa las clases de software y las asociaciones representan punteros o referencias. Sin embargo, cuando se usa un diagrama de clases para representar entidades y relaciones o conceptos de negocio, es menos pertinente representar la navegabilidad. En este caso, podría ser preferible dibujar las asociaciones sin flechas. Puede hacerlo estableciendo la **es navegable** propiedad en ambos extremos de la asociación en True. Para facilitar esta tarea, puede descargar el ejemplo de código [modelado de dominio UML](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4).  
  
### <a name="attributes-and-associations"></a>Atributos y asociaciones  
 Una asociación es una manera gráfica de mostrar un atributo. Por ejemplo, en lugar de crear una clase Restaurante con un atributo de tipo Menú, puede dibujar una asociación entre Restaurante y Menú.  
  
 Cada nombre de atributo se transforma en un nombre de rol. Aparece en el extremo opuesto al tipo propietario de la asociación. Observe, por ejemplo, `myMenu` en la ilustración.  
  
 Por lo general, resulta más conveniente utilizar los atributos solo en aquellos tipos que no se van a dibujar en el diagrama, como los tipos primitivos.  
  
 ![Atributos y asociación equivalentes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")  
  
##  <a name="Inheritance"></a> Herencia  
 Use la **herencia** herramienta para crear las relaciones siguientes:  
  
- Un *generalización* relación entre un tipo especializado y un tipo general  
  
   \- o -  
  
- Un *realización* relación entre una clase y una interfaz que implementa.  
  
  No se pueden crear bucles en las relaciones de herencia.  
  
### <a name="generalization"></a>Generalización  
 La generalización significa que el tipo que se especializa o el tipo derivado heredan los atributos, las operaciones y las asociaciones del tipo general o tipo base.  
  
 El tipo general aparece en el extremo de la relación con la punta de flecha.  
  
 Las operaciones y atributos heredados no suelen mostrarse en los tipos especializados. Sin embargo, pueden agregarse operaciones heredadas a la lista de operaciones del tipo especializado. Esto resulta útil si desea invalidar algunas de las propiedades de una operación en el tipo especializado o si desea indicar que el código que se va a implementar debería hacerlo.  
  
##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Para invalidar la definición de una operación en un tipo especializado  
  
1. Haga clic en la relación de generalización.  
  
    Aparecerá resaltada junto a una etiqueta de acción.  
  
2. Haga clic en la etiqueta de acción y, a continuación, haga clic en **invalidar operaciones**.  
  
    El **invalidar operaciones** aparece el cuadro de diálogo.  
  
3. Seleccione las operaciones que desee que aparezcan en el tipo especializado y, a continuación, haga clic en **Aceptar**.  
  
   Las operaciones que seleccionó aparecen ahora en el tipo especializado.  
  
### <a name="realization"></a>Realización  
 La realización significa que una clase implementa los atributos y operaciones especificados por la interfaz. La interfaz se encuentra en el extremo del conector que tiene la flecha.  
  
 Al crear un conector de realización, las operaciones de la interfaz se replican automáticamente en la clase que se realiza. Si se agregan nuevas operaciones a una interfaz, estas operaciones se replicarán en las clases que se realizan.  
  
 Después de crear una relación de realización, puede transformarla en una notación circular. Haga clic en la relación y elija **mostrar como círculo**.  
  
 De este modo, puede mostrar las interfaces que una clase implementa sin llenar los diagramas de clases con vínculos de realización. También puede mostrar la interfaz y las clases que la realizan en diagramas independientes.  
  
 ![Realización mostrada con conector y círculo](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")  
  
##  <a name="Templates"></a> Tipos de plantilla  
 Puede definir un tipo genérico o un tipo de plantilla que otros tipos o valores puedan parametrizar.  
  
 Por ejemplo, puede crear un Diccionario genérico parametrizado por tipos de valor y clave:  
  
 ![Clase de plantilla con dos parámetros](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")  
  
#### <a name="to-create-a-template-type"></a>Para crear un tipo de plantilla  
  
1. Cree una clase o interfaz. Este objeto pasará a ser el tipo de plantilla. Asígnele el nombre apropiado, por ejemplo `Dictionary`.  
  
2. Abra el menú contextual para el nuevo tipo y, a continuación, elija **propiedades**.  
  
3. En el **propiedades** ventana, haga clic en **[...]**  en el **parámetros de plantilla** campo.  
  
    El **Editor de colección de parámetros de plantilla** aparece el cuadro de diálogo.  
  
4. Haga clic en **Agregar**.  
  
5. Establezca la propiedad de nombre en el nombre de un parámetro del tipo de plantilla, por ejemplo, `Key`.  
  
6. Establecer **el tipo de parámetro**. El valor predeterminado es **clase**.  
  
7. Si desea que el parámetro acepte solamente clases derivadas de una clase base determinada, establezca **valor restringido** a la clase base que desee.  
  
8. Agregue tantos parámetros como sea necesario, a continuación, elija **Aceptar**.  
  
9. Agregue atributos y operaciones al tipo de plantilla del mismo modo que lo haría en otras clases.  
  
     Puede utilizar parámetros cuyo tipo sea **clase**, **interfaz** o **enumeración** en la definición de atributos y operaciones. Por ejemplo, si utiliza las clases de parámetros `Key` y `Value`, puede definir esta operación en `Dictionary`:  
  
     `Get(k : Key) : Value`  
  
     Puede usar un parámetro cuyo tipo **entero** como un límite de multiplicidad. Por ejemplo, el valor entero máximo de un parámetro podría utilizarse para definir la multiplicidad de un atributo como `[0..max]`.  
  
   Una vez creados los tipos de plantilla, puede utilizarlos para definir los enlaces de la plantilla:  
  
   ![Clase enlazada de la plantilla de diccionario](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")  
  
#### <a name="to-use-a-template-type"></a>Para utilizar un tipo de plantilla  
  
1.  Cree un nuevo tipo, por ejemplo, `AddressTable`.  
  
2.  Abra el menú contextual para el nuevo tipo y, a continuación, elija **propiedades**.  
  
3.  En el **Template Binding** propiedad, seleccione el tipo de plantilla, por ejemplo `Dictionary`, en la lista desplegable.  
  
4.  Expanda el **Template Binding** propiedad.  
  
     Aparecerá una fila para cada parámetro del tipo de plantilla.  
  
5.  Establezca cada parámetro en un valor apropiado. Por ejemplo, establezca el parámetro `Key` en una clase denominada `Name`.  
  
##  <a name="Packages"></a> Paquetes  
 Puede ver los paquetes en un diagrama de clases de UML. Un paquete es un contenedor de otros elementos del modelo. Puede crear cualquier elemento dentro de un paquete. En el diagrama, los elementos incluidos en el paquete se desplazarán al mover el paquete.  
  
 Puede utilizar el control de expandir y contraer para ocultar o mostrar el contenido del paquete.  
  
 Consulte [definir paquetes y espacios de nombres](../modeling/define-packages-and-namespaces.md).  
  
##  <a name="generating"></a> Generar código a partir de diagramas de clases UML  
 Para iniciar la implementación de las clases en un diagrama de clases UML, puede generar código C# o personalizar plantillas para la generación de código. Para iniciar la generación de código usando las plantillas de C# proporcionadas:  
  
-   Abra el menú contextual del diagrama o un elemento, elija **generar código**y, a continuación, establezca las propiedades necesarias.  
  
     Para obtener más información acerca de cómo establecer estas propiedades y personalizar las plantillas proporcionadas, consulte [generar código a partir de diagramas de clases UML](../modeling/generate-code-from-uml-class-diagrams.md).  
  
## <a name="see-also"></a>Vea también  
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrama de clases de UML: Referencia](../modeling/uml-class-diagrams-reference.md)   
 [Requisitos de usuario del modelo](../modeling/model-user-requirements.md)   
 [Diagramas de componentes UML: Referencia](../modeling/uml-component-diagrams-reference.md)   
 [Diagramas de secuencia de UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramas de casos de uso UML: Referencia](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramas de componentes UML: referencia](../modeling/uml-component-diagrams-reference.md)
