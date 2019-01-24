---
title: Personalizar herramientas de elemento
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ee9f574b1d0db7a90b2d056456ccb29db0604e1e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846105"
---
# <a name="customizing-element-tools"></a>Personalizar herramientas de elemento
En algunas definiciones de DSL, un único concepto se representa como un grupo de elementos. Por ejemplo, si crea un modelo en el que un componente tiene un conjunto fijo de puertos, siempre desea que los puertos que deben crearse al mismo tiempo que su componente primario. Por lo tanto, debe personalizar la herramienta de creación de elemento para que crea un grupo de elementos en lugar de uno. Para lograr esto, puede personalizar cómo se inicializa la herramienta de creación del elemento.

 También puede invalidar lo que sucede cuando se arrastra la herramienta hasta el diagrama o un elemento.

## <a name="customizing-the-content-of-an-element-tool"></a>Personalizar el contenido de una herramienta de elemento
 Cada herramienta de elemento almacena una instancia de un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), que contiene una versión serializada de uno o varios elementos del modelo y los vínculos. De forma predeterminada, el EGP de una herramienta de elemento contiene una instancia de la clase que especifique para la herramienta. Puede cambiar esto reemplazando *Sulenguaje*`ToolboxHelper.CreateElementToolPrototype`. Este método se llama cuando se carga el paquete DSL.

 Un parámetro del método es el identificador de la clase que especificó en la definición de DSL. Cuando se llama al método con la clase que le interesa, puede agregar elementos adicionales en el EGP.

 Debe incluir el EGP incrustar vínculos desde un elemento principal a los elementos secundarios. También puede incluir vínculos de referencia.

 En el ejemplo siguiente se crea un elemento principal y dos elementos incrustados. La clase principal se denomina resistencia y tiene dos relaciones de incrustación para elementos denominados Terminal. Las propiedades del rol de incrustación se denominan Terminal1 y Terminal2, y ambos tienen una multiplicidad de 1..1.

```csharp
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Vea también

- [Personalizar la creación y el movimiento de los elementos](../modeling/customizing-element-creation-and-movement.md)