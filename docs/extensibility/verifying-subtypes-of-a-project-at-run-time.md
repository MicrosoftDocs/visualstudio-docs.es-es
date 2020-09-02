---
title: Comprobar subtipos de un proyecto en tiempo de ejecución | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698182"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Comprobar los subtipos de un proyecto en tiempo de ejecución
Un VSPackage que depende de un subtipo de proyecto personalizado debe incluir lógica para buscar ese subtipo, de modo que se pueda producir un error sin problemas si el subtipo no está presente. En el procedimiento siguiente se muestra cómo comprobar la presencia de un subtipo especificado.

### <a name="to-verify-the-presence-of-a-subtype"></a>Para comprobar la presencia de un subtipo

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>Agregue el código siguiente al VSPackage para obtener la jerarquía del proyecto y los objetos de la solución como un objeto.

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

2. Convierta la jerarquía a la <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interfaz.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtiene la lista de los GUID de tipo de proyecto mediante la invocación de <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Busque en la lista el GUID del subtipo especificado.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Vea también
- [Subtipos de proyecto](../extensibility/internals/project-subtypes.md)
- [Diseño de subtipos de proyecto](../extensibility/internals/project-subtypes-design.md)
- [Propiedades y métodos extendidos por subtipos de proyecto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
