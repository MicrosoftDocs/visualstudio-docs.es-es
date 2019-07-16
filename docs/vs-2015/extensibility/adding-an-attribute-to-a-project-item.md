---
title: Agrega un atributo a un elemento de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184817"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Adición de un atributo a un elemento de proyecto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> obtener y establecer el valor de los atributos de un elemento de proyecto. SetItemAttribute crea el atributo si ya no existe, éste se agrega a los metadatos de elemento de proyecto.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Agrega un atributo a un elemento de proyecto  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Para agregar un atributo a un elemento de proyecto  
  
- El siguiente código utiliza el <xref:EnvDTE.DTE> objeto de automatización y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para agregar un atributo a un elemento de proyecto. El identificador de elemento de proyecto se obtiene del nombre de elemento de proyecto "program.cs". El atributo "MyAttribute" se agrega a este elemento de proyecto y se le asigna el valor "MyValue".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Conservación de datos en el archivo de proyecto de MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
