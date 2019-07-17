---
title: Actualizar formas y conectores para reflejar el modelo | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 51eb2af9-00e7-4725-a87d-62fb4f39f444
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c8520084b57fdf0f831f62626593832d03c25636
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183921"
---
# <a name="updating-shapes-and-connectors-to-reflect-the-model"></a>Actualizar formas y conectores para reflejar el modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un lenguaje específico de dominio en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], puede hacer que la apariencia de una forma de reflejar el estado del modelo subyacente.  
  
 Los ejemplos de código en este tema se deben agregar a un `.cs` de archivos en su `Dsl` proyecto. Necesita estas instrucciones en cada archivo:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  
```  
  
## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Establecer las propiedades de mapa de formas para controlar la visibilidad de un elemento decorator  
 Puede controlar la visibilidad de un elemento decorator sin necesidad de escribir código de programa, mediante la configuración de la asignación entre la forma y la clase de dominio en la definición de DSL. Para obtener más información, vea los temas siguientes:  
  
- [Procedimientos: Controlar la visibilidad de un elemento Decorator-redirigir](../misc/how-to-control-the-visibility-of-a-decorator-redirect.md)  
  
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)  
  
## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Exponer el color y estilo de una forma como propiedades  
 En la definición de DSL, haga clic en la clase shape, seleccione **agregar expuestos**y, a continuación, haga clic en uno de los elementos como **Color de relleno**.  
  
 Ahora, la forma tiene una propiedad de dominio que se puede establecer en el código de programa o como un usuario. Por ejemplo, para establecerla en el código del programa de un comando o una regla, podría escribir:  
  
 `shape.FillColor = System.Drawing.Color.Red;`  
  
 Si desea hacer que la variable de propiedad sólo bajo control del programa y no por el usuario, seleccione la nueva propiedad de dominio como **Color de relleno** en el diagrama de definición de DSL. A continuación, en la ventana Propiedades, establezca **es examinable** a `false` o establecer **es Readonly de interfaz de usuario** a `true`.  
  
## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definir reglas de cambio para que el color, estilo o una ubicación dependen de las propiedades del elemento de modelo  
 Puede definir reglas que actualizan la apariencia de la forma depende de otras partes del modelo. Por ejemplo, podría definir una regla de cambio en un elemento de modelo que actualiza el color de su forma depende de las propiedades del elemento del modelo. Para obtener más información sobre cómo cambiar las reglas, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Debe usar las reglas solo para actualizar las propiedades que se mantienen en el Store, ya que las reglas no se invocan cuando se realiza el comando Deshacer. Esto no incluye algunas características como el tamaño y la visibilidad de una forma gráficas. Para actualizar las características de una forma, consulte [características gráficas de actualización no-Store](#OnAssociatedProperty).  
  
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
 Para establecer las propiedades de una forma cuando es el primero creado, la invalidación `OnChildConfigured()` en una definición parcial de la clase del diagrama. La clase de diagrama se especifica en la definición de DSL, y el código generado está en **Dsl\Generated Code\Diagram.cs**. Por ejemplo:  
  
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
  
 Este método puede usarse tanto para las propiedades de dominio y no-store características, como el tamaño de la forma.  
  
## <a name="OnAssociatedProperty"></a> Usar AssociateValueWith() para actualizar otras características de una forma  
 Para algunas características de una forma, por ejemplo, si tiene una sombra o el estilo de flecha de un conector, no hay ningún método integrado de exponer la función como una propiedad de dominio.  Los cambios en estas características no están bajo el control del sistema de transacciones. Por lo tanto, no es adecuado actualizarlos mediante reglas, puesto que las reglas no se invocan cuando el usuario realiza el comando Deshacer.  
  
 En su lugar, puede actualizar estas características mediante <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. En el ejemplo siguiente, el estilo de flecha de un conector se controla mediante un valor de una propiedad de dominio en la relación que se muestra el conector:  
  
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
        { // Update the shape’s built-in Decorator feature:  
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
  
 `AssociateValueWith()` debe llamarse una vez para cada propiedad de dominio que desea registrar. Después de que se ha llamado, cualquier cambio en la propiedad especificada se llamará `OnAssociatedPropertyChanged()` en formas que presentan el elemento de modelo de la propiedad.  
  
 No es necesario llamar a `AssociateValueWith()` para cada instancia. Aunque InitializeResources es un método de instancia, se invoca solo una vez para cada clase shape.
