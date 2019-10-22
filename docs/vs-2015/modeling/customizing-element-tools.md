---
title: Personalizar herramientas de elementos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655023"
---
# <a name="customizing-element-tools"></a>Personalizar herramientas de elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En algunas definiciones de DSL, se representa un único concepto como grupo de elementos. Por ejemplo, si crea un modelo en el que un componente tiene un conjunto fijo de puertos, siempre quiere que los puertos se creen al mismo tiempo que su componente primario. Por consiguiente, tiene que personalizar la herramienta de creación de elementos para que cree un grupo de elementos en lugar de uno solo. Para ello, puede personalizar la forma en que se inicializa la herramienta de creación de elementos.

 También puede invalidar lo que ocurre cuando se arrastra la herramienta al diagrama o un elemento.

## <a name="customizing-the-content-of-an-element-tool"></a>Personalizar el contenido de una herramienta de elemento
 Cada herramienta de elemento almacena una instancia de un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), que contiene una versión serializada de uno o más vínculos y elementos del modelo. De forma predeterminada, el EGP de una herramienta de elemento contiene una instancia de la clase que se especifica para la herramienta. Puede cambiar esto invalidando *sulenguaje* `ToolboxHelper.CreateElementToolPrototype`. Se llama a este método cuando se carga el paquete DSL.

 Un parámetro del método es el identificador de la clase que especificó en la definición de DSL. Cuando se llama al método con la clase que le interesa, puede agregar elementos adicionales al EGP.

 El EGP debe incluir vínculos de incrustación de un elemento principal a los elementos secundarios. También puede incluir vínculos de referencia.

 En el ejemplo siguiente se crea un elemento principal y dos elementos incrustados. La clase principal se denomina resistencia y tiene dos relaciones de incrustación a los elementos denominados terminal. Las propiedades del rol de incrustación se denominan Terminal1 y Terminal2, y ambas tienen una multiplicidad de 1.. 1.

```
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
 [Personalizar la creación y el movimiento de los elementos](../modeling/customizing-element-creation-and-movement.md)
