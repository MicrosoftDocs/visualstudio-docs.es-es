---
title: 'UML Class Diagrams: Guidelines | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c170827825d772f4d97cd22f0b5754232e8d2257
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297285"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramas de clases de UML: Instrucciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can use a *UML class diagram* to describe data types and their relationships separately from their implementation. El diagrama se utiliza para que la atención se centre en los aspectos lógicos de las clases en lugar de en su implementación.

 To create a UML class diagram, on the **Architecture** menu, choose **New UML Diagram or Layer Diagram**.

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> En este tema se analizan los diagramas de clases de UML. Existe otro tipo de diagrama de clases, que se crea y utiliza para visualizar el código del programa. See [Designing and Viewing Classes and Types](https://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="Using"></a> Using UML Class Diagrams
 Los diagramas de clases de UML pueden utilizarse para una gran variedad de propósitos:

- Para proporcionar una descripción de los tipos que se utilizan en un sistema y se pasan entre sus componentes que no tenga nada que ver con su implementación.

     Por ejemplo, en el código .NET, el tipo Pedido de menú podría implementarse en la capa del negocio; en XML, en las interfaces entre los componentes; en SQL, en la base de datos, y en HTML, en la interfaz de usuario. Aunque estas implementaciones tengan un nivel de detalle diferente, la relación entre el tipo Pedido de menú y otros tipos, como Menú y Pago, es siempre la misma. El diagrama de clases de UML permite analizar estas relaciones con independencia de las implementaciones.

- Para clarificar el glosario de términos que se utiliza en la comunicación entre la aplicación y los usuarios y en las descripciones de las necesidades de los usuarios. See [Model user requirements](../modeling/model-user-requirements.md).

     Por ejemplo, piense en los casos de usuario, los casos de uso y otras descripciones de los requisitos de la aplicación de un restaurante. En este tipo de descripción, encontrará términos como Menú, Pedido, Comida, Precio, Pago, etc. Puede dibujar un diagrama de clases de UML en el que se definan las relaciones entre estos términos. De este modo, se reducirá el riesgo de inconsistencias en las descripciones de los requisitos, así como en la interfaz de usuario y los documentos de ayuda.

### <a name="relationship-to-other-diagrams"></a>Relación con otros diagramas
 Un diagrama de clases de UML normalmente se crea junto con otros diagramas de modelado para proporcionar descripciones de los tipos que utilizan. En cada caso, la representación física de los tipos no está implícita en ninguno de los diagramas.

 Diagrama de actividades

 Tipos de datos que pasan por un nodo de objeto.

 Tipos de terminales de entrada (Input Pin) y de salida (Output Pin) de nodos de parámetros de actividad.

 See [UML Activity Diagrams: Guidelines](../modeling/uml-activity-diagrams-guidelines.md).

 Diagrama de secuencia

 Tipos de parámetros y valores devueltos de mensajes.

 Tipos de líneas de vida. La clase de una línea de vida debe incluir las operaciones de todos los mensajes que puede recibir.

 See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagrama de componentes

 Interfaces de componentes, con un listado de sus operaciones.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 Diagrama de casos de uso

 Tipos mencionados en las descripciones de los objetivos y los pasos de un caso de uso.

 See [UML Use Case Diagrams: Guidelines](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a> Basic Steps for Drawing Class Diagrams
 For reference information about the elements on UML class diagrams, see [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> Detailed steps for creating any of the modeling diagrams are described in [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>Para crear un diagrama de clases de UML

1. On the **Architecture** menu, choose **New UML or Layer Diagram**.

2. Under **Templates**, choose **UML Class Diagram**.

3. Especifique un nombre para el diagrama.

4. In **Add to Modeling Project**, select an existing modeling project in your solution, or **Create a New Modeling Project**, and then choose **OK**.

     A new class diagram appears with the **UMLClass Diagram** Toolbox. El cuadro de herramientas contiene las relaciones y elementos necesarios.

#### <a name="to-draw-a-uml-class-diagram"></a>Para dibujar un diagrama de clases de UML

1. To create a type, choose the **Class**, **Interface** or **Enumeration** tool on the Toolbox, and then click a blank part of the diagram. (Si no puede ver el cuadro de herramientas, presione CTRL+ALT+X).

2. To add attributes or operations to the types, or literals to an enumeration, choose the **Attributes**, **Operations** or **Literals** heading in the type, and press ENTER.

     Puede escribir una firma, como por ejemplo `f(x:Boolean):Integer`. See [Attributes and Operations](#AttributesAndOperations).

     Para agregar rápidamente varios elementos, presione ENTRAR dos veces al final de cada elemento. Puede utilizar las teclas de dirección para subir y bajar la lista.

3. Para expandir o contraer un tipo, elija el icono de botón de contenido adicional situado en la parte superior izquierda. You can also expand and collapse the **Attributes** and **Operations** section of a class or interface.

4. Para dibujar vínculos de asociación, herencia o dependencia entre los tipos, haga clic en la herramienta adecuada, a continuación, en el tipo de origen y, por último, en el tipo de destino.

5. To create types in a package, create a package using the **Package** tool, and then create new types and packages within the package. También puede copiarlos con el comando Copiar y pegarlos después en un paquete.

6. Cada diagrama es una vista de un modelo que comparten otros diagramas del mismo proyecto. To see a tree view of the complete model, choose **View**, **Other Windows**, **UML Model Explorer**.

## <a name="UsingTypes"></a> Using Classes, Interfaces, and Enumerations
 Hay tres tipos estándar de clasificadores disponibles en el cuadro de herramientas. These are referred to as *types* throughout this document.

 ![A class, an enumeration, and an interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Use **Classes** (1) to represent data or object types for most purposes.

- Use **Interfaces** (2) in a context where you have to differentiate between pure interfaces and concrete classes that have internal implementations. Esta diferencia resulta útil cuando el propósito del diagrama es describir una implementación de software. Resulta menos útil, sin embargo, cuando se modelan datos pasivos o cuando se definen contextos que se utilizan para describir los requisitos del usuario.

- Use an **Enumeration** (3) to represent a type that has a limited number of literal values, for example `Stop` and `Go`.

  - Agregue los valores literales a la enumeración. Asigne a cada uno un nombre diferente.

  - Si lo desea, también puede proporcionar un valor numérico para cada valor literal. Open the shortcut menu for the literal in the enumeration, choose **Properties**, and then type a number in the **Value** field in the **Properties** window.

  Asigne un nombre único a cada tipo.

### <a name="getting-types-from-other-diagrams"></a>Obtener tipos de otros diagramas
 Puede hacer que los tipos de otro diagrama aparezcan en su diagrama de clases de UML.

 Diagrama de clases de UML

 Puede hacer que una clase aparezca en varios diagramas de clases de UML. When you have created a class on one diagram, drag the class from **UML Model Explorer** onto the other diagram.

 Esto resulta útil si desea que cada diagrama se concentre en un grupo de relaciones determinado.

 Por ejemplo, puede mostrar las asociaciones entre un Pedido de menú y el Menú del restaurante en un diagrama y las asociaciones entre Pedido de menú y Pago en otro diagrama.

 Diagrama de componentes

 If you have defined interfaces on the components in a component diagram, you can drag an interface from **UML Model Explorer** onto the class diagram. En el diagrama de clases, puede definir los métodos que la interfaz incluye.

 See [UML Component Diagrams: Guidelines](../modeling/uml-component-diagrams-guidelines.md).

 Diagrama de secuencia UML

 You can create classes and interfaces from lifelines in a sequence diagram, and then drag the class from **UML Model Explorer** to a UML class diagram. Cada línea de vida de un diagrama de secuencia representa una instancia de un objeto, componente o actor.

 To create a class from a lifeline, open the shortcut menu for the lifeline, and then choose **Create Class** or **Create Interface**. See [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a> Attributes and Operations
 Un atributo (4) es un valor con nombre que todas las instancias de un tipo pueden tener. Cuando se obtiene acceso a un atributo, no se modifica el estado de la instancia.

 Una operación (5) es un método o función que las instancias del tipo pueden realizar. Puede devolver un valor. If its **isQuery** property is true, it cannot change the state of the instance.

 To add an attribute or operation to a type, open the shortcut menu for the type, choose **Add**, and then choose **Attribute** or **Operation**.

 To see its properties, open the shortcut menu for the attribute or operation, and then choose **Properties**. The properties appear in the **Properties** window.

 To see the properties of an operation's parameters, choose <strong>[…]</strong>in the **Parameters** property. Aparece un nuevo cuadro de diálogo Propiedades.

 Para obtener información detallada sobre todas las propiedades que puede establecer, consulte:

- [Propiedades de los atributos de diagramas de clases de UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propiedades de las operaciones de diagramas de clases de UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Tipos de atributos y operaciones
 Each *Type* of an attribute or operation, and each parameter type, can be one of the following:

- **(none)** - You can leave a type unspecified in the signature by omitting the preceding colon (`:`).

- One of the standard primitive types: **Boolean**, **Integer**, **String**.

- Un tipo que esté definido en el modelo.

- A parameterized value of a template type, written Template\<Parameter>. See [Template Types](#Templates).

  También puede escribir el nombre de un tipo que aún no haya definido en el modelo. The name will be listed under **Unspecified Types** in UML Model Explorer.

> [!NOTE]
> Si posteriormente define una clase o interfaz con ese nombre en el modelo, los atributos y operaciones anteriores todavía harán referencia al elemento en Tipos sin especificar. Si desea cambiarlos para que hagan referencia a la nueva clase, deberá visitar cada atributo u operación y restablecer el tipo, seleccionando la nueva clase en el menú desplegable.

#### <a name="multiple-types"></a>Tipos múltiples
 Puede establecer la multiplicidad de cualquier tipo de parámetro, atributo u operación.

 Los valores permitidos son los siguientes:

 `[1]`

 Un valor del tipo especificado. Este es el valor predeterminado.

 `[0..1]`

 **Null** or a value of the given type.

 `[*]`

 Una colección con un número de instancias del tipo especificado.

 `[1..*]`

 Una colección de al menos una instancia del tipo especificado.

 `[n..m]`

 Una colección de entre `n` y `m` instancias del tipo especificado.

 Si la multiplicidad es mayor que 1, también puede establecer estas propiedades:

- **IsOrdered** - If true, the collection has a defined order.

- **IsUnique** - If true, there are no duplicate values in the collection.

### <a name="visibility"></a>Visibility
 *Visibility* indicates whether the attribute or operation can be accessed outside the class definition. Los valores permitidos son los siguientes:

 **Public**

 **+**

 Accesible desde todos los demás tipos.

 **Private**

 **-**

 Solamente se puede obtener acceso a la definición interna de este tipo.

 **Paquete**

 **~**

 Solamente se puede obtener acceso dentro del paquete que contiene este tipo y en los paquetes que lo importan explícitamente. See [Defining Namespaces and Packages](#Packages).

 **Protected**

 **#**

 Solamente se puede obtener acceso a este tipo y sus tipos heredados. See [Inheritance](#Inheritance).

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
> Si escribe un nombre sin tipo en una lista de parámetros, especificará el nombre del parámetro, en lugar de su tipo. En este ejemplo, MenuItem e Integer resultan ser los nombres de dos parámetros con tipos no especificados:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Para establecer la multiplicidad de un tipo en una firma, escriba la multiplicidad entre corchetes tras el nombre de tipo, por ejemplo:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Si el atributo u operación es estático, su nombre aparecerá subrayado en la firma. Si es abstracto, el nombre aparecerá en cursiva.

 However, you can only set the **Is Static** and **Is Abstract** properties in the **Properties** window.

#### <a name="full-signature"></a>Firma completa
 Al modificar la firma de un atributo u operación, algunas propiedades adicionales pueden aparecer al final de la línea y después de cada parámetro. Aparecen entre llaves {...}. Puede editar o agregar estas propiedades. Por ejemplo:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Estas propiedades son las siguientes:

 `unique`

 **Is Unique**

 No hay valores duplicados en la colección. Se aplica a tipos cuya multiplicidad es mayor que 1.

 `ordered`

 **Is Ordered**

 La colección es una secuencia. Si es false, no está definido el primer elemento. Se aplica a tipos cuya multiplicidad es mayor que 1.

 `query`

 **Is Query**

 La operación no cambia el estado de la instancia. Solo se aplica a las operaciones.

 `/`

 **Is Derived**

 El atributo se calcula a partir de los valores de otros atributos o asociaciones.

 "/" precede al nombre de un atributo. Por ejemplo:

```
/TotalPrice: Integer
```

 Normalmente, la firma completa solamente aparece en el diagrama mientras se está editando. Al finalizar la edición, las propiedades adicionales quedan ocultas. If you want to see the full signature all the time, open the shortcut menu for the type, and then choose **Show Full Signature**.

## <a name="Associations"></a> Drawing and Using Associations
 Utilice una asociación para representar cualquier tipo de vinculación entre dos elementos, con independencia del modo en que esta vinculación se implemente en el software. Puede utilizar, por ejemplo, una asociación para representar un puntero en C#, una relación de una base de datos o una referencia cruzada que asocie una parte de un archivo XML con otra. Puede representar una asociación entre objetos en el mundo real, como la tierra y el sol. La asociación no indica cómo se representa el vínculo, solo que existe la información.

### <a name="properties-of-an-association"></a>Propiedades de una asociación
 Después de crear una asociación, establezca sus propiedades. Open the shortcut menu for the association, and then choose **Properties**.

 In addition to the properties of the association as a whole, each *role*, that is, each end of the association, has some properties of its own. To view them, expand the **First Role** and **Second Role** properties.

 Algunas propiedades de cada uno de los roles pueden verse directamente en el diagrama. Son las siguientes:

- El nombre del rol. Aparece en el extremo correspondiente de la asociación del diagrama. You can set it either on the diagram or in the **Properties** window.

- **Multiplicity**, which defaults to **1**. También aparece en el diagrama situado junto al extremo correspondiente de la asociación.

- **Aggregation**. Aparece en un extremo del conector y tiene forma de diamante. Puede utilizarse para indicar que las instancias del rol que se están agregando poseen o contienen instancias del otro rol.

- **Is Navigable**. Si es true solamente en uno de los roles, aparece una flecha en la dirección navegable. Puede utilizarse para indicar la navegabilidad de vínculos y relaciones de base de datos en el software.

  For the full details of these and other properties, see [Properties of associations on UML class diagrams](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Navegabilidad
 Cuando se dibuja una asociación, tiene una flecha en un extremo, lo que significa que la asociación es navegable en esa dirección. Esto resulta útil si el diagrama de clases representa las clases de software y las asociaciones representan punteros o referencias. Sin embargo, cuando se usa un diagrama de clases para representar entidades y relaciones o conceptos de negocio, es menos pertinente representar la navegabilidad. En este caso, podría ser preferible dibujar las asociaciones sin flechas. You can do so by setting the **Is Navigable** property on both ends of the association to True.

### <a name="attributes-and-associations"></a>Atributos y asociaciones
 Una asociación es una manera gráfica de mostrar un atributo. Por ejemplo, en lugar de crear una clase Restaurante con un atributo de tipo Menú, puede dibujar una asociación entre Restaurante y Menú.

 Cada nombre de atributo se transforma en un nombre de rol. Aparece en el extremo opuesto al tipo propietario de la asociación. Observe, por ejemplo, `myMenu` en la ilustración.

 Por lo general, resulta más conveniente utilizar los atributos solo en aquellos tipos que no se van a dibujar en el diagrama, como los tipos primitivos.

 ![Equivalent association and attributes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> Herencia
 Use the **Inheritance** tool to create the following relationships:

- A *generalization* relationship between a specialized type and a general type

   \- o -

- A *realization* relation between a class and an interface that it implements.

  No se pueden crear bucles en las relaciones de herencia.

### <a name="generalization"></a>Generalización
 La generalización significa que el tipo que se especializa o el tipo derivado heredan los atributos, las operaciones y las asociaciones del tipo general o tipo base.

 El tipo general aparece en el extremo de la relación con la punta de flecha.

 Las operaciones y atributos heredados no suelen mostrarse en los tipos especializados. Sin embargo, pueden agregarse operaciones heredadas a la lista de operaciones del tipo especializado. Esto resulta útil si desea invalidar algunas de las propiedades de una operación en el tipo especializado o si desea indicar que el código que se va a implementar debería hacerlo.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Para invalidar la definición de una operación en un tipo especializado

1. Haga clic en la relación de generalización.

    Aparecerá resaltada junto a una etiqueta de acción.

2. Click the Action tag, and then click **Override Operations**.

    The **Override Operations** dialog box appears.

3. Select the operations that you want to appear in the specializing type, and then click **OK**.

   Las operaciones que seleccionó aparecen ahora en el tipo especializado.

### <a name="realization"></a>Realización
 La realización significa que una clase implementa los atributos y operaciones especificados por la interfaz. La interfaz se encuentra en el extremo del conector que tiene la flecha.

 Al crear un conector de realización, las operaciones de la interfaz se replican automáticamente en la clase que se realiza. Si se agregan nuevas operaciones a una interfaz, estas operaciones se replicarán en las clases que se realizan.

 Después de crear una relación de realización, puede transformarla en una notación circular. Right-click the relationship and choose **Show as Lollipop**.

 De este modo, puede mostrar las interfaces que una clase implementa sin llenar los diagramas de clases con vínculos de realización. También puede mostrar la interfaz y las clases que la realizan en diagramas independientes.

 ![Realization shown with conector and lollipop](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a> Template Types
 Puede definir un tipo genérico o un tipo de plantilla que otros tipos o valores puedan parametrizar.

 Por ejemplo, puede crear un Diccionario genérico parametrizado por tipos de valor y clave:

 ![Template class with two parameters](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Para crear un tipo de plantilla

1. Cree una clase o interfaz. Este objeto pasará a ser el tipo de plantilla. Asígnele el nombre apropiado, por ejemplo `Dictionary`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Properties** window, click **[…]** in the **Template Parameters** field.

    The **Template Parameter Collection Editor** dialog box appears.

4. Haga clic en **Agregar**.

5. Establezca la propiedad de nombre en el nombre de un parámetro del tipo de plantilla, por ejemplo, `Key`.

6. Set **Parameter Kind**. The default is **Class**.

7. If you want the parameter to accept only derived classes of a particular base class, set **Constrained Value** to the base class that you want.

8. Add as many parameters as you need, then choose **OK**.

9. Agregue atributos y operaciones al tipo de plantilla del mismo modo que lo haría en otras clases.

     You can use parameters whose kind is **Class**, **Interface** or **Enumeration** in the definition of attributes and operations. Por ejemplo, si utiliza las clases de parámetros `Key` y `Value`, puede definir esta operación en `Dictionary`:

     `Get(k : Key) : Value`

     You can use a parameter whose kind is **Integer** as a bound in a multiplicity. Por ejemplo, el valor entero máximo de un parámetro podría utilizarse para definir la multiplicidad de un atributo como `[0..max]`.

   Una vez creados los tipos de plantilla, puede utilizarlos para definir los enlaces de la plantilla:

   ![A  class bound from the Dictionary template](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Para utilizar un tipo de plantilla

1. Cree un nuevo tipo, por ejemplo, `AddressTable`.

2. Open the shortcut menu for the new type, and then choose **Properties**.

3. In the **Template Binding** property, select the template type, for example `Dictionary`, from the drop-down list.

4. Expand the **Template Binding** property.

     Aparecerá una fila para cada parámetro del tipo de plantilla.

5. Establezca cada parámetro en un valor apropiado. Por ejemplo, establezca el parámetro `Key` en una clase denominada `Name`.

## <a name="Packages"></a> Packages
 Puede ver los paquetes en un diagrama de clases de UML. Un paquete es un contenedor de otros elementos del modelo. Puede crear cualquier elemento dentro de un paquete. En el diagrama, los elementos incluidos en el paquete se desplazarán al mover el paquete.

 Puede utilizar el control de expandir y contraer para ocultar o mostrar el contenido del paquete.

 See [Define packages and namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a> Generating Code from UML Class Diagrams
 Para iniciar la implementación de las clases en un diagrama de clases UML, puede generar código C# o personalizar plantillas para la generación de código. Para iniciar la generación de código usando las plantillas de C# proporcionadas:

- Open the shortcut menu for the diagram or an element, choose **Generate Code**, and then set the necessary properties.

     For more information about how to set these properties and customize the provided templates, see [Generate code from UML class diagrams](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Vea también
 [Edit UML models and diagrams](../modeling/edit-uml-models-and-diagrams.md) [UML Class Diagrams: Reference](../modeling/uml-class-diagrams-reference.md) [Model user requirements](../modeling/model-user-requirements.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md) [UML Sequence Diagrams: Reference](../modeling/uml-sequence-diagrams-reference.md) [UML Use Case Diagrams: Reference](../modeling/uml-use-case-diagrams-reference.md) [UML Component Diagrams: Reference](../modeling/uml-component-diagrams-reference.md)
