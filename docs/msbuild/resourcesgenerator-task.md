---
title: "ResourcesGenerator (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "incrustar recursos en un archivo .resources [WPF MSBuild]"
  - "ResourcesGenerator (tarea) [WPF MSBuild]"
  - "ResourcesGenerator (tarea) [WPF MSBuild], parámetros"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResourcesGenerator (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> incrusta uno o varios recursos \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en formato binario y en otros tipos de extensiones\) en un archivo .resources.  
  
## Parámetros de la tarea  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`OutputPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del directorio de resultados.  Si la ruta de acceso no es una ruta absoluta, se trata como si fuese una ruta relativa al directorio raíz del proyecto.|  
|`OutputResourcesFile`|Parámetro de salida obligatorio de tipo **ITaskItem\[\]**.<br /><br /> Especifica la ruta de acceso y el nombre del archivo .resources generado.  Si la ruta de acceso no es una ruta absoluta, el archivo .resources se genera respecto al directorio raíz del proyecto.|  
|`ResourcesFiles`|Parámetro obligatorio de tipo **ITaskItem\[\]**.<br /><br /> Especifica uno o más recursos que se van a incrustar en el archivo .resources generado.|  
  
## Ejemplo  
 En el ejemplo siguiente, se genera un archivo .resources con un solo recurso .bmp.  El recurso .bmp se genera en un directorio que es relativo al directorio raíz del proyecto.  
  
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
  
## Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)