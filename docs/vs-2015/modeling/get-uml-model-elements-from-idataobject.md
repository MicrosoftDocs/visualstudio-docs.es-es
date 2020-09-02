---
title: Obtener elementos del modelo UML de IDataObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666078"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Obtener elementos del modelo UML a partir de IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando el usuario arrastra elementos desde cualquier origen a un diagrama, los elementos arrastrados se codifican en un objeto `System.Windows.Forms.IDataObject`. La codificación depende del tipo de objeto de origen. El siguiente fragmento muestra cómo recuperar los elementos cuando el origen es un diagrama UML.

> [!NOTE]
> La mayoría de las operaciones que tiene que hacer en los modelos UML se pueden realizar mediante los tipos de definidos en los ensamblados **Microsoft. VisualStudio. UML. interfaces** y **Microsoft. VisualStudio. ArchitectureTools. Extensibility**. Sin embargo, para este propósito, es necesario utilizar algunas clases que formen parte de la implementación de las herramientas de modelado UML. Por ejemplo, `ShapeElement` en este fragmento no es igual que el objeto `IShape` UML. Para reducir el riesgo de provocar un estado incoherente en el modelo y diagramas UML, es mejor evitar el uso de los métodos en estas clases de implementación, excepto si no hay ninguna alternativa.

## <a name="code-sample"></a>Ejemplo de código
 El proyecto debe hacer referencia a los siguientes [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] ensamblados:

 **Microsoft.VisualStudio.Modeling.Sdk.[versión]**

 **Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]**

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

 Para obtener más información sobre `ElementGroupPrototype` y el `Store` en el que se implementan las herramientas de modelado UML, vea [modelado del SDK para Visual Studio-lenguajes específicos de dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Consulte también
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md) [definir un comando de menú en un diagrama de modelado](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
