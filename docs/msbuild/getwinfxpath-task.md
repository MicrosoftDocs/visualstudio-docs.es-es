---
title: "GetWinFXPath (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "obtener el directorio del runtime de .NET Framework actual [WPF MSBuild]"
  - "GetWinFXPath (tarea) [WPF MSBuild]"
  - "GetWinFXPath (tarea) [WPF MSBuild], parámetros"
  - "obtener la ruta de acceso al runtime de .NET Framework actual [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# GetWinFXPath (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> devuelve el directorio del motor en tiempo de ejecución actual de [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].  
  
## Parámetros de la tarea  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WinFXPath`|Parámetro de salida de tipo **String** opcional.<br /><br /> Especifica la ruta de acceso real del motor en tiempo de ejecución de [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del motor en tiempo de ejecución de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] nativo.|  
|`WinFXWowPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de los ensamblados de [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] del módulo **Windows on Windows** de 32 bits en sistemas de 64 bits.|  
  
## Comentarios  
 Si la tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> se ejecuta en un procesador de 64 bits, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXWowPath**; de lo contrario, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXNativePath**.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo se utiliza la tarea **GetWinFXPath** para detectar la ruta de acceso nativa del motor en tiempo de ejecución de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)