---
title: Archivos .Targets de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec05a2947bad76b0be4e7cf339bbef98a27644e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274240"
---
# <a name="msbuild-targets-files"></a>Archivos .Targets de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] incluye varios archivos .targets que contienen elementos, propiedades, destinos y tareas para escenarios comunes. Estos archivos se importan automáticamente en la mayoría de los archivos del proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para simplificar el mantenimiento y la legibilidad.  
  
 Normalmente, los proyectos importan uno o más archivos .targets para definir su proceso de compilación. Por ejemplo un proyecto de [!INCLUDE[csprcs](../includes/csprcs-md.md)] creado por [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] importará Microsoft.CSharp.targets, que importa Microsoft.Common.targets. El propio proyecto de [!INCLUDE[csprcs](../includes/csprcs-md.md)] definirá los elementos y las propiedades específicos de ese proyecto, pero las reglas de compilación estándar para un proyecto de [!INCLUDE[csprcs](../includes/csprcs-md.md)] se definen en los archivos .targets importados.  
  
 El valor `$(MSBuildToolsPath)` especifica la ruta de acceso de estos archivos .targets comunes. Si `ToolsVersion` es 4.0, los archivos están en la siguiente ubicación: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Para obtener información sobre cómo crear sus propios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obtener información sobre cómo usar el elemento `Import` para insertar un archivo del proyecto en otro archivo del proyecto, consulte [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) y [Cómo: Usar el mismo destino en varios archivos del proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Archivos .Targets comunes  
  
|Archivo .Targets|Descripción|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Define los pasos en el proceso de compilación estándar para proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../includes/csprcs-md.md)].<br /><br /> Importado mediante los archivos Microsoft.CSharp.targets y Microsoft.VisualBasic.targets, que incluyen la siguiente instrucción: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Define los pasos en el proceso de compilación estándar para proyectos de Visual C#.<br /><br /> Importado mediante los archivos del proyecto de Visual C# (.csproj), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Define los pasos en el proceso de compilación estándar para proyectos de Visual Basic.<br /><br /> Importado mediante los archivos del proyecto de Visual Basic (.vbproj), que incluyen la siguiente instrucción: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Vea también  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)


