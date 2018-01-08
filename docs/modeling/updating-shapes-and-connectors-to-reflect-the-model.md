---
title: Actualizar formas y conectores para reflejar el modelo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7c63d8e9d7da3c02259e557580c5d7cafa74d0b1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Actualizar formas y conectores para reflejar el modelo
En un lenguaje específico de dominio en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], puede hacer que la apariencia de una forma reflejan el estado del modelo subyacente.  
  
 Los ejemplos de código de este tema deben agregarse a un `.cs` un archivo en su `Dsl` proyecto. Necesitará estas instrucciones en cada archivo:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Establecer las propiedades de mapa de formas para controlar la visibilidad de un elemento decorator  
 Puede controlar la visibilidad de un elemento decorator sin escribir código de programa, mediante la configuración de la asignación entre la forma y la clase de dominio en la definición DSL. Para obtener más información, consulte [cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md).
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Exponer el color y estilo de una forma como propiedades  
 En la definición DSL, haga clic en la clase shape, seleccione **agregar expone**y, a continuación, haga clic en uno de los elementos como **Fill Color**.  
  
 La forma ahora tiene una propiedad de dominio que se puede establecer en el código de programa o como un usuario. Por ejemplo, para establecerla en el código de programa de un comando o una regla, podría escribir:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Si desea hacer que la variable de propiedad solo bajo control del programa y no por el usuario, seleccione la nueva propiedad de dominio como **Fill Color** en el diagrama de definición DSL. A continuación, en la ventana Propiedades, establezca **es examinable** a `false` o establecer **es Readonly de interfaz de usuario** a `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definir reglas de cambio para que el color, estilo o una ubicación dependen de propiedades del elemento de modelo  
 Puede definir reglas que actualizan la apariencia de la forma depende de otras partes del modelo. Por ejemplo, podría definir una regla de cambio de un elemento del modelo que actualiza el color de su forma depende de las propiedades del elemento del modelo. Para obtener más información acerca de cómo cambiar las reglas, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Debe usar las reglas para actualizar las propiedades que se mantienen en el almacén, porque las reglas no se invocan cuando se realiza el comando Deshacer. Esto no incluye algunas características como el tamaño y la visibilidad de una forma gráficas. Para actualizar las características de una forma, consulte [características gráficas de almacén no actualizar](#OnAssociatedProperty).  
  
 En el siguiente ejemplo se da por supuesto que ha expuesto `FillColor` como una propiedad de dominio como se describe en la sección anterior.  
  
```csharp  
[RuleOn(typeof(ExampleElement))]  
  class ExampleElementPropertyRule : ChangeRule  
  {  
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)  
    {  
      base.ElementPropertyChanged(e);  
      ExampleElement element = e.ModelElement as ExampleElement;  
      // The rule is called for every property that is updated.  
      // Therefore, verify which property changed:  
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)  
      {  
        // There is usually only one shape:  
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))  
        {  
          ExampleShape shape = pel as ExampleShape;  
          // Replace this with a useful condition:  
          shape.FillColor = element.Name.EndsWith("3")   
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
        }  
      }  
    }  
  }  
  // The rule must be registered:  
  public partial class OnAssociatedPropertyExptDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(ExampleElementPropertyRule));  
      // If you add more rules, list them here.   
      return types.ToArray();  
    }  
  }  
  
```  
  
## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Usar OnChildConfigured para inicializar las propiedades de una forma  
 Para establecer las propiedades de una forma cuando llega el primer creado, la invalidación `OnChildConfigured()` en una definición parcial de la clase del diagrama. La clase del diagrama se especifica en la definición de DSL y el código generado está en **Dsl\Generated Code\Diagram.cs**. Por ejemplo:  
  
```csharp  
partial class MyLanguageDiagram  
{  
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)  
  {  
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);  
    ExampleShape shape = child as ExampleShape;  
    if (shape != null)   
    {  
      if (!createdDuringViewFixup) return; // Ignore load from file.  
      ExampleElement element = shape.ModelElement as ExampleElement;  
      // Replace with a useful condition:  
      shape.FillColor = element.Name.EndsWith("3")   
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;  
    }  
    // else deal with other types of shapes and connectors.  
  }  
}  
  
```  
  
 Este método se puede utilizar tanto para las propiedades de dominio y las características de almacén no, como el tamaño de la forma.  
  
##  <a name="OnAssociatedProperty"></a>Usar AssociateValueWith() para actualizar otras características de una forma  
 Para algunas características de una forma, por ejemplo, si tiene una sombra, o el estilo de flecha de un conector, no hay ningún método integrado de exponer la característica como una propiedad de dominio.  Cambios en estas características no están bajo el control del sistema de transacciones. Por lo tanto, no resulta adecuado actualizarlos mediante reglas, porque las reglas no se invocan cuando el usuario ejecuta el comando Deshacer.  
  
 En su lugar, puede actualizar estas características mediante <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. En el ejemplo siguiente, el estilo de flecha de un conector se controla mediante un valor de una propiedad de dominio en la relación que el conector de muestra:  
  
```  
public partial class ArrowConnector // My connector class.   
{  
   /// <summary>  
    /// Called whenever a registered property changes in the associated model element.  
    /// </summary>  
    /// <param name="e"></param>  
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)  
    {  
      base.OnAssociatedPropertyChanged(e);  
      // Can be called for any property change. Therefore,  
      // Verify that this is the property we're interested in:  
      if ("IsDirected".Equals(e.PropertyName))  
      {  
        if (e.NewValue.Equals(true))  
        { // Update the shape's built-in Decorator feature:  
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;  
        }  
        else  
        {  
          this.DecoratorTo = null; // No arrowhead.  
        }  
      }  
    }  
    // OnAssociatedPropertyChanged is called only for properties  
    // that have been registered using AssociateValueWith().  
    // InitializeResources is a convenient place to call this.  
    // This method is invoked only once per class, even though  
    // it is an instance method.   
    protected override void InitializeResources(StyleSet classStyleSet)  
    {  
      base.InitializeResources(classStyleSet);  
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);  
      // Add other properties here.  
    }  
}  
  
```  
  
 `AssociateValueWith()`debe llamarse una vez por cada propiedad del dominio que desea registrar. Después de la llamada, se llamará los cambios en la propiedad especificada `OnAssociatedPropertyChanged()` en las formas que presenten el elemento del modelo de la propiedad.  
  
 No es necesario llamar a `AssociateValueWith()` para cada instancia. Aunque InitializeResources es un método de instancia, se invoca solo una vez para cada clase de forma.
