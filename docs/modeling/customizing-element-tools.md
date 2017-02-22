---
title: "Personalizar herramientas de elemento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 6
caps.handback.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Personalizar herramientas de elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En algunas definiciones de DSL, un único concepto se representa como un grupo de elementos. Por ejemplo, si crea un modelo en el que un componente tiene un conjunto fijo de puertos, siempre desea que los puertos se creará al mismo tiempo que su componente primario. Por lo tanto, tendrá que personalizar la herramienta de creación de elemento para que se crea un grupo de elementos en lugar de solo uno. Para ello, puede personalizar cómo se inicializa la herramienta de creación del elemento.  
  
 También puede invalidar lo que ocurre cuando se arrastra la herramienta hasta el diagrama o un elemento.  
  
## Personalizar el contenido de una herramienta de elemento  
 Cada herramienta de elemento almacena una instancia de un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> \(EGP\), que contiene una versión serializada de uno o más elementos del modelo y vínculos. De forma predeterminada, el EGP de una herramienta de elemento contiene una instancia de la clase que especifique para la herramienta. Puede cambiar mediante el reemplazo de *Sulenguaje*`ToolboxHelper.CreateElementToolPrototype`. Este método se llama cuando se carga el paquete DSL.  
  
 Un parámetro del método es el identificador de la clase que especificó en la definición de DSL. Cuando se llama al método con la clase que le interesa, puede agregar elementos adicionales en el EGP.  
  
 Debe incluir el EGP incrustar vínculos de un elemento principal para los elementos secundarios. También puede incluir vínculos de referencia.  
  
 En el ejemplo siguiente se crea un elemento principal y dos elementos incrustados. La clase principal se denomina resistencia y tiene dos relaciones de incrustación para elementos denominados Terminal. Las propiedades del rol incrustación se denominan Terminal1 y Terminal2, y ambos tienen una multiplicidad de 1.. 1.  
  
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
  
## Vea también  
 [Personalizar la creación y el movimiento de los elementos](../modeling/customizing-element-creation-and-movement.md)