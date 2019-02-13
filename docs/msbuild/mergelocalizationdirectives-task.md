---
title: MergeLocalizationDirectives (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0cb537f045f3ed2409dfcf0def2826057fd55687
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927752"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives (Tarea)
La tarea <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en un solo archivo para todo el ensamblado.

## <a name="task-parameters"></a>Parámetros de tareas

| Parámetro | Descripción |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la lista de los archivos de directivas de localización para los archivos individuales en formato binario de [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputFile` | Parámetro de salida obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de salida del ensamblado de directivas de localización compilado. |

## <a name="remarks"></a>Comentarios
Puede agregar atributos y comentarios de localización al contenido de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]. Con la compatibilidad para la localización incluida en [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)], puede quitar los atributos y los comentarios de localización y colocarlos en un archivo *.loc* que sea independiente del ensamblado generado. Puede hacerlo mediante el atributo **LocalizationPropertyStorage**. Para obtener más información sobre atributos y comentarios de localización y **LocalizationPropertyStorage**, vea [Atributos y comentarios sobre localización](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Ejemplo
En el siguiente ejemplo se combinan los comentarios de localización de varios archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de formato binario en un solo archivo *.loc*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vea también
[Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)  
[Referencia de tareas de MSBuild para WPF](../msbuild/wpf-msbuild-task-reference.md)  
[Referencia de MSBuild](../msbuild/msbuild-reference.md)  
[Referencia de tareas de MSBuild](../msbuild/msbuild-task-reference.md)  
[Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
