---
title: Personalizar las herramientas y el cuadro de herramientas
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.selectiondialog
- vs.dsltools.dsldesigner.selecticondialog
- vs.dsltools.dsldesigner.selectcursordialog
helpviewer_keywords:
- Domain-Specific Language, toolbox
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae5873462c2938ab4215d1cd4837c496e235ab35
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913371"
---
# <a name="customizing-tools-and-the-toolbox"></a>Personalizar las herramientas y el cuadro de herramientas

Debe definir los elementos del cuadro de herramientas que quiera que los usuarios puedan agregar a sus modelos. Hay dos tipos de herramientas: herramientas de elemento y las herramientas de conexión. En el diseñador generado, un usuario puede seleccionar una herramienta de elemento para dibujar formas en el diagrama, y puede seleccionar una herramienta de conexión para dibujar vínculos entre las formas. Por lo general, las herramientas de elemento permiten a los usuarios agregar instancias de clases de dominio a sus modelos, y las herramientas de conexión les permiten agregar instancias de relaciones de dominio.

## <a name="ToolboxDef"></a> Cómo se define el cuadro de herramientas
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

-   Crear nuevas pestañas. Las pestañas definen los títulos de sección en el cuadro de herramientas.

-   Crear nuevas herramientas.

-   Copiar y pegar herramientas.

-   Subir o bajar las herramientas en la lista.

-   Eliminar pestañas y herramientas.

> [!IMPORTANT]
> Para agregar o pegar elementos en DSL Explorer (Explorador de DSL), haga clic con el botón secundario en el elemento primario principal del nuevo nodo. Por ejemplo, para agregar una herramienta, haga clic en la ficha y no el **herramientas** nodo. Para agregar una pestaña, haga clic en el **Editor** nodo.

El **icono cuadro de herramientas** propiedad de cada herramienta hace referencia a un archivo de mapa de bits 16 x 16. Normalmente, estos archivos se guardan en el **Dsl\Resources** carpeta.

El **clase** propiedad de una herramienta de elemento hace referencia a una clase de dominio concreto. De forma predeterminada, la herramienta creará instancias de esta clase. Sin embargo, puede escribir código para que la herramienta cree grupos de elementos, o elementos de diferentes tipos.

El **generador de conexiones** propiedad de una herramienta de conexión hace referencia a un generador de conexiones, que define qué tipos de elementos que puede conectar la herramienta y qué relaciones crea entre ellos. Los generadores de conexiones se definen como nodos en DSL Explorer (Explorador de DSL). Los generadores de conexiones se crean automáticamente al definir relaciones de dominio, pero puede escribir código para personalizarlos.

#### <a name="to-add-a-tool-to-the-toolbox"></a>Para agregar una herramienta al cuadro de herramientas

1.  Normalmente, una herramienta de elemento se crea después de haber creado una clase de forma y de haberla asignado a una clase de dominio.

     Y una herramienta de conector se suele crear después de haber creado una clase de conector y de haberla asignado a una relación de referencia.

2.  En el Explorador de DSL, expanda el **Editor** nodo y el **Toolbox Tabs** nodo.

     Haga clic en un nodo de la pestaña del cuadro de herramientas y, a continuación, haga clic en **agregar nueva herramienta de elemento** o **agregar nueva herramienta de conexión**.

3.  Establecer el **icono cuadro de herramientas** propiedad para hacer referencia a un mapa de bits de 16 x 16.

     Si desea definir un icono nuevo, cree un archivo de mapa de bits en el Explorador de soluciones en la **Dsl\Resources** carpeta. El archivo debe tener los siguientes valores de propiedad: **Acción de compilación** = **contenido**; **Copy to Output Directory** = **no copie**.

4.  **Para una herramienta de elemento:** Establecer el **clase** propiedad de la herramienta para hacer referencia a una clase de dominio concreto que se asigna a una forma.

     **Para una herramienta de conector:** Establecer el **generador de conexiones** propiedad de la herramienta para uno de los elementos que se ofrecen en la lista desplegable. Los generadores de conexiones se crean automáticamente cuando se asigna un conector a una relación de dominio. Si ha creado un conector recientemente, normalmente seleccionaría el generador de conexiones asociado.

5.  Para probar el DSL, presione F5 o CTRL+F5 y, en la instancia experimental de Visual Studio, abra un archivo de modelo de ejemplo. La nueva herramienta debería aparecer en el cuadro de herramientas. Arrástrela al diagrama para comprobar que crea un nuevo elemento.

     Si la herramienta no aparece, detenga el experimental de Visual Studio. En el Windows **iniciar** menú, ejecute **restablecer el Microsoft Visual Studio 2010 Experimental Instance**. En el menú **Compilar**, haga clic en **Recompilar solución**. Después, vuelva a probar el DSL.

## <a name="customizing"></a> Personalizar herramientas de elemento
 De forma predeterminada, la herramienta creará una instancia única de la clase especificada, pero puede cambiar esto de dos maneras:

-   Defina directivas de combinación de elementos en otras clases, permita que acepten nuevas instancias de esta clase y permita que creen vínculos adicionales cuando se crea un elemento nuevo. Por ejemplo, podría permitir que el usuario coloque un comentario en otro elemento, creando así un vínculo de referencia entre los dos.

     Estas personalizaciones afectan también a lo que sucede cuando el usuario pega o arrastra y coloca un elemento.

     Para obtener más información, consulte [personalizar la creación de elemento y el movimiento](../modeling/customizing-element-creation-and-movement.md).

-   Escriba código para personalizar la herramienta de manera que pueda crear grupos de elementos. La herramienta se inicializa mediante métodos de ToolboxHelper.cs que puede invalidar. Para obtener más información, consulte [crear grupos de elementos desde una herramienta](#groups).

## <a name="groups"></a> Creación de grupos de elementos de una herramienta
 Cada herramienta de elemento contiene un prototipo de los elementos que debe crear. De forma predeterminada, cada herramienta de elemento crea un solo elemento, pero se puede crear un grupo de objetos relacionados con una herramienta. Para ello, inicialice la herramienta con un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> que contenga los elementos relacionados.

 El siguiente ejemplo se toma de un DSL en el que hay un tipo Transistor. Cada Transistor tiene tres Terminals con nombre. La herramienta de elemento de Transistors almacena un prototipo que contiene cuatro elementos de modelo y tres vínculos de relación. Cuando el usuario arrastra la herramienta al diagrama, se crea una instancia del prototipo que se vincula a la raíz del modelo.

 Este código invalida un método que se define en **Dsl\GeneratedCode\ToolboxHelper.cs**.

 Para obtener más información acerca de cómo personalizar el modelo mediante el uso de código de programa, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

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

## <a name="connections"></a> Personalizar herramientas de conexión
 Normalmente, se crea una herramienta de elemento al crear una nueva clase de conector. También puede sobrecargar una herramienta permitiendo que los tipos de los dos extremos determinen el tipo de la relación. Por ejemplo, podría definir una herramienta de conexión que podría crear relaciones Persona-Persona y Persona-Ciudad.

 Las herramientas de conexión invocan generadores de conexiones. Use generadores de conexiones para especificar cómo los usuarios pueden vincular elementos en el diseñador generado. Los generadores de conexiones especifican los elementos que se pueden vincular y el tipo de vínculo que se crea entre ellos.

 Cuando se crea una relación de referencia entre clases de dominio, automáticamente se crea un generador de conexiones. Puede usar este generador de conexiones cuando asigne una herramienta de conexión. Para obtener más información sobre cómo crear herramientas de conexión, consulte [configurar el cuadro de herramientas](../modeling/customizing-tools-and-the-toolbox.md).

 Puede modificar el generador de conexiones predeterminado para que pueda tratar con tipos de orígenes y destinos diferentes, y crear diferentes tipos de relaciones.

 También puede escribir código personalizado para que los generadores de conexiones especifiquen las clases de origen y destino de la conexión, definan el tipo de conexión que se va a realizar y realicen otras acciones relacionadas con la creación de una conexión.

### <a name="the-structure-of-connection-builders"></a>Estructura de los generadores de conexiones
 Los generadores de conexiones contienen una o varias directivas de conexión de vínculo, que especifican la relación de dominio y los elementos de origen y destino. Por ejemplo, en la plantilla de solución de flujo de tareas, puede ver el **CommentReferencesSubjectsBuilder** en el **DSL Explorer**. Este generador de conexión contiene un vínculo conectar directiva denominada **CommentReferencesSubjects**, que se asigna a la relación de dominio **CommentReferencesSubjects**. Esta directiva de conexión de vínculo contiene una directiva de rol de origen que apunta a la clase de dominio `Comment`, y una directiva de rol de destino que apunta a la clase de dominio `FlowElement`.

### <a name="using-connection-builders-to-restrict-source-and-target-roles"></a>Usar generadores de conexiones para restringir los roles de origen y destino
 Puede usar generadores de conexiones para restringir la aparición de determinadas clases en el rol de origen o en el rol de destino de una relación de dominio determinada. Por ejemplo, puede que tenga una clase de dominio base que tiene una relación de dominio con otra clase de dominio, pero quizás no quiera que todas las clases derivadas de la clase base tengan los mismos roles en esa relación. En la solución de flujo de tareas, hay cuatro clases de dominio específicas (**StartPoint**, **extremo**, **MergeBranch**, y **sincronización**) que heredan directamente de la clase de dominio abstracta **FlowElement**, y dos clases de dominio de concretas (**tarea** y **ObjectInState**) que heredan directamente de ella. También hay un **flujo** hacen referencia la relación que toma **FlowElement** clases de dominio en su rol de origen y el rol de destino. Sin embargo, una instancia de un **extremo** la clase de dominio no debe ser el origen de una instancia de un **flujo** relación, ni se debe a una instancia de un **StartPoint** clase ser el destino de una instancia de un **flujo** relación. El **FlowBuilder** generador de conexiones tiene un vínculo conectar directiva denominada **flujo** que especifica qué clases de dominio pueden desempeñar el rol de origen (**tarea**,  **MergeBranch**, **StartPoint**, y **sincronización**) y que puede desempeñar el rol de destino (**MergeBranch**,  **Punto de conexión**, y **sincronización**).

### <a name="connection-builders-with-multiple-link-connect-directives"></a>Generadores de conexiones con varias directivas de conexión de vínculo
 Puede agregar más de una directiva de conexión de vínculo a un generador de conexiones. Esto puede ayudar a ocultar algunas de las complejidades del modelo de dominio de los usuarios y mantener la **cuadro de herramientas** llene demasiado. Puede agregar directivas de conexión de vínculo para varias relaciones de dominio diferentes a un único generador de conexiones. Sin embargo, debe combinar las relaciones de dominio cuando realicen aproximadamente la misma función.

 En la solución de flujo de tareas, el **flujo** herramienta de conexión se usa para dibujar instancias tanto el **flujo** y el **ObjectFlow** relaciones de dominio. El **FlowBuilder** generador de conexiones tiene, además la **flujo** conexión de vínculo de directiva se ha descrito anteriormente, denominadas de directivas de conexión de vínculo dos **ObjectFlow**. Estas directivas especifican que una instancia de un **ObjectFlow** se puede dibujar la relación entre las instancias de la **ObjectInState** la clase de dominio, o desde una instancia de un **ObjectInState**  a una instancia de un **tarea**, pero no entre dos instancias de un **tarea**, o desde una instancia de un **tarea** a una instancia de un **ObjectInState**. Sin embargo, una instancia de un **flujo** se puede dibujar la relación entre dos instancias de un **tarea**. Si compila y ejecuta la solución de flujo de tareas, puede ver ese plano un **flujo** desde una instancia de un **ObjectInState** a una instancia de un **tarea** crea una instancia de un **ObjectFlow**, dibujo, pero un **flujo** entre dos instancias de un **tarea** crea una instancia de un **flujo**.

### <a name="custom-code-for-connection-builders"></a>Código personalizado para generadores de conexiones
 Hay cuatro casillas en la interfaz de usuario que definen los diferentes tipos de personalización de los generadores de conexiones:

- el **aceptación personalizada** casilla de verificación de una directiva de rol de origen o destino

- el **conexión personalizada** casilla de verificación de una directiva de rol de origen o destino

- el **usa conexión personalizada** casilla de verificación de una directiva de conexión

- el **Is Custom** propiedad del generador de conexión

  Debe proporcionar algún código de programa para realizar estas personalizaciones. Para averiguar qué código debe proporcionar, seleccione una de estas casillas, haga clic en Transformar todas las plantillas y, después, compile su solución. Se producirá un informe de error. Haga doble clic en el informe de error para ver un comentario que explica qué código debe agregar.

> [!NOTE]
>  Para agregar código personalizado, cree una definición de clase parcial en un archivo de código diferente de los archivos de código de las carpetas GeneratedCode. Para evitar perder su trabajo, no edite los archivos de código generados. Para obtener más información, consulte [invalidar y ampliar las clases generadas](../modeling/overriding-and-extending-the-generated-classes.md).

#### <a name="creating-custom-connection-code"></a>Crear código para conexiones personalizadas
 En cada vínculo conectar directiva, el **directivas de rol de origen** ficha define desde qué tipos pueden arrastrar. De forma similar, el **directivas de rol de destino** ficha define a qué tipos pueden arrastrar. Para cada tipo, se puede especificar si se permite la conexión (para la directiva de conexión de ese vínculo) estableciendo el **aceptación personalizada** marca y, a continuación, proporcione el código extra.

 También puede personalizar lo que ocurre cuando se realiza la conexión. Por ejemplo, puede personalizar solo el caso en el que se arrastra hacia o desde una clase determinada, todos los casos que se rigen por una directiva de conexión de vínculo o todo el generador de conexiones FlowBuilder. Para cada una de estas opciones, puede establecer marcas personalizadas en el nivel correspondiente. Cuando se transforman todas las plantillas y se intenta compilar la solución, los mensajes de error le dirigen a comentarios que hay en el código generado. Estos comentarios identifican qué debe proporcionar.

 En la muestra del diagrama de componentes, el generador de conexiones de la relación de dominio Connection se personaliza para restringir las conexiones que se pueden realizar entre los puertos. La ilustración siguiente muestra que puede realizar conexiones solo desde elementos `OutPort` a elementos `InPort`, pero puede anidar unos componentes dentro de otros.

 **Conexión que llega a un OutPort desde un componente anidado**

 ![Generador de conexiones](../modeling/media/connectionbuilder_3.png)

 Por este motivo, quizás quiera especificar que una conexión puede ir dirigida desde un componente anidado hacia un OutPort. Para especificar una conexión de este tipo, establezca **usa aceptación personalizada** en el **InPort** tipo como rol de origen y el **OutPort** tipo como rol de destino en el **detalles de DSL**  ventana tal y como se muestra en las ilustraciones siguientes:

 **Vínculo de directiva de conexión en el Explorador de DSL**

 ![Imagen de generador de conexiones](../modeling/media/connectionbuilder_4a.png)

 **Vínculo de directiva de conexión en la ventana de detalles de DSL**

 ![](../modeling/media/connectionbuilder_4b.png)

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
    private static bool CanAcceptInPortAndInPortAsSourceAndTarget                (InPort sourceInPort, InPort targetInPort)
    {
      return sourceInPort.Component == targetInPort.Component.Parent;
    }
// And similar for OutPorts...
```

 Para obtener más información acerca de cómo personalizar el modelo mediante el uso de código de programa, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

 Puede usar un código similar, por ejemplo, para evitar que los usuarios creen bucles en vínculos de elementos primarios y secundarios. Estas restricciones se consideran las restricciones 'hard' porque los usuarios no pueden infringirlas en cualquier momento. También puede crear comprobaciones de validación 'soft' que los usuarios pueden omitir temporalmente creando configuraciones no válidas que no se puede guardar.

### <a name="good-practice-in-defining-connection-builders"></a>Procedimientos recomendados para definir generadores de conexiones
 Debe definir un generador de conexiones para crear diferentes tipos de relaciones solo si están conceptualmente relacionados. En la muestra del flujo de tareas, use el mismo generador para crear los flujos entre las tareas y entre las tareas y los objetos. Sin embargo, resultaría confuso usar el mismo generador para crear relaciones entre comentarios y tareas.

 Si define un generador de conexiones para varios tipos de relaciones, debe asegurarse de que no se corresponda con más de un tipo del mismo par de objetos de origen y destino. De lo contrario, los resultados serán impredecibles.

 Usar código personalizado para aplicar las restricciones 'hard' pero debería considerar si los usuarios deben poder hacer temporalmente las conexiones no válidas. En caso de que deban, puede modificar las restricciones para que las conexiones no se validen hasta que los usuarios intenten guardar los cambios.

## <a name="see-also"></a>Vea también

- [Personalizar la creación y el movimiento de los elementos](../modeling/customizing-element-creation-and-movement.md)
- [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)
- [Cómo: Agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Ejemplo de diagramas de circuitos DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)