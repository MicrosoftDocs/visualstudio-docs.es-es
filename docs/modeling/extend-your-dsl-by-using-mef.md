---
title: Ampliar DSL mediante MEF
description: Obtenga información sobre cómo puede ampliar el lenguaje específico de dominio (DSL) mediante el Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388885"
---
# <a name="extend-your-dsl-by-using-mef"></a>Ampliar DSL mediante MEF

Puede ampliar el lenguaje específico del dominio (DSL) mediante Managed Extensibility Framework (MEF). Usted u otros desarrolladores podrán escribir extensiones para el DSL sin cambiar la definición de DSL y el código del programa. Estas extensiones incluyen comandos de menú, controladores de arrastrar y colocar y validación. Los usuarios podrán instalar el DSL y, opcionalmente, instalar extensiones para él.

Además, al habilitar MEF en el DSL, puede ser más fácil escribir algunas de las características del DSL, incluso si todas se han creado junto con el DSL.

Para obtener más información sobre MEF, [vea Managed Extensibility Framework (MEF).](/dotnet/framework/mef/index)

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Para permitir que MEF pueda ampliar el DSL

1. Cree una carpeta denominada **MefExtension dentro** del **proyecto DslPackage.** Agregue los siguientes archivos:

     Nombre de archivo: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Establezca el GUID de este archivo para que sea el mismo que el valor de CommandSetId de GUID que se define en DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Nombre de archivo: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Nombre de archivo: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Nombre de archivo: `ValidationExtensionRegistrar.tt`

    Si agrega este archivo, debe habilitar la validación en el DSL mediante al menos uno de los modificadores de **EditorValidation** en el Explorador dsl.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nombre de archivo: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Cree una carpeta denominada **MefExtension dentro** del **proyecto dsl.** Agregue los siguientes archivos:

     Nombre de archivo: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Nombre de archivo: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Nombre de archivo: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Agregue la siguiente línea al archivo existente denominado **DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Inserte la línea después de la directiva `<Include>` existente.

4. Abra *DslDefinition.dsl.*

5. En el Explorador DSL, seleccione **Editor\Validation**.

6. En la ventana Propiedades, asegúrese de que al menos una de las propiedades **denominadas Usa** es `true` .

7. En la barra **Explorador de soluciones** de herramientas, haga clic **en Transformar todas las plantillas.**

     Los archivos subsidiarias aparecen debajo de cada uno de los archivos que ha agregado.

8. Compile y ejecute la solución para comprobar que sigue funcionando.

El DSL ahora está habilitado para MEF. Puede escribir comandos de menú, controladores de gestos y restricciones de validación como extensiones MEF. Puede escribir estas extensiones en la solución DSL junto con otro código personalizado. Además, usted u otros desarrolladores pueden escribir extensiones de Visual Studio independientes que amplían el DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Creación de una extensión para un DSL habilitado para MEF

Si tiene acceso a un DSL habilitado para MEF creado por usted mismo o por otra persona, puede escribir extensiones para él. Las extensiones se pueden usar para agregar comandos de menú, controladores de gestos o restricciones de validación. Para crear estas extensiones, use una solución Visual Studio de extensión (VSIX). La solución tiene dos partes: un proyecto de biblioteca de clases que compila el ensamblado de código y un proyecto VSIX que empaqueta el ensamblado.

### <a name="to-create-a-dsl-extension-vsix"></a>Para crear una extensión DSL VSIX

1. Cree un proyecto de **Biblioteca de clases**.

2. En el nuevo proyecto, agregue una referencia al ensamblado del DSL.

   - Este ensamblado normalmente tiene un nombre que termina con ".Dsl.dll".

   - Si tiene acceso al proyecto DSL, puede encontrar el archivo de ensamblado en el directorio **Dsl \\ bin \\ \***

   - Si tiene acceso al archivo VSIX de DSL, puede encontrar el ensamblado cambiando la extensión de nombre de archivo del archivo VSIX a ".zip". Descomprime el .zip archivo.

3. Agregue referencias a los siguientes ensamblados de .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Cree un nuevo **proyecto VSIX.**

5. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto VSIX y elija **Establecer como proyecto de inicio.**

6. En el nuevo proyecto, abra **source.extension.vsixmanifest**.

7. Haga clic **en Agregar contenido.** En el cuadro de diálogo, establezca **Tipo de contenido** en Componente **MEF** y **Proyecto de origen** en el proyecto de biblioteca de clases.

8. Agregue una referencia de VSIX al DSL.

   1. En **source.extension.vsixmanifest, haga** clic **en Agregar referencia.**

   2. En el cuadro de diálogo, haga clic **en Agregar carga** y busque el archivo VSIX del DSL. El archivo VSIX se basa en la solución DSL, en **dslpackage \\ bin \\ \***.

       Esto permite a los usuarios instalar el DSL y la extensión al mismo tiempo. Si el usuario ya ha instalado el DSL, solo se instalará la extensión.

9. Revise y actualice los demás campos de **source.extension.vsixmanifest**. Haga **clic en Seleccionar ediciones** y compruebe que se han Visual Studio ediciones correctas.

10. Agregue código al proyecto de biblioteca de clases. Use los ejemplos de la sección siguiente como guía.

     Puede agregar cualquier número de clases de comandos, gestos y validación.

11. Para probar la extensión, presione **F5**. En la instancia experimental de Visual Studio, cree o abra un archivo de ejemplo del DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Escritura de extensiones MEF para DSL

Puede escribir extensiones en el proyecto de código de ensamblado de una solución de extensión DSL independiente. También puede usar MEF en el proyecto DslPackage, como una manera cómoda de escribir comandos, gestos y código de validación como parte del DSL.

### <a name="menu-commands"></a>Comandos de menú

Para escribir un comando de menú, defina una clase que implemente y antefie la clase con el atributo definido en el <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> DSL, denominado *YourDsl* `CommandExtension` . Puede escribir más de una clase de comando de menú.

`QueryStatus()` Se llama a cada vez que el usuario hace clic con el botón derecho en el diagrama. Debe inspeccionar la selección actual y establecer `command.Enabled` para indicar cuándo es aplicable el comando.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Controladores de gestos

Un controlador de gestos puede tratar con objetos arrastrados al diagrama desde cualquier lugar, dentro o fuera de Visual Studio. En el ejemplo siguiente se permite al usuario arrastrar archivos Explorador de Windows al diagrama. Crea elementos que contienen los nombres de archivo.

Puede escribir controladores para tratar con los arrastres de otros modelos DSL y modelos UML. Para obtener más información, [vea Cómo: Agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Restricciones de validación

Los métodos de validación están marcados por `ValidationExtension` el atributo generado por el DSL y también por <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . El método puede aparecer en cualquier clase que no esté marcada por un atributo .

Para obtener más información, [vea Validación en un Domain-Specific lenguaje .](../modeling/validation-in-a-domain-specific-language.md)

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Vea también

- [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [La validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)
