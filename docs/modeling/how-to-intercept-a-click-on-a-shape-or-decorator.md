---
title: 'Cómo: Interceptar un clic en una forma o decorador'
description: Obtenga información sobre cómo interceptar un clic en una forma o un decorador de icono, y cómo puede interceptar clics, hacer doble clic, arrastrar y otros gestos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff49c1950e81098633fab92ffbbdf25020945a1e
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363905"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Cómo: Interceptar un clic en una forma o decorador
Los procedimientos siguientes muestran cómo interceptar un clic en una forma o un decorador de icono. Puede interceptar clics, hacer doble clic, arrastrar y otros gestos y hacer que el elemento responda.

## <a name="to-intercept-clicks-on-shapes"></a>Para interceptar los clics en formas
 En el proyecto DSL, en un archivo de código que es independiente de los archivos de código generados, escriba una definición de clase parcial para la clase Shape. Reemplace `OnDoubleClick()` o uno de los otros métodos que tenga un nombre que comience por `On...` . Por ejemplo:

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Establezca `e.Handled` en `true` , a menos que desee que el evento se pase a la forma o el diagrama que lo contiene.

## <a name="to-intercept-clicks-on-decorators"></a>Para interceptar los clics en los elementos Decorator
 Los decoradores de imagen se transfieren a una instancia de la clase ImageField, que tiene un método DoubleClick. Puede interceptar los clics si escribe una subclase ImageField. Los campos se configuran en el método InitializeShapeFields. Por lo tanto, debe cambiar ese método para crear una instancia de la subclase en lugar de la ImageField normal. El método InitializeShapeFields se encuentra en el código generado de la clase Shape. Puede invalidar la clase Shape si establece su `Generates Double Derived` propiedad tal y como se describe en el procedimiento siguiente.

 Aunque InitializeShapeFields es un método de instancia, solo se llama una vez para cada clase. Por lo tanto, solo existe una instancia de ClickableImageField para cada campo de cada clase, no una instancia para cada forma del diagrama. Cuando el usuario hace doble clic en una instancia, debe identificar qué instancia se ha alcanzado, como se muestra en el código del ejemplo.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Para interceptar un clic en un decorador de icono

1. Abra o cree una solución DSL.

2. Elija o cree una forma que tenga un decorador de icono y asígnela a una clase de dominio.

3. En un archivo de código que sea independiente de los archivos de la `GeneratedCode` carpeta, cree la nueva subclase de ImageField:

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Debe establecer Handled en true si no desea que el evento se pase a la forma contenedora.

4. Reemplace el método InitializeShapeFields en la clase Shape agregando la siguiente definición de clase parcial.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Compile y ejecute la solución.

2. Haga doble clic en el icono de una instancia de la forma. Debería aparecer el mensaje de prueba.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Interceptar clics y arrastrar en listas de CompartmentShape
 El ejemplo siguiente permite a los usuarios volver a ordenar los elementos de una forma de compartimiento arrastrándolos. Para ejecutar este código:

1. Cree una nueva solución de DSL con la plantilla de solución **diagramas de clases** .

    También puede trabajar con una solución propia que contenga formas de compartimiento. En este código se supone que hay una relación de incrustación entre los elementos del modelo representada por la forma y los elementos representados en los elementos de la lista de compartimientos.

2. Establezca la propiedad **genera Double derived** de la forma de compartimiento.

3. Agregue este código a un archivo en el proyecto **DSL** .

4. Ajuste los nombres de la clase de dominio y de la forma en este código para que coincida con su propio DSL.

   En Resumen, el código funciona de la siguiente manera. En este ejemplo, `ClassShape` es el nombre de la forma de compartimiento.

- Cuando se crea un conjunto de controladores de eventos del mouse, se adjunta a cada instancia de compartimiento.

- El `ClassShape.MouseDown` evento almacena el elemento actual.

- Cuando el mouse sale del elemento actual, se crea una instancia de MouseAction, que establece el cursor y captura el mouse hasta que se libera.

     Para evitar interferir con otras acciones del mouse, como seleccionar el texto de un elemento, el MouseAction no se crea hasta que el mouse deja el elemento original.

     Una alternativa a la creación de una MouseAction sería simplemente escuchar para MouseUp. Sin embargo, esto no funcionaría correctamente si el usuario suelta el mouse después de arrastrarlo fuera del compartimiento. El MouseAction puede realizar la acción adecuada independientemente de dónde se suelte el mouse.

- Cuando se suelta el mouse, MouseAction. MouseUp reorganiza el orden de los vínculos entre los elementos del modelo.

- El cambio de orden de rol desencadena una regla que actualiza la pantalla. Este comportamiento ya está definido y no se requiere ningún código adicional.

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
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
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
  /// click somewhere else in the source shape.
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
 /// **_ GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. _***
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
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
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

## <a name="see-also"></a>Consulta también

- [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md)
- [Propiedades de los decoradores](../modeling/properties-of-decorators.md)
