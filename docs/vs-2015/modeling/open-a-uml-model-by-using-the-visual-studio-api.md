---
title: Abrir un modelo UML mediante la API de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 694f10fb0af440513331aa6e76dbf9a59a16d340
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668509"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Abrir un modelo UML mediante la API de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

También se pueden abrir modelos y diagramas en la interfaz de usuario de Visual Studio a través de la API.

 Si solamente desea leer un modelo en el código del programa sin hacerlo visible al usuario, puede usar los siguientes métodos:

- ModelBus de Visual Studio permite acceder a los modelos y los elementos que hay dentro de ellos. También ofrece un método estándar para crear vínculos entre modelos. Para obtener más información, vea [integrar modelos UML con otros modelos y herramientas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- Puede abrir un modelo en modo de solo lectura. Para obtener más información, vea [leer un modelo UML en el código del programa](../modeling/read-a-uml-model-in-program-code.md).

## <a name="opening-models-and-diagrams-in-visual-studio"></a><a name="Showing"></a> Abrir modelos y diagramas en Visual Studio
 Para abrir un modelo en la interfaz de usuario, use la API estándar de Visual Studio `EnvDTE.DTE`. Existen dos conversiones útiles que pueden realizarse en elementos de proyecto de modelado:

- `EnvDTE.Project` se puede convertir a y desde `IModelingProject` , si el proyecto es un proyecto de modelado y si el proyecto se carga en el AppDomain actual.

- Si el elemento es un diagrama de UML, `EnvDTE.ProjectItem` se puede convertir a `IDiagramContext`, y viceversa.

  En el ejemplo siguiente, su proyecto debería importar estas referencias:

- EnvDTE

- Microsoft.VisualStudio.ArchitectureTools.Extensibility

- Microsoft.VisualStudio.Modeling.Sdk.[versión]

- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[versión]

- Microsoft.VisualStudio.Shell.Immutable.[versión]

- Microsoft.VisualStudio.Uml.Interfaces

- System.ComponentModel.Composition

  En este ejemplo se abre un modelo UML en Visual Studio:

```
using EnvDTE; // Visual Studio API for loading diagrams
using
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   // for ICommandExtension and other handler types
using Microsoft.VisualStudio.Uml.Classes;
   // for basic UML types
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   // for model construction methods
using EnvDTE;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
                             // for IDiagram
...
```

 En una extensión de Visual Studio, puede realizar esta declaración para acceder al proveedor de servicios de host:

```
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}
...
```

 En un método, puede tener acceso a un proyecto, por ejemplo, el proyecto actual:

```
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
IModelingProject modelingProject = project as IModelingProject;
if (modelingProject == null) return; // not a modeling project

// Access the model's store and contents.
IModelStore store = modelingProject.Store;
foreach (IElement element in store.Root.OwnedElements) {...}

// Open all the project's diagrams.
foreach (ProjectItem item in project.ProjectItems)
{
     IDiagramContext modelingItem = item as IDiagramContext;
     if (modelingItem == null)
         continue; // not a model diagram
     IDiagram diagram = modelingItem.CurrentDiagram;
     if (diagram == null)
     {
        // Diagram is closed. Open it.
        item.Open().Activate();
        diagram = modelingItem.CurrentDiagram;
     }
     // Access the shapes.
     foreach (IShape<IElement> shape
               in diagram.GetChildShapes<IElement>())
     {
       IElement displayedElement = shape.Element;
       ...
     }
   }
}
```

## <a name="see-also"></a>Consulte también
 [Programar con la API de UML](../modeling/programming-with-the-uml-api.md) [ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md)
