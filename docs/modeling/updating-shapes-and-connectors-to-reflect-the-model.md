---
title: Actualizar formas y conectores para reflejar el modelo
description: Obtenga información sobre que, en un lenguaje específico del dominio Visual Studio, puede hacer que la apariencia de una forma refleje el estado del modelo subyacente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6439a01de2a02361914ce227c43d903f1b24b405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388573"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Actualizar formas y conectores para reflejar el modelo

En un lenguaje específico del dominio Visual Studio, puede hacer que la apariencia de una forma refleje el estado del modelo subyacente.

Los ejemplos de código de este tema deben agregarse a un `.cs` archivo del `Dsl` proyecto. Necesita estas directivas en cada archivo:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Establecer las propiedades del mapa de formas para controlar la visibilidad de un decorador

Puede controlar la visibilidad de un decorador sin escribir código de programa mediante la configuración de la asignación entre la forma y la clase de dominio en la definición de DSL. Para obtener más información, [vea How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Exponer el color y el estilo de una forma como propiedades

En la definición de DSL, haga clic con el botón derecho en la clase de forma, seleccione Agregar expuesto **y,** a continuación, haga clic en uno de los elementos, como **Color de relleno.**

La forma ahora tiene una propiedad de dominio que puede establecer en el código del programa o como usuario. Por ejemplo, para establecerlo en el código de programa de un comando o regla, podría escribir:

`shape.FillColor = System.Drawing.Color.Red;`

Si desea convertir la variable de propiedad solo bajo el control de programa y no por el usuario, seleccione la nueva propiedad de dominio, como **Color** de relleno, en el diagrama de definición de DSL. A continuación, en ventana Propiedades, establezca **Is Browsable** en `false` o establezca Is UI **Readonly** en `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Definir reglas de cambio para que el color, el estilo o la ubicación dependan de las propiedades del elemento del modelo
 Puede definir reglas que actualicen la apariencia de la forma que depende de otras partes del modelo. Por ejemplo, podría definir una regla de cambio en un elemento de modelo que actualice el color de su forma en función de las propiedades del elemento de modelo. Para obtener más información sobre las reglas de cambio, vea [Reglas propagar cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

 Solo debe usar reglas para actualizar las propiedades que se mantienen dentro del Almacén, ya que no se invocan reglas cuando se realiza el comando Deshacer. Esto no incluye algunas características gráficas, como el tamaño y la visibilidad de una forma. Para actualizar esas características de una forma, vea [Actualización de características gráficas](#OnAssociatedProperty)que no son de almacén.

 En el ejemplo siguiente se supone que se ha expuesto `FillColor` como una propiedad de dominio como se describe en la sección anterior.

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

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Uso de OnChildConfigured para inicializar las propiedades de una forma

Para establecer las propiedades de una forma cuando se crea por primera vez, invalida en `OnChildConfigured()` una definición parcial de la clase de diagrama. La clase de diagrama se especifica en la definición de DSL y el código generado se encuentra en **Dsl\Generated Code\Diagram.cs**. Por ejemplo:

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

Este método se puede usar tanto para las propiedades de dominio como para las características que no son de almacén, como el tamaño de la forma.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Usar AssociateValueWith() para actualizar otras características de una forma

Para algunas características de una forma, como si tiene una sombra o el estilo de flecha de un conector, no hay ningún método integrado para exponer la característica como una propiedad de dominio.  Los cambios en estas características no están bajo el control del sistema de transacciones. Por lo tanto, no es adecuado actualizarlas mediante reglas, ya que no se invocan reglas cuando el usuario realiza el comando Deshacer.

En su lugar, puede actualizar estas características mediante <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . En el ejemplo siguiente, el estilo de flecha de un conector se controla mediante un valor de una propiedad de dominio en la relación que muestra el conector:

```csharp
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

`AssociateValueWith()` se debe llamar una vez por cada propiedad de dominio que quiera registrar. Una vez que se haya llamado, cualquier cambio en la propiedad especificada llamará a en cualquier forma que presente el `OnAssociatedPropertyChanged()` elemento de modelo de la propiedad.

No es necesario llamar a `AssociateValueWith()` para cada instancia. Aunque InitializeResources es un método de instancia, solo se invoca una vez para cada clase de forma.
