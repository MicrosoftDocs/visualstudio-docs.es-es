---
title: Verificación de subtipos de un proyecto en tiempo de ejecución Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698182"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificar subtipos de un proyecto en tiempo de ejecución
Un VSPackage que depende de un subtipo de proyecto personalizado debe incluir lógica para buscar ese subtipo para que pueda producir un error correctamente si el subtipo no está presente. El siguiente procedimiento muestra cómo comprobar la presencia de un subtipo especificado.

### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar la presencia de un subtipo

1. Obtener la jerarquía del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> los objetos de proyecto y solución como un objeto agregando el código siguiente al VSPackage.

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

2. Convierta la jerarquía <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> en la interfaz.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtenga la lista de GUID de tipo <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>de proyecto invocando el archivo .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Compruebe la lista para el GUID del subtipo especificado.

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
