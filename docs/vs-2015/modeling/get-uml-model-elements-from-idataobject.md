---
title: Obtener elementos del modelo UML a partir de IDataObject | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5f60338a8a856b4c6ef8fa913d6d7168ff67bb9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427037"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Obtener elementos del modelo UML a partir de IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando el usuario arrastra elementos desde cualquier origen a un diagrama, los elementos arrastrados se codifican en un objeto `System.Windows.Forms.IDataObject`. La codificación depende del tipo de objeto de origen. El siguiente fragmento muestra cómo recuperar los elementos cuando el origen es un diagrama UML.  
  
> [!NOTE]
> La mayoría de las operaciones que se deben realizar en los modelos UML puede realizarse mediante el uso de los tipos en el que se define en los ensamblados **Microsoft.VisualStudio.Uml.Interfaces** y  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Sin embargo, para este propósito, es necesario utilizar algunas clases que formen parte de la implementación de las herramientas de modelado UML. Por ejemplo, `ShapeElement` en este fragmento no es igual que el objeto `IShape` UML. Para reducir el riesgo de provocar un estado incoherente en el modelo y diagramas UML, es mejor evitar el uso de los métodos en estas clases de implementación, excepto si no hay ninguna alternativa.  
  
## <a name="code-sample"></a>Ejemplo de código  
 El proyecto debe hacer referencia a la siguiente [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] ensamblados:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]**  
  
 **System.Windows.Forms**  
  
```  
using Microsoft.VisualStudio.Modeling;    
  // for ElementGroupPrototype  
using Microsoft.VisualStudio.Modeling.Diagrams;    
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs  
…   
  /// <summary>  
  /// Retrieves UML IElements from drag arguments.  
  /// Works for drags from UML diagrams.  
  /// </summary>  
  private IEnumerable<IElement> GetModelElementsFromDragEvent  
                  (DiagramDragEventArgs dragEvent)  
  {  
     //ElementGroupPrototype is the container for  
     //dragged and copied elements and toolbox items.  
     ElementGroupPrototype prototype =  
        dragEvent.Data.  
        GetData(typeof(ElementGroupPrototype))  
                     as ElementGroupPrototype;  
     // Locate the originals in the implementation store.  
     IElementDirectory implementationDirectory =   
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;  
  
     return  prototype.ProtoElements.Select(  
       prototypeElement =>   
       {  
          ModelElement element = implementationDirectory  
                .FindElement(prototypeElement.ElementId);  
          ShapeElement shapeElement = element as ShapeElement;  
          if (shapeElement != null)  
          {   
            // Dragged from a diagram.  
            return shapeElement.ModelElement as IElement;  
          }  
          else  
          {   
            // Dragged from UML Model Explorer.  
            return element as IElement;  
          }  
        });  
    }  
```  
  
 Para obtener más información acerca de `ElementGroupPrototype` y `Store` en que se implementan las herramientas de modelado UML, vea [SDK de modelado de Visual Studio - lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).  
  
## <a name="see-also"></a>Vea también  
 [Programación con la API de UML](../modeling/programming-with-the-uml-api.md)   
 [Definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
