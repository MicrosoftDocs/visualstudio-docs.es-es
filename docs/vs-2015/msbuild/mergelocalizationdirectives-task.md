---
title: MergeLocalizationDirectives (Tarea) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703420"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La tarea <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en un solo archivo para todo el ensamblado.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Parámetro obligatorio de tipo **ITaskItem[]** .<br /><br /> Especifica la lista de los archivos de directivas de localización para los archivos individuales en formato binario de [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
|`OutputFile`|Parámetro de salida obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de salida del ensamblado de directivas de localización compilado.|  
  
## <a name="remarks"></a>Comentarios  
 Puede agregar atributos y comentarios de localización al contenido de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]. Con la compatibilidad para la localización incluida en [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)], puede quitar los atributos y los comentarios de localización y colocarlos en un archivo .loc que sea independiente del ensamblado generado. Puede hacerlo mediante el atributo **LocalizationPropertyStorage**. Para obtener más información sobre los atributos y los comentarios de localización, y **LocalizationPropertyStorage**, consulte [atributos y comentarios de localización](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se combinan los comentarios de localización de varios archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de formato binario en un solo archivo .loc.  
  
```  
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
  
## <a name="see-also"></a>Consulte también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
