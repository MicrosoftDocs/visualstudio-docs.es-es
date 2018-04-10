---
title: GetWinFXPath (tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: msbuild
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2adb5bed33a789301422910301a8788a8b0d069f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="getwinfxpath-task"></a>GetWinFXPath (Tarea)
La tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> devuelve el directorio del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] actual.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`WinFXPath`|Parámetro de salida de tipo **String** opcional.<br /><br /> Especifica la ruta de acceso real del motor en tiempo de ejecución de [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del tiempo de ejecución de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] nativo.|  
|`WinFXWowPath`|Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de los ensamblados de [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] del módulo **Windows on Windows** de 32 bits en sistemas de 64 bits.|  
  
## <a name="remarks"></a>Comentarios  
 Si la tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> se ejecuta en un procesador de 64 bits, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXWowPath**; de lo contrario, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXNativePath**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo se utiliza la tarea **GetWinFXPath** para detectar la ruta de acceso nativa del tiempo de ejecución de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```xml  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)