---
title: Comprobación de subtipos de un proyecto en tiempo de ejecución | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22e3205f3a8bd8ef7ce7e44b775ae1ef5a30cfa5
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586214"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Compruebe los subtipos de un proyecto en tiempo de ejecución
Un VSPackage que depende de un subtipo de proyecto personalizada debe incluir la lógica para buscar que para que se puede producir un error correctamente si no está presente el subtipo de subtipo. El siguiente procedimiento muestra cómo comprobar la presencia de un subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para comprobar la presencia de un subtipo  
  
1.  Obtener la jerarquía del proyecto de los objetos de proyecto y solución como un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto agregando el código siguiente para el VSPackage.  
  
    ```csharp  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Convertir la jerarquía para el <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaz.  
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obtener la lista de GUID de tipo de proyecto invocando el <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Compruebe la lista para el GUID del subtipo especificado.  
  
    ```csharp  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Subtipos de proyecto](../extensibility/internals/project-subtypes.md)   
 [Diseño de subtipos de proyecto](../extensibility/internals/project-subtypes-design.md)   
 [Las propiedades y métodos ampliados por subtipos de proyecto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)