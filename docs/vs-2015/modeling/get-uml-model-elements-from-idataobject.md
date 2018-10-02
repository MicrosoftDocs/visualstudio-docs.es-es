---
title: Obtener elementos del modelo UML a partir de IDataObject | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: a69a6f20fdccdce9d8795c68bf0a70c74604428b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580054"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Obtener elementos del modelo UML a partir de IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [elementos del modelo UML obtener a partir de IDataObject](https://docs.microsoft.com/visualstudio/modeling/get-uml-model-elements-from-idataobject).  
  
Cuando el usuario arrastra elementos desde cualquier origen a un diagrama, los elementos arrastrados se codifican en un objeto `System.Windows.Forms.IDataObject`. La codificación depende del tipo de objeto de origen. El siguiente fragmento muestra cómo recuperar los elementos cuando el origen es un diagrama UML.  
  
> [!NOTE]
>  La mayoría de las operaciones que se deben realizar en los modelos UML puede realizarse mediante el uso de los tipos en el que se define en los ensamblados **Microsoft.VisualStudio.Uml.Interfaces** y  **Microsoft.VisualStudio.ArchitectureTools.Extensibility**. Sin embargo, para este propósito, es necesario utilizar algunas clases que formen parte de la implementación de las herramientas de modelado UML. Por ejemplo, `ShapeElement` en este fragmento no es igual que el objeto `IShape` UML. Para reducir el riesgo de provocar un estado incoherente en el modelo y diagramas UML, es mejor evitar el uso de los métodos en estas clases de implementación, excepto si no hay ninguna alternativa.  
  
## <a name="code-sample"></a>Ejemplo de código  
 El proyecto debe hacer referencia a la siguiente [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] ensamblados:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [versión]**  
  
 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams. [versión]**  
  
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



