---
title: Agregar comandos y gestos a diagramas de dependencia
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8e985aecf317d0bf66a77d0dd0c08a3f141f6193
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909989"
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Agregar comandos y gestos a diagramas de dependencia

Puede definir comandos del menú contextual y controladores de gestos en diagramas de dependencia en Visual Studio. Estas extensiones se pueden empaquetar en una extensión de integración de Visual Studio (VSIX) que luego puede distribuir a otros usuarios de Visual Studio.

Si lo desea, puede definir varios controladores de comandos y gestos en el mismo proyecto de Visual Studio. También puede combinar varios proyectos de este tipo en un VSIX. Por ejemplo, podría definir un VSIX único que incluye comandos de capa y un lenguaje específico de dominio.

> [!NOTE]
> También puede personalizar la validación de arquitectura, en la fuente de que los usuarios se compara código con diagramas de dependencia. La validación de arquitectura debe definirse en un proyecto de Visual Studio independiente. Puede agregarlo al mismo VSIX que otras extensiones. Para obtener más información, consulte [agregar validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

## <a name="requirements"></a>Requisitos

Vea [Requisitos](../modeling/extend-layer-diagrams.md#prereqs).

## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Definir un comando o gesto en un nuevo VSIX

El método más rápido para crear una extensión consiste en usar la plantilla de proyecto. Esto coloca el código y el manifiesto de VSIX en el mismo proyecto.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Para definir una extensión mediante una plantilla de proyecto

1. Cree un proyecto en una nueva solución mediante el comando **Nuevo proyecto** del menú **Archivo** .

2. En el cuadro de diálogo **Nuevo proyecto** , en **Proyectos de modelado**, seleccione **Layer Designer Command Extension** (Extensión de comandos del diseñador de capas) o **Layer Designer Gesture Extension**(Extensión de gestos del diseñador de capas).

    La plantilla crea un proyecto que contiene un pequeño ejemplo funcional.

3. Para probar la extensión, presione **Ctrl**+**F5** o **F5**.

    Inicia una instancia experimental de Visual Studio. En este caso, cree un diagrama de dependencia. El comando o extensión de gesto debería funcionar en este diagrama.

4. Cierre la instancia experimental y modifique el código de muestra. Para obtener más información, consulte [navegación y actualización de modelos en el código de programa capa](../modeling/navigate-and-update-layer-models-in-program-code.md).

5. Puede agregar más controladores de comandos o de gestos al mismo proyecto. Para obtener más información, vea una de las secciones siguientes:

    [Definir un comando de menú](#command)

    [Definir un controlador de gestos](#gesture)

6. Para instalar la extensión en la instancia principal de Visual Studio o en otro equipo, busque el *.vsix* de archivos en el *bin* directory. Cópielo en el equipo donde desea instalarlo y, a continuación, haga doble clic en él. Para desinstalarla, elija **extensiones y actualizaciones** en el **herramientas** menú.

## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Agregar un comando o gesto a un VSIX independiente

Si desea crear un VSIX que contenga comandos, validadores de capas y otras extensiones, le recomendamos que cree un proyecto para definir VSIX y proyectos independientes para los controladores.

### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Para agregar extensiones de nivel a un VSIX independiente

1.  Cree un proyecto de biblioteca de clases en una solución de Visual Studio nueva o en una existente. En el cuadro de diálogo **Nuevo proyecto** , haga clic en **Visual C#** y haga clic en **Biblioteca de clases**. Este proyecto contendrá clases de controlador de comandos o de gestos.

    > [!NOTE]
    > Puede definir más de una clase de controlador de comandos o de gestos en una biblioteca de clases, pero debe definir las clases de validación de capas en una biblioteca de clases independiente.

2.  Identifique o cree un proyecto de VSIX en la solución. Un proyecto de VSIX contiene un archivo denominado **source.extension.vsixmanifest**. Para agregar una clase a un proyecto de VSIX:

    1.  En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual C#**, haga clic en **Extensibility**(Extensibilidad) y, a continuación, en **VSIX Project**(Proyecto de VSIX).

    2.  En el Explorador de soluciones, haga clic con el botón secundario en el proyecto de VSIX y, a continuación, haga clic en **Establecer como proyecto de inicio**.

    3.  Haga clic en **Seleccionar ediciones** y asegúrese de que **Visual Studio** está activado.

3.  En **source.extension.vsixmanifest**, en **Activos**, agregue el proyecto de controlador de comandos o de gestos como componente MEF.

    1.  En la pestaña **Activos**, elija **Nuevo**.

    2.  En **Tipo**, seleccione **Microsoft.VisualStudio.MefComponent**.

    3.  En **Origen**seleccione el **proyecto de la solución actual** y seleccione el nombre del proyecto de controlador de comandos o de gestos.

    4.  Guarde el archivo.

4.  Vuelva al proyecto de controlador de comandos o gestos y agregue las siguientes referencias de proyecto:

   |**Referencia**|**Qué permite hacer**|
   |-|-|
   |Archivos de programa\Microsoft Visual Studio [versión]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Crear y modificar las capas|
   |Microsoft.VisualStudio.Uml.Interfaces|Crear y modificar las capas|
   |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modificar formas en los diagramas|
   |System.ComponentModel.Composition|Definir componentes mediante MEF (Managed Extensibility Framework)|
   |Microsoft.VisualStudio.Modeling.Sdk.[versión]|Definir las extensiones de modelado|
   |Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]|Actualizar formas y diagramas|

5.  Edite el archivo de clases en el proyecto de biblioteca de clases de C# para que contenga el código de la extensión. Para obtener más información, vea una de las secciones siguientes:

     [Definir un comando de menú](#command)

     [Definir un controlador de gestos](#gesture)

     Vea también [navegación y actualización de modelos en el código de programa capa](../modeling/navigate-and-update-layer-models-in-program-code.md).

6.  Para probar la característica, presione CTRL+F5 o F5. Se abre una instancia experimental de Visual Studio. En este caso, cree o abra un diagrama de dependencia.

7.  Para instalar VSIX en la instancia principal de Visual Studio o en otro equipo, busque el **.vsix** de archivos en el **bin** directorio del proyecto VSIX. Cópielo en el equipo donde desea instalar VSIX. En el Explorador de Windows, haga doble clic en el archivo VSIX.

     Para desinstalarla, use **Extensiones y actualizaciones** en el menú **Herramientas** .

##  <a name="command"></a> Definir un comando de menú

Puede agregar más definiciones de comando de menú a un proyecto de gesto o comando existente. Cada comando se define con una clase que tiene las siguientes características:

- La clase se declara de la siguiente forma:

   `[LayerDesignerExtension]`

   `[Export(typeof(ICommandExtension))]`

   `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`

- El espacio de nombres y el nombre de la clase son insignificantes.

- Los métodos que implementan `ICommandExtension` son los siguientes:

  -   `string Text {get;}` - La etiqueta que aparece en el menú.

  -   `void QueryStatus(IMenuCommand command)` - se le llama cuando el usuario hace clic con el botón secundario en el diagrama y determina si el comando debería estar visible y habilitado para la selección actual del usuario.

  -   `void Execute(IMenuCommand command)` - se le llama cuando el usuario selecciona el comando.

- Para determinar la selección actual, puede importar `IDiagramContext`:

   `[Import]`

   `public IDiagramContext DiagramContext { get; set; }`

   `...`

   `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`

Para obtener más información, consulte [navegación y actualización de modelos en el código de programa capa](../modeling/navigate-and-update-layer-models-in-program-code.md).

Para agregar un nuevo comando, cree un nuevo archivo de código que contenga el siguiente ejemplo. A continuación, pruébelo y modifíquelo.

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtension // Change to your preference.
{
  // This is a feature for dependency diagrams:
  [LayerDesignerExtension]
  // This feature is a menu command:
  [Export(typeof(ICommandExtension))]
  // Change the class name to your preference:
  public class MyLayerCommand : ICommandExtension
  {
    [Import]
    public IDiagramContext DiagramContext { get; set; }

    [Import]
    public ILinkedUndoContext LinkedUndoContext { get; set; }

    // Menu command label:
    public string Text
    {
      get { return "Duplicate layers"; }
    }

    // Called when the user right-clicks the diagram.
    // Defines whether the command is visible and enabled.
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible =
      command.Enabled = DiagramContext.CurrentDiagram
        .SelectedShapes.Count() > 0;
    }

    // Called when the user selects the command.
    public void Execute(IMenuCommand command)
    {
      // A selection of starting points:
      IDiagram diagram = this.DiagramContext.CurrentDiagram;
      ILayerModel lmodel = diagram.GetLayerModel();
      foreach (ILayer layer in lmodel.Layers)
      { // All layers in model.
      }
      // Updates should be performed in a transaction:
      using (ILinkedUndoTransaction t =
        LinkedUndoContext.BeginTransaction("copy selection"))
      {
        foreach (ILayer layer in
          diagram.SelectedShapes
            .Select(shape=>shape.GetLayerElement())
            .Where(element => element is ILayer))
        {
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");
          // Position the shapes:
          IShape originalShape = layer.GetShape();
          copy.GetShape().Move(
            originalShape.XPosition + originalShape.Width * 1.2,
            originalShape.YPosition);
        }
        t.Commit();
      }
    }
  }
}
```

##  <a name="gesture"></a> Definir un controlador de gestos

Un controlador de gestos responde cuando el usuario arrastra elementos hasta el diagrama de dependencia, y cuando el usuario hace doble clic en cualquier lugar en el diagrama.

En el proyecto de VSIX existente de controlador de comandos o gestos, puede agregar un archivo de código que defina un controlador de gestos:

```csharp
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using System.ComponentModel.Composition;
using System.Linq;

namespace MyLayerExtensions // change to your preference
{
  [LayerDesignerExtension]
  [Export(typeof(IGestureExtension))]
  public class MyLayerGestureHandler : IGestureExtension
  {
  }
}
```

Observe los siguientes aspectos sobre los controladores de gestos:

-   Los miembros de `IGestureExtension` son los siguientes:

     **OnDoubleClick** : se le llama cuando el usuario hace doble clic en cualquier parte en el diagrama.

     **CanDragDrop** : se le llama repetidamente cuando el usuario mueve el mouse mientras arrastra un elemento al diagrama. Debe funcionar rápidamente.

     **OnDragDrop** : se le llama cuando el usuario coloca un elemento en el diagrama.

-   El primer argumento de cada método es `IShape`, a partir del cual puede obtener el elemento de capa. Por ejemplo:

    ```csharp
    public void OnDragDrop(IShape target, IDataObject data)
    {
        ILayerElement element = target.GetLayerElement();
        if (element is ILayer)
        {
            // ...
        }
    }
    ```

-   Ya se han definido los controladores para algunos tipos de elemento arrastrado. Por ejemplo, el usuario puede arrastrar elementos desde el Explorador de soluciones hasta un diagrama de dependencia. No puede definir un controlador de arrastre para estos tipos de elemento. En estos casos, no se invocarán los métodos `DragDrop` .

## <a name="see-also"></a>Vea también

- [Navegar y actualizar modelos de capas en el código del programa](../modeling/navigate-and-update-layer-models-in-program-code.md)
- [Adición de validación de arquitectura personalizada a diagramas de dependencia](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)
