---
title: GetWinFXPath (tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab8e15cef722e935dde322072f6834ba00be8bc5
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633972"
---
# <a name="getwinfxpath-task"></a>GetWinFXPath (Tarea)

La tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> devuelve el directorio del entorno de ejecución de .NET actual.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Descripción |
|-------------------| - |
| `WinFXPath` | Parámetro de salida de tipo **String** opcional.<br /><br /> Especifica la ruta de acceso real del entorno de ejecución de .NET. |
| `WinFXNativePath` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso del entorno de ejecución de .NET nativo. |
| `WinFXWowPath` | Parámetro obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de los ensamblados de .NET del módulo **Windows on Windows** de 32 bits en sistemas de 64 bits. |

## <a name="remarks"></a>Comentarios

 Si la tarea <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> se ejecuta en un procesador de 64 bits, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXWowPath**; de lo contrario, el valor del parámetro **WinFXPath** se establece en la ruta de acceso almacenada en el parámetro **WinFXNativePath**.

## <a name="example"></a>Ejemplo

 En el ejemplo siguiente se muestra cómo se utiliza la tarea **GetWinFXPath** para detectar la ruta de acceso nativa del entorno de ejecución de .NET.

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

- [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)
- [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
