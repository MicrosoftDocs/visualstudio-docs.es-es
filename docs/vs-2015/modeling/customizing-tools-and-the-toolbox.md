---
title: Customizing Tools and the Toolbox | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
ms.assetid: 2a0d03d7-ebc6-4458-b9f4-d2cb8418a62d
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a5e2a46a2326c123d6b7b4e85fa29908ede9fc9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299331"
---
# <a name="customizing-tools-and-the-toolbox"></a>Personalizar las herramientas y el cuadro de herramientas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe definir los elementos del cuadro de herramientas que quiera que los usuarios puedan agregar a sus modelos. There are two kinds of tools: element tools and connection tools. En el diseñador generado, un usuario puede seleccionar una herramienta de elemento para dibujar formas en el diagrama, y puede seleccionar una herramienta de conexión para dibujar vínculos entre las formas. Por lo general, las herramientas de elemento permiten a los usuarios agregar instancias de clases de dominio a sus modelos, y las herramientas de conexión les permiten agregar instancias de relaciones de dominio.

 En este tema:

- [How the Toolbox is Defined](#ToolboxDef)

- [Personalizar herramientas de elemento](#customizing)

- [Creating Groups of Elements from a Tool](#groups)

- [Customizing Connection Tools](#connections)

## <a name="ToolboxDef"></a> How the toolbox is defined
 En DSL Explorer (Explorador de DSL), expanda el nodo Editor (Editor) y los nodos situados bajo él. Normalmente, verá una jerarquía similar a esta:

```

Editor
     Toobox Tabs
        MyDsl          //a tab
           Tools
               ExampleElement      // an element tool
               ExampleRelationship // a connection tool

```

 En esta parte de DSL Explorer (Explorador de DSL), puede:

- Crear nuevas pestañas. Las pestañas definen los títulos de sección en el cuadro de herramientas.

- Crear nuevas herramientas.

- Copiar y pegar herramientas.

- Subir o bajar las herramientas en la lista.

- Eliminar pestañas y herramientas.

> [!IMPORTANT]
> Para agregar o pegar elementos en DSL Explorer (Explorador de DSL), haga clic con el botón secundario en el elemento primario principal del nuevo nodo. For example, to add a tool, right-click the tab, and not the **Tools** node. To add a tab, right-click the **Editor** node.

 The **Toolbox Icon** property of every tool references a 16x16 bitmap file. These files are usually kept in the **Dsl\Resources** folder.

 The **Class** property of an element tool refers to a concrete domain class. De forma predeterminada, la herramienta creará instancias de esta clase. Sin embargo, puede escribir código para que la herramienta cree grupos de elementos, o elementos de diferentes tipos.

 The **Connection Builder** property of a connection tool refers to a connection builder, which defines what types of elements the tool can connect, and what relationships it creates between them. Los generadores de conexiones se definen como nodos en DSL Explorer (Explorador de DSL). Los generadores de conexiones se crean automáticamente al definir relaciones de dominio, pero puede escribir código para personalizarlos.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Para agregar una herramienta al cuadro de herramientas

1. Normalmente, una herramienta de elemento se crea después de haber creado una clase de forma y de haberla asignado a una clase de dominio.

     Y una herramienta de conector se suele crear después de haber creado una clase de conector y de haberla asignado a una relación de referencia.

2. In DSL Explorer, expand the **Editor** node and the **Toolbox Tabs** node.

     Right-click a toolbox tab node, and then click **Add New Element Tool** or **Add New Connection Tool**.

3. Set the **Toolbox Icon** property to refer to a 16x16 bitmap.

     If you want to define a new icon, create a bitmap file in Solution Explorer in the **Dsl\Resources** folder. The file should have the following property values: **Build Action** = **Content**; **Copy to Output Directory** = **Do not copy**.

4. **For an element tool:** Set the **Class** property of the tool to refer to a concrete domain class that is mapped to a shape.

     **For a connector tool:** Set the **Connection Builder** property of the tool to one of the items that are offered in the drop-down list. Los generadores de conexiones se crean automáticamente cuando se asigna un conector a una relación de dominio. Si ha creado un conector recientemente, normalmente seleccionaría el generador de conexiones asociado.

5. Para probar el DSL, presione F5 o CTRL+F5 y, en la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra un archivo de modelo de muestra. La nueva herramienta debería aparecer en el cuadro de herramientas. Arrástrela al diagrama para comprobar que crea un nuevo elemento.

     Si la herramienta no aparece, detenga la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In the Windows **Start** menu, run **Reset the Microsoft Visual Studio 2010 Experimental Instance**. On the [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Build** menu, click **Rebuild Solution**. Después, vuelva a probar el DSL.

## <a name="customizing"></a> Customizing Element Tools
 De forma predeterminada, la herramienta creará una instancia única de la clase especificada, pero puede cambiar esto de dos maneras:

- Defina directivas de combinación de elementos en otras clases, permita que acepten nuevas instancias de esta clase y permita que creen vínculos adicionales cuando se crea un elemento nuevo. Por ejemplo, podría permitir que el usuario coloque un comentario en otro elemento, creando así un vínculo de referencia entre los dos.

     Estas personalizaciones afectan también a lo que sucede cuando el usuario pega o arrastra y coloca un elemento.

     For more information, see [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md).

- Escriba código para personalizar la herramienta de manera que pueda crear grupos de elementos. La herramienta se inicializa mediante métodos de ToolboxHelper.cs que puede invalidar. For more information, see [Creating Groups of Elements from a Tool](#groups).

## <a name="groups"></a> Creating Groups of Elements from a Tool
 Cada herramienta de elemento contiene un prototipo de los elementos que debe crear. De forma predeterminada, cada herramienta de elemento crea un solo elemento, pero se puede crear un grupo de objetos relacionados con una herramienta. Para ello, inicialice la herramienta con un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> que contenga los elementos relacionados.

 El siguiente ejemplo se toma de un DSL en el que hay un tipo Transistor. Cada Transistor tiene tres Terminals con nombre. La herramienta de elemento de Transistors almacena un prototipo que contiene cuatro elementos de modelo y tres vínculos de relación. Cuando el usuario arrastra la herramienta al diagrama, se crea una instancia del prototipo que se vincula a la raíz del modelo.

 This code overrides a method that is defined in **Dsl\GeneratedCode\ToolboxHelper.cs**.

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;

  public partial class CircuitsToolboxHelper
  {
    /// <summary>
    /// Toolbox initialization, called for each element tool on the toolbox.
    /// This version deals with each Component subtype separately.
    /// </summary>
    /// <param name="store"></param>
    /// <param name="domainClassId">Identifies the domain class this tool should instantiate.</param>
    /// <returns>prototype of the object or group of objects to be created by tool</returns>
    protected override ElementGroupPrototype CreateElementToolPrototype(Store store, Guid domainClassId)
    {
        if (domainClassId == Transistor.DomainClassId)
        {
            Transistor transistor = new Transistor(store);

            transistor.Base = new ComponentTerminal(store);
            transistor.Collector = new ComponentTerminal(store);
            transistor.Emitter = new ComponentTerminal(store);

            transistor.Base.Name = "base";
            transistor.Collector.Name = "collector";
            transistor.Emitter.Name = "emitter";

            // Create an ElementGroup for the Toolbox.
            ElementGroup elementGroup = new ElementGroup(store.DefaultPartition);
            elementGroup.AddGraph(transistor, true);
            // AddGraph includes the embedded parts

            return elementGroup.CreatePrototype();
        }
        else
        {
            return base.CreateElementToolPrototype(store, domainClassId);
}  }    }

```

## <a name="connections"></a> Customizing Connection Tools
 Normalmente, se crea una herramienta de elemento al crear una nueva clase de conector. También puede sobrecargar una herramienta permitiendo que los tipos de los dos extremos determinen el tipo de la relación. Por ejemplo, podría definir una herramienta de conexión que podría crear relaciones Persona-Persona y Persona-Ciudad.

 Las herramientas de conexión invocan generadores de conexiones. Use generadores de conexiones para especificar cómo los usuarios pueden vincular elementos en el diseñador generado. Los generadores de conexiones especifican los elementos que se pueden vincular y el tipo de vínculo que se crea entre ellos.

 Cuando se crea una relación de referencia entre clases de dominio, automáticamente se crea un generador de conexiones. Puede usar este generador de conexiones cuando asigne una herramienta de conexión. For more information about how to create connection tools, see [Configuring the Toolbox](../modeling/customizing-tools-and-the-toolbox.md).

 Puede modificar el generador de conexiones predeterminado para que pueda tratar con tipos de orígenes y destinos diferentes, y crear diferentes tipos de relaciones.

 También puede escribir código personalizado para que los generadores de conexiones especifiquen las clases de origen y destino de la conexión, definan el tipo de conexión que se va a realizar y realicen otras acciones relacionadas con la creación de una conexión.

### <a name="the-structure-of-connection-builders"></a>Estructura de los generadores de conexiones
 Los generadores de conexiones contienen una o varias directivas de conexión de vínculo, que especifican la relación de dominio y los elementos de origen y destino. For example, in the Task Flow solution template, you can see the **CommentReferencesSubjectsBuilder** in the **DSL Explorer**. This connection builder contains one link connect directive named **CommentReferencesSubjects**, which is mapped to the domain relationship **CommentReferencesSubjects**. Esta directiva de conexión de vínculo contiene una directiva de rol de origen que apunta a la clase de dominio `Comment`, y una directiva de rol de destino que apunta a la clase de dominio `FlowElement`.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Usar generadores de conexiones para restringir los roles de origen y destino
 Puede usar generadores de conexiones para restringir la aparición de determinadas clases en el rol de origen o en el rol de destino de una relación de dominio determinada. Por ejemplo, puede que tenga una clase de dominio base que tiene una relación de dominio con otra clase de dominio, pero quizás no quiera que todas las clases derivadas de la clase base tengan los mismos roles en esa relación. In the Task Flow solution, there are four concrete domain classes (**StartPoint**, **EndPoint**, **MergeBranch**, and **Synchronization**) that inherit directly from the abstract domain class **FlowElement**, and two concrete domain classes (**Task** and **ObjectInState**) that inherit indirectly from it. There is also a **Flow** reference relationship that takes **FlowElement** domain classes in both its source role and target role. However, an instance of an **EndPoint** domain class should not be the source of an instance of a **Flow** relationship, nor should an instance of a **StartPoint** class be the target of an instance of a **Flow** relationship. The **FlowBuilder** connection builder has a link connect directive named **Flow** that specifies which domain classes can play the source role (**Task**, **MergeBranch**, **StartPoint**, and **Synchronization**) and which can play the target role(**MergeBranch**, **Endpoint**, and **Synchronization**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Generadores de conexiones con varias directivas de conexión de vínculo
 Puede agregar más de una directiva de conexión de vínculo a un generador de conexiones. This can help you hide some of the complexities of the domain model from users and keep the **Toolbox** from getting too cluttered. Puede agregar directivas de conexión de vínculo para varias relaciones de dominio diferentes a un único generador de conexiones. Sin embargo, debe combinar las relaciones de dominio cuando realicen aproximadamente la misma función.

 In the Task Flow solution, the **Flow** connection tool is used to draw instances of both the **Flow** and the **ObjectFlow** domain relationships. The **FlowBuilder** connection builder has, in addition to the **Flow** link connect directive described earlier, two link connect directives named **ObjectFlow**. These directives specify that an instance of an **ObjectFlow** relationship may be drawn between instances of the **ObjectInState** domain class, or from an instance of an **ObjectInState** to an instance of a **Task**, but not between two instances of a **Task**, or from an instance of a **Task** to an instance of an **ObjectInState**. However, an instance of a **Flow** relationship may be drawn between two instances of a **Task**. If you compile and run the Task Flow solution, you can see that drawing a **Flow** from an instance of an **ObjectInState** to an instance of a **Task** creates an instance of an **ObjectFlow**, but drawing a **Flow** between two instances of a **Task** creates an instance of a **Flow**.

### <a name="custom-code-for-connection-builders"></a>Código personalizado para generadores de conexiones
 Hay cuatro casillas en la interfaz de usuario que definen los diferentes tipos de personalización de los generadores de conexiones:

- the **Custom accept** check box on a source or target role directive

- the **Custom connect** check box on a source or target role directive

- the **Uses custom connect** check box on a connect directive

- the **Is Custom** property of the connection builder

  Debe proporcionar algún código de programa para realizar estas personalizaciones. Para averiguar qué código debe proporcionar, seleccione una de estas casillas, haga clic en Transformar todas las plantillas y, después, compile su solución. Se producirá un informe de error. Haga doble clic en el informe de error para ver un comentario que explica qué código debe agregar.

> [!NOTE]
> Para agregar código personalizado, cree una definición de clase parcial en un archivo de código diferente de los archivos de código de las carpetas GeneratedCode. Para evitar perder su trabajo, no edite los archivos de código generados. For more information, see [Overriding and Extending the Generated Classes](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Crear código para conexiones personalizadas
 In each link connect directive, the **Source role directives** tab defines from what types you can drag. Similarly, the **Target role directives** tab defines to what types you can drag. For each type, you can further specify whether to allow the connection (for that link connect directive) by setting the **Custom Accept** flag and then supplying the extra code.

 También puede personalizar lo que ocurre cuando se realiza la conexión. Por ejemplo, puede personalizar solo el caso en el que se arrastra hacia o desde una clase determinada, todos los casos que se rigen por una directiva de conexión de vínculo o todo el generador de conexiones FlowBuilder. Para cada una de estas opciones, puede establecer marcas personalizadas en el nivel correspondiente. Cuando se transforman todas las plantillas y se intenta compilar la solución, los mensajes de error le dirigen a comentarios que hay en el código generado. Estos comentarios identifican qué debe proporcionar.

 En la muestra del diagrama de componentes, el generador de conexiones de la relación de dominio Connection se personaliza para restringir las conexiones que se pueden realizar entre los puertos. La ilustración siguiente muestra que puede realizar conexiones solo desde elementos `OutPort` a elementos `InPort`, pero puede anidar unos componentes dentro de otros.

 **Connection Coming in to an OutPort from a Nested Component**

 ![Connection Builder](../modeling/media/connectionbuilder-3.png "ConnectionBuilder_3")

 Por este motivo, quizás quiera especificar que una conexión puede ir dirigida desde un componente anidado hacia un OutPort. To specify such a connection, you set **Uses Custom Accept** on the **InPort** type as source role and the **OutPort** type as target role in the **DSL Details** window as shown in the following illustrations:

 **Link Connect Directive in DSL Explorer**

 ![Connection builder image](../modeling/media/connectionbuilder-4a.png "ConnectionBuilder_4a")

 **Link Connect Directive in DSL Details Window**

 ![](../modeling/media/connectionbuilder-4b.png "ConnectionBuilder_4b")

 Después, debe proporcionar métodos en la clase ConnectionBuilder:

```
  public partial class ConnectionBuilder
  {
    /// <summary>
    /// OK if this component has children
    /// </summary>
    private static bool CanAcceptInPortAsSource(InPort candidate)
    {
       return candidate.Component.Children.Count > 0;
    }

    /// <summary>
    /// Only if source is on parent of target.
    /// </summary>
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts…
```

 For more information about customizing the model by using program code, see [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Puede usar un código similar, por ejemplo, para evitar que los usuarios creen bucles en vínculos de elementos primarios y secundarios. Estas restricciones se consideran inflexibles porque los usuarios no pueden infringirlas en ningún momento. También puede crear comprobaciones de validación flexibles que los usuarios pueden omitir temporalmente creando configuraciones no válidas que no puedan guardar.

### <a name="good-practice-in-defining-connection-builders"></a>Procedimientos recomendados para definir generadores de conexiones
 Debe definir un generador de conexiones para crear diferentes tipos de relaciones solo si están conceptualmente relacionados. En la muestra del flujo de tareas, use el mismo generador para crear los flujos entre las tareas y entre las tareas y los objetos. Sin embargo, resultaría confuso usar el mismo generador para crear relaciones entre comentarios y tareas.

 Si define un generador de conexiones para varios tipos de relaciones, debe asegurarse de que no se corresponda con más de un tipo del mismo par de objetos de origen y destino. De lo contrario, los resultados serán impredecibles.

 Para aplicar restricciones inflexibles se usa código personalizado, pero debe tener en cuenta si los usuarios deberán poder realizar conexiones no válidas temporalmente. En caso de que deban, puede modificar las restricciones para que las conexiones no se validen hasta que los usuarios intenten guardar los cambios.

## <a name="see-also"></a>Vea también
 [Customizing Element Creation and Movement](../modeling/customizing-element-creation-and-movement.md) [Customizing Copy Behavior](../modeling/customizing-copy-behavior.md) [How to: Add a Drag-and-Drop Handler](../modeling/how-to-add-a-drag-and-drop-handler.md) [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)
