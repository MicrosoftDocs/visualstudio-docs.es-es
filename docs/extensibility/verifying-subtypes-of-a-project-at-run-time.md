---
title: Comprobación de subtipos de un proyecto en tiempo de ejecución | Microsoft Docs
description: Obtenga información sobre cómo hacer que el VSPackage compruebe la presencia de un subtipo de proyecto personalizado especificado del que depende.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 621a40e1857d7c78ec4c5be08a3b7c3808a0d48b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905478"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Comprobación de los subtipos de un proyecto en tiempo de ejecución
Un VSPackage que depende de un subtipo de proyecto personalizado debe incluir lógica para buscar ese subtipo de modo que pueda producir un error correctamente si el subtipo no está presente. El procedimiento siguiente muestra cómo comprobar la presencia de un subtipo especificado.

### <a name="to-verify-the-presence-of-a-subtype"></a>Para comprobar la presencia de un subtipo

1. Obtenga la jerarquía de proyectos de los objetos de proyecto y solución como un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto agregando el código siguiente al VSPackage.

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

2. Convierte la jerarquía en la <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaz .

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtenga la lista de GUID de tipo de proyecto invocando <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Compruebe la lista del GUID del subtipo especificado.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Consulta también
- [Subtipos de proyecto](../extensibility/internals/project-subtypes.md)
- [Diseño de subtipos de proyecto](../extensibility/internals/project-subtypes-design.md)
- [Propiedades y métodos extendidos por subtipos de proyecto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
