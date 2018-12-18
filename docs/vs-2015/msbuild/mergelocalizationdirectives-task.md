---
title: MergeLocalizationDirectives (Tarea) | Microsoft Docs
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 842e36d549dab7d6e7c2f7d1da2f3e9b4db4e9d3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268208"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La tarea <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en un solo archivo para todo el ensamblado.  
  
## <a name="task-parameters"></a>Parámetros de tareas  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Parámetro obligatorio de tipo **ITaskItem[]**.<br /><br /> Especifica la lista de los archivos de directivas de localización para los archivos individuales en formato binario de [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)].|  
|`OutputFile`|Parámetro de salida obligatorio de tipo **String**.<br /><br /> Especifica la ruta de acceso de salida del ensamblado de directivas de localización compilado.|  
  
## <a name="remarks"></a>Comentarios  
 Puede agregar atributos y comentarios de localización al contenido de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]. Con la compatibilidad para la localización incluida en [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)], puede quitar los atributos y los comentarios de localización y colocarlos en un archivo .loc que sea independiente del ensamblado generado. Puede hacerlo mediante el atributo **LocalizationPropertyStorage**. Para obtener más información sobre atributos y comentarios de localización, y **LocalizationPropertyStorage**, consulte [Atributos y comentarios sobre localización](http://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
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
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild para WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referencia de tareas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Compilar una aplicación de WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)



