---
title: "Comprobar los subtipos de un proyecto en tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2e4ebcf8ca85c0ed6face82dfd91f8c5266013f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Comprobar los subtipos de un proyecto en tiempo de ejecución
Un VSPackage que depende de un subtipo de proyecto personalizado debe incluir lógica para buscar que para que puede generar un error si no está presente el subtipo de subtipo. El siguiente procedimiento muestra cómo comprobar la presencia de un subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para comprobar la presencia de un subtipo  
  
1.  Obtener la jerarquía del proyecto de los objetos de proyecto y la solución como un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto agregando el código siguiente para el VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Convierte la jerarquía para el <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaz.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obtener la lista de GUID de tipo de proyecto mediante la invocación de la <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Busque el GUID del subtipo especificado de la lista.  
  
    ```  
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
 [Propiedades y métodos ampliados por subtipos de proyecto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)