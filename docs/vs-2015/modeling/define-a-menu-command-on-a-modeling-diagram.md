---
title: Define a menu command on a modeling diagram | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23ba1a6900559d7ee13639bb1da696127e47e536
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299268"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Definir un comando de menú en un diagrama de modelado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En Visual Studio, puede definir elementos de menú adicionales en los menús contextuales de un diagrama UML. Puede controlar si el comando de menú aparece y está habilitado en el menú contextual de cualquier elemento del diagrama, y puede escribir código que se ejecute cuando el usuario elija el elemento de menú. Puede empaquetar estas extensiones en una extensión de integración de Visual Studio ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) y distribuirla a otros usuarios de Visual Studio.

## <a name="requirements"></a>Requisitos
 Vea [Requisitos](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Definir el comando de menú
 Para crear un comando de menú para un diseñador UML, debe crear una clase que defina el comportamiento del comando e incrustarla en una extensión de integración de Visual Studio (VSIX). Las extensiones VSIX actúan como contenedores que instalan el comando. Hay dos métodos para definir un comando de menú:

- **Create a menu command in its own VSIX using a project template.** Este es el método más rápido. Utilícelo si no desea combinar los comandos de menú con otros tipos de extensión, como las extensiones de validación, los elementos de cuadro de herramientas personalizados o los controladores de gestos.

- **Create separate menu command and VSIX projects.** Use este método si desea combinar varios tipos de extensiones en la misma VSIX. Por ejemplo, si el comando de menú espera que el modelo respete restricciones concretas, podría incrustarlo en la misma VSIX como método de validación.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Para crear un comando de menú en una VSIX

1. En el cuadro de diálogo **Nuevo proyecto** , en **Proyectos de modelado**, seleccione **Extensión de comando**.

2. Abra el archivo **.cs** en el nuevo proyecto y modifique la clase `CommandExtension` para implementar el comando.

    Para obtener más información, vea [Implementar el comando de menú](#Implementing).

3. Puede agregar comandos adicionales a este proyecto mediante la definición de nuevas clases.

4. Pruebe el comando de menú presionando F5. Para obtener más información, vea [Ejecutar el comando de menú](#Executing).

5. Install the menu command on another computer by copying the file **bin\\\*\\\*.vsix** that is built by your project. Para obtener más información, vea [Instalar y desinstalar una extensión](#Installing).

   A continuación se muestra el procedimiento alternativo:

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Para crear un comando de menú en un proyecto de biblioteca de clases (DLL) independiente

1. Cree un proyecto de biblioteca de clases en una nueva solución de Visual Studio o en una solución existente.

   1. En el menú **Archivo** , elija **Nuevo**, **Proyecto**.

   2. En **Plantillas instaladas**, seleccione **Visual C#** o **Visual Basic**. En la columna central, elija **Biblioteca de clases**.

   3. Establezca **Solución** para indicar si desea crear una nueva solución o agregar un componente a una solución VSIX que ya tiene abierta.

   4. Especifique el nombre y la ubicación del proyecto, y haga clic en Aceptar.

2. Agregue las referencias siguientes al proyecto.

   |                                                                                                    Referencia                                                                                                    |                                                                                                  Qué permite hacer                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Defina los componentes mediante [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Leer y modificar las propiedades de los elementos del modelo.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Crear elementos del modelo y modificar formas en los diagramas.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[versión]                                                                                  | Definir controladores de eventos del modelo.<br /><br /> Encapsular series de cambios en el modelo. For more information, see [Link UML model updates by using transactions](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]<br /><br /> (no siempre es necesario)                                                             |                                                                                   Obtener acceso a elementos del diagrama adicionales para controladores de gestos.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Solo se requiere para los comandos en diagramas de capas. For more information, see [Extend layer diagrams](../modeling/extend-layer-diagrams.md). |                                                                                             Definir los comandos en un diagrama de capas.                                                                                              |

3. Agregue un archivo de clase al proyecto y establezca su contenido en el código siguiente.

   > [!NOTE]
   > Cambie el espacio de nombres, el nombre de clase y el valor devuelto por `Text` como prefiera.
   >
   >  Si se definen varios comandos, estos aparecerán en el menú en orden alfabético de los nombres de clase.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Uml.Classes;
       // ADD other UML namespaces if required

   namespace UMLmenu1 // CHANGE
   {
     // DELETE any of these attributes if the command
     // should not appear in some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // All menu commands must export ICommandExtension:
     [Export (typeof(ICommandExtension))]
     // CHANGE class name – determines order of appearance on menu:
     public class Menu1 : ICommandExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       public void QueryStatus(IMenuCommand command)
       { // Set command.Visible or command.Enabled to false
         // to disable the menu command.
         command.Visible = command.Enabled = true;
       }

       public string Text
       {
         get { return "MENU COMMAND LABEL"; }
       }

       public void Execute(IMenuCommand command)
       {
         // A selection of starting points:
         IDiagram diagram = this.DiagramContext.CurrentDiagram;
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
         { IElement element = shape.Element; }
         IModelStore modelStore = diagram.ModelStore;
         IModel model = modelStore.Root;
         foreach (IElement element in modelStore.AllInstances<IClass>())
         { }
       }
     }
   }
   ```

    Para obtener más información acerca de qué poner en los métodos, vea [Implementar el comando de menú](#Implementing).

   Debe agregar el comando de menú a un proyecto VSIX, que actúa como contenedor para instalar el comando. Si lo desea, puede incluir otros componentes en el mismo VSIX.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Para agregar un comando de menú a un proyecto VSIX

1. No necesita este procedimiento si ha creado el comando de menú con un VSIX propio.

2. Cree un proyecto VSIX, a menos que la solución ya tenga uno.

    1. En el **Explorador de soluciones**, en el menú contextual de la solución, elija **Agregar**, **Nuevo proyecto**.

    2. En **Plantillas instaladas**, expanda **Visual C#** o **Visual Basic**y, a continuación, elija **Extensibilidad**. En la columna central, elija **Proyecto VSIX**.

3. En el Explorador de soluciones, en el menú contextual del proyecto VSIX, elija **Establecer como proyecto de inicio**.

4. Abra **source.extension.vsixmanifest**.

    1. En la pestaña **Metadatos** , establezca un nombre para VSIX.

    2. En la pestaña **Destinos de instalación** , establezca las versiones de Visual Studio como destinos.

    3. En la pestaña **Activos** , elija **Nuevo**y, en el cuadro de diálogo, establezca:

         **Tipo** = **Componente MEF**

         **Origen** = **Un proyecto de la solución actual**

         **Proyecto** = *Su proyecto de biblioteca de clases*

## <a name="Implementing"></a> Implementing the Menu Command
 La clase del comando de menú implementa los métodos necesarios para <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.

|||
|-|-|
|`string Text { get; }`|Devuelve la etiqueta del elemento de menú.|
|`void QueryStatus(IMenuCommand command);`|Se llama cuando el usuario hace clic con el botón secundario del mouse en el diagrama.<br /><br /> Este método no debería cambiar el modelo.<br /><br /> Utilice `DiagramContext.CurrentDiagram.SelectedShapes` para especificar si desea que el comando aparezca y esté habilitado.<br /><br /> Establezca:<br /><br /> -   `command.Visible` to `true` if the command must appear in the menu when the user right-clicks in the diagram<br />-   `command.Enabled` to `true` if the user can click the command in the menu<br />-   `command.Text` to set the menu label dynamically|
|`void Execute (IMenuCommand command);`|Se llama cuando el usuario hace clic en el elemento de menú, siempre que esté visible y habilitado.|

### <a name="accessing-the-model-in-code"></a>Tener acceso al modelo en el código
 Incluya la siguiente declaración en la clase de comando de menú:

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 La declaración de `IDiagramContext` le permite escribir en los métodos código que tiene acceso al diagrama, la selección actual y el modelo:

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Navegar y actualizar el modelo
 Los elementos del modelo UML están todos disponibles a través de la API. Desde la selección actual o la raíz del modelo, puede tener acceso a todos los demás elementos. For more information, see [Navigate the UML model](../modeling/navigate-the-uml-model.md) and [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 If you are dealing with a sequence diagram, see also [Edit UML sequence diagrams by using the UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 La API también le permite cambiar las propiedades de los elementos, eliminar elementos y relaciones, y crear nuevos elementos y relaciones.

 De forma predeterminada, cada cambio que efectúe en el método Execute se realizará en una transacción independiente. El usuario podrá deshacer cada cambio independientemente. If you want to group the changes into a single transaction, use a <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> as described in [Link UML model updates by using transactions](../modeling/link-uml-model-updates-by-using-transactions.md).

### <a name="use-the-ui-thread-for-updates"></a>Usar el subproceso de la interfaz de usuario en las actualizaciones
 En ciertos casos, puede resultar útil hacer actualizaciones en el modelo desde un subproceso en segundo plano. Por ejemplo, si el comando carga datos de un recurso que es lento, puede realizar la carga en un subproceso en segundo plano para que el usuario pueda ver los cambios mientras se producen y cancelar la operación si fuera necesario.

 Sin embargo, debe tener en cuenta que el almacén de modelos no es seguro para subprocesos. Siempre debe usar el subproceso de la interfaz de usuario para realizar las actualizaciones y, si es posible, evitar que el usuario realice modificaciones mientras la operación en segundo plano está en curso. For an example, see [Update a UML model from a background thread](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="Executing"></a> Executing the Menu Command
 A efectos de prueba, ejecute el comando en modo de depuración.

#### <a name="to-test-the-menu-command"></a>Para probar el comando de menú

1. Presione **F5**o, en el menú **Depurar** , elija **Iniciar depuración**.

     Se iniciará una instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Solución de problemas**: si no se inicia un nuevo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

    - Si tiene más de un proyecto, asegúrese de que el proyecto VSIX está configurado como proyecto de inicio de la solución.

    - En el Explorador de soluciones, en el menú contextual del proyecto de inicio o único, elija **Propiedades**. In the project properties editor, select the **Debug** tab. Make sure that the string in the **Start external program** field is the full pathname of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], typically:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra o cree un proyecto de modelado, y abra o cree un diagrama de modelado. Use un diagrama que pertenezca a uno de los tipos que aparecen en la lista de atributos de la clase del comando de menú.

3. Abra el menú contextual en cualquier parte del diagrama. El comando debería aparecer en el menú.

     **Solución de problemas**: si el comando no aparece en el menú, asegúrese de que:

    - El proyecto de comando de menú aparece como componente MEF en la pestaña **Activos** de **source.extensions.manifest** en el proyecto VSIX.

    - Los parámetros de los atributos `Import` e `Export` son válidos.

    - The `QueryStatus` method is not setting the `command`.`Enabled` o `Visible` en `false`.

    - El tipo de diagrama del modelo que está usando (secuencia, clases UML, etc.) se muestra como uno de los atributos de la clase del comando de menú `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` etc.

## <a name="Installing"></a> Installing and uninstalling an extension
 Puede instalar una extensión de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] en su propio equipo y en otros equipos.

#### <a name="to-install-an-extension"></a>Para instalar una extensión

1. En el equipo, busque el archivo **.vsix** compilado en el proyecto VSIX.

    1. En el **Explorador de soluciones**, en el menú contextual del proyecto VSIX, elija **Abrir carpeta en el Explorador de Windows**.

    2. Locate the file **bin\\\*\\** _YourProject_ **.vsix**

2. Copie el archivo **.vsix** en el equipo de destino en el que desea instalar la extensión. Puede tratarse de su propio equipo o de otro.

     El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que especificó en **source.extension.vsixmanifest**.

3. En el equipo de destino, abra el archivo **.vsix** , por ejemplo, haciendo doble clic en él.

     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Para desinstalar una extensión

1. En el menú **Herramientas** , elija **Extensiones y actualizaciones**.

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión y, a continuación, elija **Desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:

   *%LocalAppData%* **\Local\Microsoft\VisualStudio\\[version]\Extensions**

## <a name="MenuExample"></a> Ejemplo
 En el ejemplo siguiente se muestra el código de un comando de menú que intercambiará los nombres de dos elementos en un diagrama de clases. Este código debe compilarse en un proyecto de extensión de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e instalarse tal y como se describió en las secciones anteriores.

```
using System.Collections.Generic; // for IEnumerable
using System.ComponentModel.Composition;
  // for [Import], [Export]
using System.Linq; // for IEnumerable extensions
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
  // for IDiagramContext
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
  // for designer extension attributes
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext
using Microsoft.VisualStudio.Uml.Classes;
  // for class diagrams, packages

/// <summary>
/// Extension to swap names of classes in a class diagram.
/// </summary>
namespace SwapClassNames
{
  // Declare the class as an MEF component:
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  // Add more ExportMetadata attributes to make
  // the command appear on diagrams of other types.
  public class NameSwapper : ICommandExtension
  {
  // MEF required interfaces:
  [Import]
  public IDiagramContext Context { get; set; }
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  /// <param name="command"></param>
  public void Execute(IMenuCommand command)
  {
    // Get selected shapes that are IClassifiers -
    // IClasses, IInterfaces, IEnumerators.
    var selectedShapes = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;

    // Get model elements displayed by shapes.
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;

    // Do the swap in a transaction so that user
    // cannot undo one change without the other.
    using (ILinkedUndoTransaction transaction =
    LinkedUndoContext.BeginTransaction("Swap names"))
    {
    string firstName = firstElement.Name;
    firstElement.Name = lastElement.Name;
    lastElement.Name = firstName;
    transaction.Commit();
    }
  }

  /// <summary>
  /// Called by Visual Studio to determine whether
  /// menu item should be visible and enabled.
  /// </summary>
  public void QueryStatus(IMenuCommand command)
  {
    int selectedClassifiers = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>().Count();
    command.Visible = selectedClassifiers > 0;
    command.Enabled = selectedClassifiers == 2;
  }

  /// <summary>
  /// Name of the menu command.
  /// </summary>
  public string Text
  {
    get { return "Swap Names"; }
  }
  }

}
```

## <a name="see-also"></a>Vea también
 [Define and install a modeling extension](../modeling/define-and-install-a-modeling-extension.md) [Extend UML models and diagrams](../modeling/extend-uml-models-and-diagrams.md) [Define a gesture handler on a modeling diagram](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Define a custom modeling toolbox item](../modeling/define-a-custom-modeling-toolbox-item.md) [Define validation constraints for UML models](../modeling/define-validation-constraints-for-uml-models.md) [Edit UML sequence diagrams by using the UML API](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) [Programming with the UML API](../modeling/programming-with-the-uml-api.md) [Sample: Command to Align Shapes on a UML Diagram](https://go.microsoft.com/fwlink/?LinkID=213809)
