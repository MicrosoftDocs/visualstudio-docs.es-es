---
title: Ampliar DSL mediante MEF | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 378aab6aaac3c45dc0a912dc62f5ebf55fffd46c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573981"
---
# <a name="extend-your-dsl-by-using-mef"></a>Ampliar DSL mediante MEF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ampliar DSL mediante MEF](https://docs.microsoft.com/visualstudio/modeling/extend-your-dsl-by-using-mef).  
  
Puede ampliar su lenguaje específico de dominio (DSL) mediante el uso de Managed Extensibility Framework (MEF). Usted u otros desarrolladores podrán escribir extensiones para el DSL sin cambiar la definición de DSL y el código del programa. Estas extensiones incluyen comandos de menú, los controladores de arrastrar y colocar y la validación. Los usuarios podrán instalar su DSL y, opcionalmente, instalar extensiones para él.  
  
 Además, al habilitar MEF en su DSL, puede ser más fácil de escribir algunas de las características de su DSL, incluso si se crean junto con el DSL.  
  
 Para obtener más información acerca de MEF, vea [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Para habilitar su DSL sea ampliada por MEF  
  
1.  Cree una carpeta nueva denominada **MefExtension** dentro de la **DslPackage** proyecto. Agregue los siguientes archivos en ella:  
  
     Nombre de archivo: `CommandExtensionVSCT.tt`  
  
    > [!IMPORTANT]
    >  El GUID del conjunto de este archivo para ser el mismo que el que se define en DslPackage\GeneratedCode\Constants.tt CommandSetId de GUID  
  
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
  
     Si agrega este archivo, debe habilitar la validación en su DSL mediante el uso de al menos uno de los modificadores en **EditorValidation** en el Explorador de DSL.  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
    ```  
  
     Nombre de archivo: `PackageExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
    ```  
  
2.  Cree una carpeta nueva denominada **MefExtension** dentro de la **Dsl** proyecto. Agregue los siguientes archivos en ella:  
  
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
  
3.  Agregue la siguiente línea al archivo existente que se denomina **Dslpackage\commands**:  
  
    ```  
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
    ```  
  
     Inserte la línea después de la existente `<Include>` directiva.  
  
4.  `Open DslDefinition.dsl.`  
  
5.  En el Explorador de DSL, seleccione **Editor\Validation**.  
  
6.  En la ventana Propiedades, asegúrese de que al menos una de las propiedades con nombre **usa...**  es `true`.  
  
7.  En la barra de herramientas del explorador de soluciones, haga clic en **Transformar todas las plantillas**.  
  
     Archivos secundarios aparecen debajo de cada uno de los archivos que ha agregado.  
  
8.  Compile y ejecute la solución para comprobar que sigue funcionando.  
  
 Su DSL ya está habilitado de MEF. Puede escribir comandos de menú, los controladores de gestos y restricciones de validación como extensiones MEF. Puede escribir estas extensiones en la solución DSL, junto con otro código personalizado. Además, usted u otros desarrolladores pueden escribir independiente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensiones que amplían su DSL.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Creación de una extensión para un DSL MEF habilitado  
 Si tiene acceso a un DSL habilitado MEF creado por usted u otra persona, puede escribir las extensiones para él. Las extensiones se pueden usar para agregar las restricciones de validación, los controladores de gestos o comandos de menú. Para crear estas extensiones, usa un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución de extensión (VSIX). La solución tiene dos partes: un proyecto de biblioteca de clases que se compila el ensamblado de código y un proyecto VSIX que los paquetes del ensamblado.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>Para crear una extensión VSIX de DSL  
  
1.  Cree un nuevo proyecto de biblioteca de clases. Para ello, en el **nuevo proyecto** cuadro de diálogo, seleccione **Visual Basic** o **Visual C#** y, a continuación, seleccione **biblioteca de clases**.  
  
2.  En el nuevo proyecto de biblioteca de clases, agregue una referencia al ensamblado del DSL.  
  
    -   Normalmente, este ensamblado tiene un nombre que termina con ". DSL.dll".  
  
    -   Si tiene acceso al proyecto de DSL, puede encontrar el archivo de ensamblado en el directorio **Dsl\bin\\\***  
  
    -   Si tiene acceso al archivo VSIX de DSL, puede encontrar el ensamblado cambiando la extensión de nombre de archivo del archivo VSIX para "zip". Descomprima el archivo zip.  
  
3.  Agregue referencias a los ensamblados de .NET siguientes:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
    -   System.ComponentModel.Composition.dll  
  
    -   System.Windows.Forms.dll  
  
4.  Cree un proyecto VSIX en la misma solución. Para ello, en el **nuevo proyecto** cuadro de diálogo, expanda **Visual Basic** o **Visual C#**, haga clic en **extensibilidad**y, a continuación, seleccione  **Proyecto de VSIX**.  
  
5.  En el Explorador de soluciones, haga clic en el proyecto VSIX y, a continuación, haga clic en **establecer como proyecto de inicio**.  
  
6.  En el nuevo proyecto, abra **source.extension.vsixmanifest**.  
  
7.  Haga clic en **agregar contenido**. En el cuadro de diálogo, establezca **tipo de contenido** a **componente MEF**, y **proyecto de código fuente** a su proyecto de biblioteca de clases.  
  
8.  Agregue una referencia VSIX para el DSL.  
  
    1.  En **source.extension.vsixmanifest**, haga clic en **Agregar referencia**  
  
    2.  En el cuadro de diálogo, haga clic en **agregar carga** y, a continuación, busque el archivo VSIX del DSL. Generado en el archivo VSIX en la solución de DSL, **DslPackage\bin\\\***.  
  
         Esto permite a los usuarios instalar el DSL y la extensión al mismo tiempo. Si el usuario ya ha instalado el DSL, se instalará solo la extensión.  
  
9. Revisar y actualizar los demás campos de **source.extension.vsixmanifest**. Haga clic en **seleccionar ediciones** y compruebe que el valor correcto [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se establecen las ediciones.  
  
10. Agregue código al proyecto de biblioteca de clases. Utilice los ejemplos en la sección siguiente como guía.  
  
     Puede agregar cualquier número de clases de validación, gesto y comando.  
  
11. Para probar la extensión, presione **F5**. En la instancia experimental de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cree o abra un archivo de ejemplo del DSL.  
  
## <a name="writing-mef-extensions-for-dsls"></a>Escribir las extensiones MEF para DSL  
 Puede escribir las extensiones en el proyecto de código de ensamblado de una solución independiente de extensión DSL. También puede utilizar MEF en el proyecto DslPackage, como una manera cómoda de escribir código de validación, gestos y comandos como parte del DSL.  
  
### <a name="menu-commands"></a>Comandos de menú  
 Para escribir un comando de menú, defina una clase que implementa <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> y prefijo de la clase con el atributo que se define en su DSL, denominado *Sudsl*`CommandExtension`. Puede escribir más de una clase de comando de menú.  
  
 `QueryStatus()` se llama siempre que el usuario del botón secundario en el diagrama. Debe inspeccionar la selección actual y establecer `command.Enabled` para indicar si el comando es aplicable.  
  
```  
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
 Un controlador de gestos puede tratar con objetos que se arrastran al diagrama desde cualquier lugar dentro o fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. En el siguiente ejemplo permite al usuario arrastrar archivos desde el Explorador de Windows al diagrama. Crea los elementos que contienen los nombres de archivo.  
  
 Puede escribir controladores para tratar con arrastra desde otros modelos DSL y modelos UML. Para obtener más información, consulte [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
```  
  
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
 Los métodos de validación se marcan con el `ValidationExtension` atributo generado por el DSL y también por <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. El método puede aparecer en cualquier clase que no está marcado por un atributo.  
  
 Para obtener más información, consulte [validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
```  
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
 [Extensiones de Visual Studio de trasvase de registros](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [La validación en los lenguajes específicos de dominio](../modeling/validation-in-a-domain-specific-language.md)



