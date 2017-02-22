---
title: "C&#243;mo: ampliar el Dise&#241;ador de lenguaje espec&#237;fico de dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa807f1b-2780-491e-925b-abbfd31b2bfa
caps.latest.revision: 9
caps.handback.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# C&#243;mo: ampliar el Dise&#241;ador de lenguaje espec&#237;fico de dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear extensiones para el diseñador que se usa para editar las definiciones de DSL. Tipos de extensión que se puede realizar incluyen la adición de comandos de menú, agregar controladores para arrastrar y haga doble clic en movimientos y las reglas que se desencadenan cuando cambian de determinados tipos de relaciones o valores. Las extensiones pueden empaquetar como una extensión de integración de Visual Studio \(VSIX\) y distribuirse a otros usuarios.  
  
 Código de ejemplo y obtener más información sobre esta característica, vea Visual Studio [sitio Web de visualización y modelado de SDK \(VMSDK\)](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
## Configuración de la solución  
 Configurar un proyecto que contiene el código de la extensión y un proyecto VSIX que exporta el proyecto. La solución puede contener otros proyectos que se incorporan en el mismo VSIX.  
  
#### Para crear una solución de extensión de diseñador de DSL  
  
1.  Cree un nuevo proyecto mediante la plantilla de proyecto Biblioteca de clases. En el **nuevo proyecto** cuadro de diálogo, haga clic en **Visual C\#** y, a continuación, en la ventana central haga clic en **biblioteca de clases de**.  
  
     Este proyecto contendrá el código de las extensiones.  
  
2.  Cree un nuevo proyecto mediante la plantilla de proyecto VSIX. En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\#**, haga clic en **extensibilidad**, y, a continuación, en la selección de la ventana central **proyecto VSIX**.  
  
     Seleccione **Agregar a solución**.  
  
     Source.Extension.vsixmanifest se abre en el editor de manifiestos VSIX.  
  
3.  Sobre el campo de contenido, haga clic en **Agregar contenido**.  
  
4.  En el **Agregar contenido** cuadro de diálogo, establezca **Seleccionar un tipo de contenido** a **componente MEF**, y establecer **proyecto** a su proyecto de biblioteca de clases.  
  
5.  Haga clic en **Seleccionar ediciones** y asegúrese de que **Visual Studio Enterprise** está activada.  
  
6.  Asegúrese de que el proyecto VSIX es el proyecto de inicio de la solución.  
  
7.  En el proyecto de biblioteca de clases, agregue referencias a los siguientes ensamblados:  
  
     Microsoft.VisualStudio.CoreUtility  
  
     Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.DslDefinition.11.0  
  
     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0  
  
     System.ComponentModel.Composition  
  
     System.Drawing  
  
     System.Drawing.Design  
  
     System.Windows.Forms  
  
## Pruebas e implementación  
 Para probar cualquiera de las extensiones de este tema, compilar y ejecutar la solución. Se abre una instancia experimental de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. En esta instancia, abra una solución de DSL. Editar el diagrama DslDefinition. Puede ver el comportamiento de la extensión.  
  
 Para implementar las extensiones en el método main [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], y a otros equipos, siga estos pasos:  
  
1.  Busque el archivo de instalación de VSIX en el proyecto VSIX en bin\\\*\\\*.vsix  
  
2.  Copie este archivo en el equipo de destino y, a continuación, en el Explorador de Windows \(o explorador de archivos\), haga doble clic en él.  
  
     El [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] abre el Administrador de extensiones para confirmar que se ha instalado la extensión.  
  
 Para desinstalar la extensión, siga estos pasos:  
  
1.  en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], en el **herramientas** menú, haga clic en **Administrador de extensiones de**.  
  
2.  Seleccione la extensión y elimínelo.  
  
## Agregar un comando de menú contextual  
 Para que un comando de menú contextual aparezcan en la superficie del Diseñador de DSL o en la ventana del explorador de DSL, escribir una clase similar a la siguiente.  
  
 La clase debe implementar `ICommandExtension` y debe tener el atributo `DslDefinitionModelCommandExtension`.  
  
```  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.DslDesigner;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Command extending the DslDesigner.  
  /// </summary>  
  [DslDefinitionModelCommandExtension]   
  public class MyDslDesignerCommand : ICommandExtension  
  {  
    /// <summary>  
    /// Selection Context for this command  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Is the command visible and active?  
    /// This is called when the user right-clicks.  
    /// </summary>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Visible = true;  
      // Is there any selected DomainClasses in the Dsl explorer?  
      command.Enabled =   
        SelectionContext.AtLeastOneSelected<DomainClass>();  
  
      // Is there any selected ClassShape on the design surface?  
      command.Enabled |=   
        (SelectionContext.GetCurrentSelection<ClassShape>()  
                .Count() > 0);  
    }  
    /// <summary>  
    /// Executes the command   
    /// </summary>  
    /// <param name="command">Command initiating this action</param>  
    public void Execute(IMenuCommand command)  
    {  
      ...  
    }  
    /// <summary>  
    /// Label for the command  
    /// </summary>  
    public string Text  
    {  
      get { return "My Command"; }  
    }  
  }  
}  
```  
  
## Control de movimientos del Mouse  
 El código es similar al código del comando de menú.  
  
```  
[DslDefinitionModelGestureExtension]  
 class MouseGesturesExtensions : IGestureExtension  
 {  
  /// <summary>  
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box  
  /// </summary>  
  /// <param name="targetElement">Shape element on which the user has clicked</param>  
  /// <param name="diagramPointEventArgs">event args for this double-click</param>  
  public void OnDoubleClick(ShapeElement targetElement,  
       DiagramPointEventArgs diagramPointEventArgs)  
  {  
   ModelElement modelElement = PresentationElementHelper.  
        GetDslDefinitionModelElement(targetElement);  
   if (modelElement != null)  
   {  
    MessageBox.Show(string.Format(  
      "Double clicked on {0}", modelElement.ToString()),   
      "Model element double-clicked");  
   }  
  }  
  
  /// <summary>  
  /// Tells if the DslDesigner can consume the to-be-dropped information  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we try to drop</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>  
  public bool CanDragDrop(ShapeElement targetMergeElement,  
        DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    diagramDragEventArgs.Effect = DragDropEffects.Copy;  
    return true;  
   }  
   return false;  
  }  
  
  /// <summary>  
  /// Processes the drop by displaying the dropped text  
  /// </summary>  
  /// <param name="targetMergeElement">Shape on which we dropped</param>  
  /// <param name="diagramDragEventArgs">Drop event</param>  
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
  {  
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))  
   {  
    string[] droppedFiles =   
      diagramDragEventArgs.Data.  
               GetData(DataFormats.FileDrop) as string[];  
    MessageBox.Show(string.Format("Dropped text {0}",  
        string.Join("\r\n", droppedFiles)), "Dropped Text");  
   }  
  }  
 }  
```  
  
## Responder a cambios de valor  
 Este controlador tiene un modelo de dominio funcione correctamente. Ofrecemos un modelo de dominio simple.  
  
```  
using System.Diagnostics;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
  /// <summary>  
  /// Rule firing when the type of a domain model property is changed. The change is displayed  
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)  
  /// </summary>  
  [RuleOn(typeof(PropertyHasType))]  
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule  
  {  
    /// <summary>  
    /// Method called when the Type of a Domain Property   
    /// is changed by the user in a DslDefinition  
    /// </summary>  
    /// <param name="e"></param>  
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)  
    {  
      // We are only interested in the type  
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)  
      {  
        PropertyHasType relationship =   
           e.ElementLink as PropertyHasType;  
        DomainType newType = e.NewRolePlayer as DomainType;  
        DomainType oldType = e.OldRolePlayer as DomainType;  
        DomainProperty property = relationship.Property;  
  
         // We write about the Type change in the debugguer  
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",  
          property.Name,  
          property.Class.Name,  
          oldType.GetFullName(false),  
          newType.GetFullName(false))  
} }  }  );  
```  
  
 El código siguiente implementa un modelo simple. Cree un nuevo GUID para reemplazar el marcador de posición.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.DslDefinition;  
namespace Fabrikam.SimpleDslDesignerExtension  
{  
    /// <summary>  
    /// Simplest possible domain model   
    /// needed only for extension rules.   
    /// </summary>  
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]  
    public class SimpleDomainModelExtension : DomainModel  
    {  
        // Id of this domain model extension   
        // Please replace this with a new GUID:  
        public const string DomainModelId =   
                  "00000000-0000-0000-0000-000000000000";  
  
        /// <summary>  
        /// Constructor for the domain model extension  
        /// </summary>  
        /// <param name="store">Store in which the domain model will be loaded</param>  
        public SimpleDomainModelExtension(Store store)  
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))  
        {  
  
        }  
  
        /// <summary>  
        /// Rules brought by this domain model extension  
        /// </summary>  
        /// <returns></returns>  
        protected override System.Type[] GetCustomDomainModelTypes()  
        {  
            return new Type[] {  
                     typeof(DomainPropertyTypeChangedRule)  
                              };  
        }  
    }  
  
    /// <summary>  
    /// Provider for the DomainModelExtension  
    /// </summary>  
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]  
    public class SimpleDomainModelExtensionProvider   
          : DomainModelExtensionProvider  
    {  
        /// <summary>  
        /// Extension model type  
        /// </summary>  
        public override Type DomainModelType  
        {  
            get  
            {  
                return typeof(SimpleDomainModelExtension);  
            }  
        }  
  
    }  
}  
```