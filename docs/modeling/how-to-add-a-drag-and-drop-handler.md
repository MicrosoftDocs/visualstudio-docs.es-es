---
title: 'Cómo: agregar un controlador de arrastrar y colocar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9b87a2e8a87721217f4c8e5442c25d9c4efd0236
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Cómo: Agregar un controlador para arrastrar y colocar
Puede agregar a su DSL controladores para eventos de arrastrar y colocar para que los usuarios puedan arrastrar elementos al diagrama desde otros diagramas o desde otras partes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. También puede agregar controladores para eventos como doble clic. Juntos, se denominan controladores de arrastrar y colocar y haga doble clic en *controladores de gestos*.  
  
 En este tema se describen los gestos de arrastrar y colocar que se originan en otros diagramas. Para eventos de mover y copiar dentro de un único diagrama, considere la posibilidad alternativa de definir una subclase de `ElementOperations`. Para obtener más información, consulte [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md). También puede personalizar la definición de DSL.  
  
## <a name="in-this-topic"></a>En este tema  
  
-   Las primeras dos secciones describen métodos alternativos para definir un controlador de gestos:  
  
    -   [Definir controladores de gestos ShapeElement reemplazar métodos](#overrideShapeElement). Se puede invalidar `OnDragDrop`, `OnDoubleClick`, `OnDragOver` y otros métodos.  
  
    -   [Definir controladores de gestos utilizando MEF](#MEF). Use este método si quiere que desarrolladores de terceros puedan definir sus propios controladores para su DSL. Los usuarios pueden elegir instalar las extensiones de terceros después de haber instalado su DSL.  
  
-   [Cómo descodificar el elemento arrastrado](#extracting). Los elementos se pueden arrastrar desde cualquier ventana o desde el escritorio, así como desde un DSL.  
  
-   [Cómo obtener la versión Original arrastró el elemento](#getOriginal). Si el elemento arrastrado es un elemento de DSL, puede abrir el modelo de origen y acceder al elemento.  
  
-   [Uso de las acciones del Mouse: Arrastre los elementos de compartimiento](#mouseActions). Este ejemplo muestra un controlador de bajo nivel que intercepta las acciones del mouse (ratón) en los campos de la forma. El ejemplo permite al usuario reordenar los elementos en un compartimiento arrastrando con el mouse.  
  
##  <a name="overrideShapeElement"></a> Definir controladores de gestos al invalidar los métodos ShapeElement  
 Agregue un nuevo archivo de código al proyecto DSL. Para un controlador de gestos, normalmente debe tener al menos las siguientes instrucciones `using`:  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using System.Linq;  
```  
  
 En el nuevo archivo, defina una clase parcial para la clase de forma o diagrama que debe responder a la operación de arrastrar. Invalide los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>: se llama a este método cuando el puntero del mouse entra en la forma durante una operación de arrastrar. El método debe inspeccionar el elemento que el usuario está arrastrando y establecer la propiedad Effect para indicar si el usuario puede colocar el elemento en esta forma. La propiedad Effect determina la apariencia del cursor mientras está sobre la forma, y determina también si se llamará a `OnDragDrop()` cuando el usuario suelte el botón del mouse.  
  
    ```csharp  
    partial class MyShape // MyShape generated from DSL Definition.  
    {  
        public override void OnDragOver(DiagramDragEventArgs e)  
        {  
          base.OnDragOver(e);  
          if (e.Effect == System.Windows.Forms.DragDropEffects.None   
               && IsAcceptableDropItem(e)) // To be defined  
          {  
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;  
          }  
        }  
  
    ```  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> : Este método se llama si el usuario suelta el botón del mouse mientras el puntero del mouse se sitúa sobre esta forma o el diagrama, si `OnDragOver(DiagramDragEventArgs e)` establecido anteriormente `e.Effect` en un valor distinto de `None`.  
  
    ```csharp  
    public override void OnDragDrop(DiagramDragEventArgs e)  
        {  
          if (!IsAcceptableDropItem(e))  
          {  
            base.OnDragDrop(e);  
          }  
          else   
          { // Process the dragged item, for example merging a copy into the diagram  
            ProcessDragDropItem(e); // To be defined  
          }    
        }  
  
    ```  
  
-   <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> : Este método se llama cuando el usuario hace doble clic en la forma o el diagrama.  
  
     Para obtener más información, consulte [Cómo: interceptar al hacer clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).  
  
 Defina `IsAcceptableDropItem(e)` para determinar si el elemento arrastrado es aceptable, y ProcessDragDropItem(e) para actualizar su modelo cuando el elemento se suelta. Estos métodos deben extraer primero el elemento de los argumentos de evento. Para obtener información acerca de cómo hacerlo, consulte [cómo obtener una referencia al elemento arrastrado](#extracting).  
  
##  <a name="MEF"></a> Definir controladores de gestos utilizando MEF  
 MEF (Managed Extensibility Framework) permite definir componentes que se pueden instalar con una configuración mínima. Para obtener más información, vea [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
#### <a name="to-define-a-mef-gesture-handler"></a>Para definir un controlador de gestos de MEF  
  
1.  Agregar a su **Dsl** y **DslPackage** proyectos la **MefExtension** archivos que se describen en [extender ADSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
2.  Ahora puede definir un controlador de gestos como un componente MEF:  
  
    ```  
  
    // This attribute is defined in the generated file  
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:  
    [MyDslGestureExtension]  
    public class MyGestureHandlerClassName : IGestureExtension  
    {  
      /// <summary>  
      /// Called to determine whether a drag onto the diagram can be accepted.  
      /// </summary>  
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>  
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>  
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>  
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
      {  
        MyShape target = targetMergeElement as MyShape;  
        if (target == null) return false;  
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;   
        return false;  
      }  
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
      {  
        MyShape target = targetMergeElement as MyShape;  
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;  
        // Process the dragged item, for example merging a copy into the diagram:  
        target.ProcessDragDropItem(diagramDragEventArgs);  
     }  
  
    ```  
  
     Puede crear más de un componente de controlador de gestos, como cuando tiene diferentes tipos de objetos arrastrados.  
  
3.  Agregue definiciones de clase parciales para las clases de forma, conector o diagrama de destino, y defina los métodos `IsAcceptableDropItem()` y `ProcessDragDropItem()`. Estos métodos deben empezar por extraer el elemento arrastrado de los argumentos del evento. Para obtener más información, consulte [cómo obtener una referencia al elemento arrastrado](#extracting).  
  
##  <a name="extracting"></a> Cómo descodificar el elemento arrastrado  
 Cuando el usuario arrastra un elemento al diagrama, o desde una parte del diagrama a otra, la información sobre el elemento que se está arrastrando está disponible en `DiagramDragEventArgs`. Como la operación de arrastrar podría haber empezado en cualquier objeto de la pantalla, los datos pueden estar disponibles en varios formatos. El código debe reconocer los formatos con los que es capaz de tratar.  
  
 Para detectar los formatos en los que la información del origen de la operación de arrastrar está disponible, ejecute el código en modo de depuración y establezca un punto de interrupción en la entrada a `OnDragOver()` o `CanDragDrop()`. Inspeccione los valores del parámetro `DiagramDragEventArgs`. La información se proporciona de dos maneras:  
  
-   <xref:System.Windows.Forms.IDataObject>  `Data` -Esta propiedad implica serializadas versiones de los objetos de origen, normalmente en más de un formato. Sus funciones más útiles son:  
  
    -   diagramEventArgs.Data.GetDataFormats() - enumera los formatos en el que pueda descodificar el objeto arrastrado. Por ejemplo, si el usuario arrastra un archivo desde el escritorio, los formatos disponibles incluyen el nombre de archivo ("`FileNameW`").  
  
    -   `diagramEventArgs.Data.GetData(format)` -Descodifica el objeto arrastrado en el formato especificado. Convierte el objeto en el tipo apropiado. Por ejemplo:  
  
         `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`  
  
         También puede transmitir objetos, como referencias de ModelBus, desde el origen con su propio formato personalizado. Para obtener más información, consulte [cómo enviar las referencias de Bus de modelo en operaciones de arrastrar y colocar](#mbr).  
  
-   <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> `Prototype` -Utilice esta propiedad si desea que los usuarios para arrastrar elementos desde una ADSL o un modelo UML. Un prototipo de grupo de elementos contiene uno o varios objetos, vínculos y los valores de sus propiedades. También se usa en operaciones de pegar y cuando se agrega un elemento del cuadro de herramientas. En un prototipo, los objetos y sus tipos se identifican por su GUID. Por ejemplo, este código permite al usuario arrastrar elementos de clase desde un diagrama UML o el Explorador de modelos UML:  
  
    ```csharp  
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)  
    {  
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>   
            element.DomainClassId.ToString()   
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.  
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId  
    }  
  
    ```  
  
     Para aceptar formas UML, determine los GUID de las clases de forma UML mediante experimentación. Recuerde que, normalmente, hay más de un tipo de elemento en cualquier diagrama. Recuerde también que un objeto arrastrado desde un diagrama DSL o UML es la forma, no el elemento de modelo.  
  
 `DiagramDragEventArgs` también tiene propiedades que indican la posición actual del puntero del mouse y si el usuario está presionando las teclas CTRL, ALT o MAYÚS.  
  
##  <a name="getOriginal"></a> Cómo obtener el original de un elemento arrastrado  
 Las propiedades `Data` y `Prototype` de los argumentos de evento solo contienen una referencia a la forma arrastrada. Normalmente, si quiere crear un objeto en el DSL de destino que deriva del prototipo de alguna manera, necesita obtener acceso al original, por ejemplo, leyendo el contenido del archivo o navegando al elemento de modelo representado por una forma.  Puede usar Visual Studio ModelBus para realizar esto.  
  
### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Para preparar un proyecto DSL para ModelBus  
  
1.  Haga que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus pueda acceder al DSL de origen:  
  
    1.  Si aún no lo ha hecho, descargue e instale la extensión Visual Studio ModelBus. Para obtener más información, consulte [SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
    2.  Abra el archivo de definición de DSL del DSL de origen en DSL Designer (Diseñador de DSL). Haga clic en la superficie de diseño y, a continuación, haga clic en **habilitar Modelbus**. En el cuadro de diálogo, elija una o ambas opciones.  Haga clic en **Aceptar**. Se agrega un nuevo proyecto "ModelBus" a la solución de DSL.  
  
    3.  Haga clic en **Transformar todas las plantillas** y recompile la solución.  
  
###  <a name="mbr"></a> Para enviar un objeto desde un origen de DSL  
  
1.  En la subclase ElementOperations, invalide `Copy()` para que codifique una referencia de ModelBus (MBR) en IDataObject. Se llamará a este método cuando el usuario comience a arrastrar desde el diagrama de origen. La MBR codificada estará disponible en IDataObject cuando el usuario coloque en el diagrama de destino.  
  
    ```  
  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Shell;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
    using Microsoft.VisualStudio.Modeling.Integration;  
    using Microsoft.VisualStudio.Modeling.Integration.Shell;  
    using System.Drawing; // PointF  
    using  System.Collections.Generic; // ICollection  
    using System.Windows.Forms; // for IDataObject  
    ...  
    public class MyElementOperations : DesignSurfaceElementOperations  
    {  
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)  
        {  
          base.Copy(data, elements, closureType, sourcePosition);  
  
          // Get the ModelBus service:  
          IModelBus modelBus =  
              this.Store.GetService(typeof(SModelBus)) as IModelBus;  
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;  
          string modelFile = docData.FileName;  
          // Get an adapterManager for the target DSL:  
          ModelBusAdapterManager manager =  
              (modelBus.FindAdapterManagers(modelFile).First());  
          ModelBusReference modelReference = manager.CreateReference(modelFile);  
          ModelBusReference elementReference = null;  
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))  
          {  
            elementReference = adapter.GetElementReference(elements.First());  
          }  
  
          data.SetData("ModelBusReference", elementReference);  
        }  
    ...}  
  
    ```  
  
### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Para recibir una referencia de ModelBus de un DSL en un proyecto DSL o UML de destino  
  
1.  En el proyecto DSL de destino, agregue las referencias del proyecto a:  
  
    -   El proyecto DSL de origen.  
  
    -   El proyecto ModelBus de origen.  
  
2.  En el archivo de código del controlador de gestos, agregue las siguientes referencias de espacio de nombres:  
  
    ```csharp  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
    using Microsoft.VisualStudio.Modeling.Integration;  
    using SourceDslNamespace;  
    using SourceDslNamespace.ModelBusAdapters;  
  
    ```  
  
3.  La muestra siguiente ilustra cómo obtener acceso al elemento de modelo de origen:  
  
    ```  
    partial class MyTargetShape // or diagram or connector   
    {  
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)  
      {  
        // Verify that we're being passed an Object Shape.  
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;  
        if (prototype == null) return;  
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId  
          != prototype.RootProtoElements.First().DomainClassId)  
          return;  
        // - This is an ObjectShape.  
        // - We need to access the originating Store, find the shape, and get its object.  
  
        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;  
  
        // Unpack the MBR that was packed in Copy:  
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;  
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)  
        {  
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))  
          {  
            // Quickest way to get the shape from the MBR:  
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);  
  
            // But actually there might be several shapes - so get them from the prototype instead:  
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;  
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)  
            {  
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;  
              if (pe == null) continue;  
              SourceElement instance = pe.ModelElement as SourceElement;  
              if (instance == null) continue;  
  
              // Do something with the object:  
          instance...  
            }  
            t.Commit();  
          }  
        }  
    }  
  
    ```  
  
### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Para aceptar un elemento con origen en un modelo UML  
  
-   En este ejemplo de código se acepta un objeto colocado desde un diagrama UML.  
  
    ```csharp  
  
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
      using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
      using Microsoft.VisualStudio.Modeling;  
      using Microsoft.VisualStudio.Modeling.Diagrams;  
      using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
      using Microsoft.VisualStudio.Uml.Classes;  
      using System;  
      using System.ComponentModel.Composition;  
      using System.Linq;  
    ...  
    partial class TargetShape  
    {  
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)  
      {  
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;  
            // Find the UML project  
            foreach (EnvDTE.Project project in dte.Solution.Projects)  
            {  
              IModelingProject modelingProject = project as IModelingProject;  
              if (modelingProject == null) continue; // not a modeling project  
              IModelStore store = modelingProject.Store;  
              if (store == null) return;  
  
              foreach (IDiagram dd in store.Diagrams())  
              {  
                  // Get Modeling.Diagram that implements UML.IDiagram:  
                  Diagram diagram = dd.GetObject<Diagram>();   
  
                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)  
                  {  
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;  
                    if (shape == null) continue;  
                    // This example assumes the shape is a UML class:  
                    IClass classElement = shape.ModelElement as IClass;  
                    if (classElement == null) continue;  
  
                    // Now do something with the UML class element ...  
                  }  
            }  
          break; // don't try any more projects   
    }  }  }  
  
    ```  
  
##  <a name="mouseActions"></a> Uso de las acciones del Mouse: Arrastre los elementos de compartimiento  
 Puede escribir un controlador que intercepta las acciones del mouse (ratón) en los campos de la forma. El ejemplo siguiente permite al usuario reordenar los elementos en un compartimiento arrastrando con el mouse.  
  
 Para compilar este ejemplo, cree una solución utilizando la **diagramas de clases** plantilla de solución. Agregue un archivo de código y agregue el código siguiente. Ajuste el espacio de nombres para que sea igual que el suyo.  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Design;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using System.Collections.Generic;  
using System.Linq;  
  
// This sample allows users to re-order items in a compartment shape by dragging.  
  
// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).  
// You will need to change the following domain class names to your own:  
// ClassShape = a compartment shape  
// ClassModelElement = the domain class displayed using a ClassShape  
// This code assumes that the embedding relationships displayed in the compartments  
// don't use inheritance (don't have base or derived domain relationships).  
  
namespace Company.CompartmentDrag  // EDIT.  
{  
 /// <summary>  
 /// Manage the mouse while dragging a compartment item.  
 /// </summary>  
 public class CompartmentDragMouseAction : MouseAction  
 {  
  private ModelElement sourceChild;  
  private ClassShape sourceShape;  
  private RectangleD sourceCompartmentBounds;  
  
  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)  
   : base (sourceParentShape.Diagram)  
  {  
   sourceChild = sourceChildElement;  
   sourceShape = sourceParentShape;  
   sourceCompartmentBounds = bounds; // For cursor.  
  }  
  
  /// <summary>  
  /// Call back to the source shape to drop the dragged item.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   sourceShape.DoMouseUp(sourceChild, e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = true;  
  }  
  
  /// <summary>  
  /// Ideally, this shouldn't happen. This action should only be active  
  /// while the mouse is still pressed. However, it can happen if you  
  /// move the mouse rapidly out of the source shape, let go, and then   
  /// click somewhere else in the source shape. Yuk.  
  /// </summary>  
  /// <param name="e"></param>  
  protected override void OnMouseDown(DiagramMouseEventArgs e)  
  {  
   base.OnMouseDown(e);  
   this.Cancel(e.DiagramClientView);  
   e.Handled = false;  
  }  
  
  /// <summary>  
  /// Display an appropriate cursor while the drag is in progress:  
  /// Up-down arrow if we are inside the original compartment.  
  /// No entry if we are elsewhere.  
  /// </summary>  
  /// <param name="currentCursor"></param>  
  /// <param name="diagramClientView"></param>  
  /// <param name="mousePosition"></param>  
  /// <returns></returns>  
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)  
  {  
   // If the cursor is inside the original compartment, show up-down cursor.  
   return sourceCompartmentBounds.Contains(mousePosition)   
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.  
    : System.Windows.Forms.Cursors.No;  
  }  
 }  
  
 /// <summary>  
 /// Override some methods of the compartment shape.  
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****  
 /// </summary>  
 public partial class ClassShape  
 {  
  /// <summary>  
  /// Model element that is being dragged.  
  /// </summary>  
  private static ClassModelElement dragStartElement = null;  
  /// <summary>  
  /// Absolute bounds of the compartment, used to set the cursor.  
  /// </summary>  
  private static RectangleD compartmentBounds;  
  
  /// <summary>  
  /// Attach mouse listeners to the compartments for the shape.  
  /// This is called once per compartment shape.  
  /// The base method creates the compartments for this shape.  
  /// </summary>  
  public override void EnsureCompartments()  
  {  
   base.EnsureCompartments();  
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())  
   {  
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);  
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);  
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);  
   }  
  }  
  
  /// <summary>  
  /// Remember which item the mouse was dragged from.  
  /// We don't create an Action immediately, as this would inhibit the  
  /// inline text editing feature. Instead, we just remember the details  
  /// and will create an Action when/if the mouse moves off this list item.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)  
  {  
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();  
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;  
  }  
  
  /// <summary>  
  /// When the mouse moves away from the initial list item, but still inside the compartment,  
  /// create an Action to supervise the cursor and handle subsequent mouse events.  
  /// Transfer the details of the initial mouse position to the Action.  
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)  
  {  
   if (dragStartElement != null)  
   {  
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())  
    {  
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);  
     dragStartElement = null;  
    }  
   }  
  }  
  
  /// <summary>  
  /// User has released the mouse button.   
  /// </summary>  
  /// <param name="sender"></param>  
  /// <param name="e"></param>  
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)  
  {  
    dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Forget the source item if mouse up occurs outside the  
  /// compartment.  
  /// </summary>  
  /// <param name="e"></param>  
  public override void OnMouseUp(DiagramMouseEventArgs e)  
  {  
   base.OnMouseUp(e);  
   dragStartElement = null;  
  }  
  
  /// <summary>  
  /// Called by the Action when the user releases the mouse.  
  /// If we are still on the same compartment but in a different list item,  
  /// move the starting item to the position of the current one.  
  /// </summary>  
  /// <param name="dragFrom"></param>  
  /// <param name="e"></param>  
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)  
  {  
   // Original or "from" item:  
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;  
   // Current or "to" item:  
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();  
   if (dragFromElement != null && dragToElement != null)  
   {  
    // Find the common parent model element, and the relationship links:  
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);  
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);  
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)  
    {  
     // Get the static relationship and role (= end of relationship):  
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();  
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];  
     // Get the node in which the element is embedded, usually the element displayed in the shape:  
     ModelElement parentFrom = parentFromLink.LinkedElements[0];  
  
     // Same again for the target:  
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();  
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];  
     ModelElement parentTo = parentToLink.LinkedElements[0];  
  
     // Mouse went down and up in same parent and same compartment:  
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)  
     {  
      // Find index of target position:  
      int newIndex = 0;  
      var elementLinks = parentToRole.GetElementLinks(parentTo);  
      foreach (ElementLink link in elementLinks)  
      {  
       if (link == parentToLink) { break; }  
       newIndex++;  
      }  
  
      if (newIndex < elementLinks.Count)  
      {  
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))  
       {  
        parentFromLink.MoveToIndex(parentFromRole, newIndex);  
        t.Commit();  
       }  
      }  
     }  
    }  
   }  
  }  
  
  /// <summary>  
  /// Get the embedding link to this element.  
  /// Assumes there is no inheritance between embedding relationships.  
  /// (If there is, you need to make sure you've got the relationship  
  /// that is represented in the shape compartment.)  
  /// </summary>  
  /// <param name="child"></param>  
  /// <returns></returns>  
  ElementLink GetEmbeddingLink(ClassModelElement child)  
  {  
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)  
   {  
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))  
    {  
     // Just the assume the first embedding link is the only one.  
     // Not a valid assumption if one relationship is derived from another.  
     return link;  
    }  
   }  
   return null;  
  }  
 }  
}  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md)   
 [Implementar soluciones de lenguajes específicos de dominio](../modeling/deploying-domain-specific-language-solutions.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

 
