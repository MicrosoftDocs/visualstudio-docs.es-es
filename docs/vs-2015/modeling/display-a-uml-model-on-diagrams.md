---
title: Mostrar un modelo UML en diagramas | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c1d3fc6cee9a4149e378a5886b33322ab85c9cf8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699464"
---
# <a name="display-a-uml-model-on-diagrams"></a>Mostrar un modelo UML en diagramas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el código de programa de una extensión de Visual Studio puede controlar el modo en que los elementos del modelo se muestran en los diagramas. Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
En este tema:  
- [Para mostrar un elemento en un diagrama](#Display)  
  
- [Obtener acceso a las formas que representan un elemento](#GetShapes)  
  
- [Mover y cambiar el tamaño de las formas](#Moving)  
  
- [Para quitar una forma de un diagrama](#Removing)  
  
- [Abrir y crear diagramas](#Opening)  
  
- [Ejemplo: Comando para alinear formas](#AlignCommand)  
  
## <a name="Display"></a> Para mostrar un elemento en un diagrama  
 Cuando se crea un elemento como un caso de uso o una acción, el usuario puede verlo en el Explorador de modelos UML, pero no siempre aparece automáticamente en un diagrama. En algunos casos, hay que escribir código para que se muestre. En la tabla siguiente se resumen las opciones.  
  
|Tipo de elemento|Por ejemplo|Requisitos del código para su visualización|  
|---------------------|-----------------|-------------------------------------|  
|Clasificador|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Cree formas asociadas en diagramas especificados. Puede crear todas las formas que desee para cada clasificador.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Establezca `parentShape` en `null` para una forma en el nivel superior del diagrama.<br /><br /> Para mostrar una forma dentro de otra:<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);` **Nota:**  Si ejecuta una operación Display dentro de un **ILinkedUndo** transacción, el método devuelve a veces no `IShape`. Sin embargo, la forma se crea correctamente y puede obtenerse acceso a ella mediante `IElement.Shapes().`|  
|Elemento secundario del clasificador|Atributo, operación,<br /><br /> Elemento, puerto|Automático: no es necesario código.<br /><br /> Se muestra como parte del elemento primario.|  
|Comportamiento|Interacción (secuencia)<br /><br /> Actividad|Enlace el comportamiento a un diagrama adecuado.<br /><br /> Un comportamiento no puede enlazarse a más de un diagrama a la vez.<br /><br /> Por ejemplo:<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|  
|Elemento secundario del comportamiento|Líneas de vida, mensajes, acciones, nodos de objeto|Automático: no es necesario código.<br /><br /> Se muestra si el elemento primario está enlazado a un diagrama.|  
|Relación|Asociación, generalización, flujo, dependencia|Automático: no es necesario código.<br /><br /> Se muestra en los diagramas en los que aparecen los dos extremos.|  
  
## <a name="GetShapes"></a> Obtener acceso a las formas que representan un elemento  
 La forma que representa un elemento pertenece a los tipos siguientes:  
  
 `IShape`  
  
 `IShape<` *ElementType* `>`  
  
 donde *ElementType* es un tipo de elemento de modelo como `IClass` o `IUseCase`.  
  
|||  
|-|-|  
|`anElement.Shapes ()`|Todos las formas `IShapes` que representan este elemento en los diagramas abiertos.|  
|`anElement.Shapes(aDiagram)`|Todos las formas `IShapes` que representan este elemento en un diagrama concreto.|  
|`anIShape.GetElement()`|`IElement` representado por la forma. Normalmente se convierte en una subclase de IElement.|  
|`anIShape.Diagram`|`IDiagram` que contiene la forma.|  
|`anIShape.ParentShape`|La forma que contiene `anIShape`. Por ejemplo, una forma de puerto está contenida dentro de una forma de componente.|  
|`anIShape.ChildShapes`|Las formas contenidas en `IShape` o `IDiagram`.|  
|`anIShape.GetChildShapes<IUseCase>()`|Las formas contenidas en `IShape` o `IDiagram` que representan elementos del tipo especificado, como `IUseCase`.|  
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Conversión de un tipo genérico `IShape` a un `IShape<IElement>` fuertemente tipado.|  
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Conversión de una forma de tipo parametrizada en otra forma.|  
  
## <a name="Moving"></a> Mover y cambiar el tamaño de las formas  
  
|||  
|-|-|  
|`anIShape.Move(x, y, [width], [height])`|Mover una forma o cambiar su tamaño.|  
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Activar la ventana y desplazar el diagrama para que todas las formas especificadas estén visibles. Las formas deben estar todas en el diagrama. Si `zoomToFit` es true, el diagrama se escalará en caso necesario para que todas las formas sean visibles.|  
  
 Para obtener un ejemplo, vea [definir un comando de alineación](#AlignCommand).  
  
## <a name="Removing"></a> Para quitar una forma de un diagrama  
 Las formas de algunos tipos de elementos se pueden eliminar sin tener que eliminar el elemento.  
  
|Elemento de modelo|Para quitar la forma|  
|-------------------|-------------------------|  
|Un clasificador: clase, interfaz, enumeración, actor, caso de uso o componente|`shape.Delete();`|  
|Un comportamiento: interacción o actividad|Se puede eliminar el diagrama del proyecto. Use `IDiagram.FileName` para obtener la ruta de acceso.<br /><br /> Esto no elimina el comportamiento del modelo.|  
|Cualquier otra forma|No se puede eliminar explícitamente otras formas de un diagrama. La forma desaparecerá automáticamente si el elemento se elimina del modelo, o si la forma primaria se quita del diagrama.|  
  
## <a name="Opening"></a> Abrir y crear diagramas  
  
### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Para obtener acceso al diagrama actual del usuario desde una extensión de gestos o comandos  
 Declare esta propiedad importada en su clase:  
  
 `[Import]`  
  
 `IDiagramContext Context { get; set; }`  
  
 A través de un método, obtenga acceso al diagrama:  
  
 `IClassDiagram classDiagram =`  
  
 `Context.CurrentDiagram as IClassDiagram;`  
  
> [!NOTE]
> Una instancia de `IDiagram` (y sus subtipos como `IClassDiagram`) solo es válida dentro del comando que se está procesando. No es recomendable mantener un objeto `IDiagram` en una variable que se conserva mientras el control se devuelve al usuario.  
  
 Para obtener más información, consulte [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
### <a name="to-obtain-a-list-of-open-diagrams"></a>Para obtener una lista de los diagramas abiertos  
 Lista de los diagramas que están abiertos actualmente en el proyecto:  
  
```  
Context.CurrentDiagram.ModelStore.Diagrams()  
```  
  
## <a name="to-access-the-diagrams-in-a-project"></a>Para obtener acceso a los diagramas de un proyecto  
 La API de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede usarse para abrir y crear proyectos de modelado y diagramas.  
  
 Observe la conversión de `EnvDTE.ProjectItem` a `IDiagramContext`.  
  
```  
  
      using EnvDTE; // Visual Studio API  
...  
[Import]  
public IServiceProvider ServiceProvider { get; set; }  
...  
// Get Visual Studio API  
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;  
// Get current Visual Studio project  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
// Open and process every diagram in the project.  
foreach (ProjectItem item in project.ProjectItems)  
{  
  // Cast ProjectItem to IDiagramContext  
  IDiagramContext context = item as IDiagramContext;  
  if (context == null)  
  {  
     // This is not a diagram file.  
     continue;  
  }  
  // Open the file and give the window the focus.  
  if (!item.IsOpen)  
  {  
      item.Open().Activate();  
  }  
  // Get the diagram.  
  IDiagram diagram = context.CurrentDiagram;  
  // Deal with specific diagram types.  
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;  
  if (seqDiagram != null)  
  { ... } } }  
```  
  
 Las instancias de `IDiagram` y sus subtipos no son válidos después de devolver el control a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 También puede obtener el almacén de modelos de un proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
```  
  
      Project project = ...;  
IModelStore modelStore = (project as IModelingProject).Store;  
```  
  
## <a name="AlignCommand"></a> Ejemplo: Comando para alinear formas  
 El código siguiente implementa un comando de menú que alinea las formas perfectamente. Primero, el usuario debe colocar dos o más formas de modo que queden más o menos alineadas, ya sea vertical u horizontalmente. A continuación se puede usar el comando de alineación para alinear sus centros.  
  
 Para que el comando esté disponible, agregue este código a un proyecto de comando de menú y, después, implemente la extensión resultante a los usuarios. Para obtener más información, consulte [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Composition;  
using System.Linq;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace AlignCommand  
{  
  // Implements a command to align shapes in a UML class diagram.  
  // The user first selects shapes that are roughly aligned either vertically or horizontally.  
  // This command will straighten them up.  
  
  // Place this file in a menu command extension project.  
  // See https://msdn.microsoft.com/library/ee329481.aspx  
  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension] // TODO: Add other diagram types if needed  
  class CommandExtension : ICommandExtension  
  {  
    /// <summary>  
    /// See https://msdn.microsoft.com/library/ee329481.aspx  
    /// </summary>  
    [Import]  
    IDiagramContext context { get; set; }  
  
    /// <summary>  
    /// Transaction context.  
    /// See https://msdn.microsoft.com/library/ee330926.aspx  
    /// </summary>  
    [Import]  
    ILinkedUndoContext linkedUndo { get; set; }  
  
    /// <summary>  
    /// Called when the user selects the command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      Align(context.CurrentDiagram.SelectedShapes);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks on the diagram.  
    /// Determines whether the command is enabled.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;  
      // Make it visible if there are shapes selected:  
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);  
  
      // Make it enabled if there are two or more shapes that are roughly in line:  
      command.Enabled = currentSelection.Count() > 1  
        && (HorizontalAlignCenter(currentSelection) > 0.0  
        || VerticalAlignCenter(currentSelection) > 0.0);  
  
    }  
  
    /// <summary>  
    /// Title of the menu command.  
    /// </summary>  
    public string Text  
    {  
      get { return "Align Shapes"; }  
    }  
  
    /// <summary>  
    /// Find a horizontal line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double Y = -1.0;  
      double top = 0.0, bottom = shapes.First().Bottom();  
      foreach (IShape shape in shapes)  
      {  
        top = Math.Max(top, shape.Top());  
        bottom = Math.Min(bottom, shape.Bottom());  
      }  
      if (bottom > top) Y = (bottom + top) / 2.0;  
      return Y;  
    }  
  
    /// <summary>  
    /// Find a vertical line that goes through a list of shapes.  
    /// </summary>  
    /// <param name="shapes"></param>  
    /// <returns></returns>  
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)  
    {  
      double X = -1.0;  
      double left = 0.0, right = shapes.First().Right();  
      foreach (IShape shape in shapes)  
      {  
        left = Math.Max(left, shape.Left());  
        right = Math.Min(right, shape.Right());  
      }  
      if (right > left) X = (right + left) / 2.0;  
      return X;  
    }  
  
    /// <summary>  
    /// Line up those shapes that are roughly aligned.  
    /// </summary>  
    /// <param name="shapes"></param>  
    private void Align(IEnumerable<IShape> shapes)  
    {  
      if (shapes.Count() > 1)  
      {  
        // The shapes must all overlap either horizontally or vertically.  
        // Find a horizontal line that is covered by all the shapes:  
        double Y = HorizontalAlignCenter(shapes);  
        if (Y > 0.0) // Negative if they don't overlap.  
        {  
          // Adjust all the shape positions in one transaction:  
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
          {  
            foreach (IShape shape in shapes)  
            {  
              shape.AlignYCenter(Y);  
            }  
            t.Commit();  
          }  
        }  
        else  
        {  
          // Find a vertical line that is covered by all the shapes:  
          double X = VerticalAlignCenter(shapes);  
          if (X > 0.0) // Negative if they don't overlap.  
          {  
            // Adjust all the shape positions in one transaction:  
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))  
            {  
              foreach (IShape shape in shapes)  
              {  
                shape.AlignXCenter(X);  
              }  
              t.Commit();  
            }  
          }  
        }  
      }  
    }  
  }  
  
  /// <summary>  
  /// Convenience extensions for IShape.  
  /// </summary>  
  public static class IShapeExtension  
  {  
    public static double Bottom(this IShape shape)  
    {  
      return shape.YPosition + shape.Height;  
    }  
  
    public static double Top(this IShape shape)  
    {  
      return shape.YPosition;  
    }  
  
    public static double Left(this IShape shape)  
    {  
      return shape.XPosition;  
    }  
  
    public static double Right(this IShape shape)  
    {  
      return shape.XPosition + shape.Width;  
    }  
  
    public static void AlignYCenter(this IShape shape, double Y)  
    {  
      shape.Move(shape.XPosition, Y - shape.YCenter());  
    }  
  
    public static void AlignXCenter(this IShape shape, double X)  
    {  
      shape.Move(X - shape.XCenter(), shape.YPosition);  
    }  
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double YCenter(this IShape shape)  
    {  
        return shape.Height / 2.0;  
    }   
  
    /// <summary>  
    /// We can adjust what bit of the shape we want to be aligned.  
    /// The default is the center of the shape.  
    /// </summary>  
    /// <param name="shape"></param>  
    /// <returns></returns>  
    public static double XCenter(this IShape shape)  
    {  
        return shape.Width / 2.0;  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Navegar por el modelo UML](../modeling/navigate-the-uml-model.md)   
 [Ejemplo: Alinear formas en un comando de menú de diagrama](http://go.microsoft.com/fwlink/?LinkId=213809)   
 [Ejemplo: Creación de elementos, formas y estereotipos](http://go.microsoft.com/fwlink/?LinkId=213811)
