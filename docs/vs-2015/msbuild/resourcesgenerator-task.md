---
title: ResourcesGenerator (Tarea) | Microsoft Docs
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
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d2d470c91d6303976e5afcbffc7f4eff968ea04
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173308"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La tarea <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> inserta uno o varios recursos (.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en formato binario y en otros tipos de extensiones) en un archivo .resources.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`OutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del directorio de salida. Si la ruta de acceso no es una ruta absoluta, se trata como si fuese una ruta relativa al directorio raíz del proyecto.|  
|`OutputResourcesFile`|Parámetro de salida obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la ruta de acceso y el nombre del archivo .resources generado. Si la ruta de acceso no es una ruta absoluta, el archivo .resources se genera respecto al directorio raíz del proyecto.|  
|`ResourcesFiles`|Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica uno o más recursos que se van a insertar en el archivo .resources generado.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se genera un archivo .resources con un solo recurso .bmp. El recurso .bmp se genera en un directorio que es relativo al directorio raíz del proyecto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



