---
title: Agregar un atributo a un elemento de proyecto | Microsoft Docs
description: Obtenga información sobre cómo agregar un atributo a un elemento de proyecto en Visual Studio mediante los métodos de interoperabilidad de Shell GetItemAttribute y SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 36fc5905fd2b1423865982a80a6cb2ba6a803cc5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902025"
---
# <a name="add-an-attribute-to-a-project-item"></a>Agregar un atributo a un elemento de proyecto
Los <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> y obtienen y establecen el valor de los atributos de un elemento de proyecto. SetItemAttribute crea el atributo si aún no existe y lo agrega a los metadatos del elemento de proyecto.

## <a name="add-an-attribute-to-a-project-item"></a>Agregar un atributo a un elemento de proyecto

- El código siguiente usa el <xref:EnvDTE.DTE> objeto de automatización y el método para agregar un atributo a un elemento de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> proyecto. El identificador del elemento de proyecto se obtiene del nombre del elemento de proyecto "program.cs". El atributo "MyAttribute" se agrega a este elemento de proyecto y se le asigna el valor "MyValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Consulta también
- [Conservación de datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
