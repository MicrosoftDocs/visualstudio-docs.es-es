---
title: Comprobar los subtipos de un proyecto en tiempo de ejecución | Documentos de Microsoft
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
ms.openlocfilehash: b8898da6850c01c1a248b57b0fbc5f46be2a8ff4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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