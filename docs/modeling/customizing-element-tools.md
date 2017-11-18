---
title: Personalizar el elemento herramientas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: "6"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 2555fe2be42ed58482cdacf174a6cb035a8d7bd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="customizing-element-tools"></a>Personalizar herramientas de elemento
En algunas definiciones de DSL, un concepto único se representa como un grupo de elementos. Por ejemplo, si crea un modelo en el que un componente tiene un conjunto fijo de puertos, desea siempre los puertos se creará al mismo tiempo que su componente primario. Por lo tanto, tiene que personalizar la herramienta de creación de elemento para que crea un grupo de elementos en lugar de solo uno. Para lograr esto, puede personalizar cómo se inicializa la herramienta de creación del elemento.  
  
 También puede invalidar lo que ocurre cuando se arrastra la herramienta hasta el diagrama o un elemento.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>Personalizar el contenido de un elemento de herramienta  
 Cada herramienta elemento almacena una instancia de un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), que contiene una versión serializada de uno o más elementos del modelo y los vínculos. De forma predeterminada, el protocolo EGP de una herramienta de elemento contiene una instancia de la clase que especifique para la herramienta. Puede cambiar mediante la invalidación *YourLanguage*`ToolboxHelper.CreateElementToolPrototype`. Este método se llama cuando se carga el paquete DSL.  
  
 Un parámetro del método es el identificador de la clase que especificó en la definición DSL. Cuando se llama al método con la clase que le interesa, puede agregar elementos adicionales en el EGP.  
  
 Debe incluir el EGP incrustar vínculos entre un elemento principal y los elementos secundarios. También puede incluir vínculos de referencia.  
  
 En el ejemplo siguiente se crea un elemento principal y dos elementos incrustados. La clase principal se denomina resistencia y tiene dos relaciones de incrustación con los elementos con el nombre de Terminal. Las propiedades del rol incrustación se denominan Terminal1 y Terminal2, y ambos tienen una multiplicidad de 1..1.  
  
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