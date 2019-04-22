---
title: Referencia de tareas de MSBuild para WPF | Microsoft Docs
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
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 785e3960148d627e437d15e8662dfd76dccc53c0
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659337"
---
# <a name="wpf-msbuild-task-reference"></a>Referencia de tareas de MSBuild para WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proceso de compilación de Windows Presentation Foundation (WPF) amplía Microsoft Build Engine (MSBuild) con un conjunto adicional de tareas de compilación, incluidas tareas para compilar marcado y procesar recursos.  
  
## <a name="in-this-section"></a>En esta sección  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Clasifica un conjunto de recursos de origen como los que se insertarán en un ensamblado. Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Genera un ensamblado si al menos una página de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] del proyecto hace referencia a un tipo declarado localmente en ese proyecto. El ensamblado generado se quita una vez completado el proceso de compilación, o si este no se produce.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Devuelve el directorio del runtime [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] actual.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Convierte archivos de proyecto de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] no localizables en un formato binario compilado.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Realiza una compilación de marcado de segundo paso en archivos de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] que hacen referencia a los tipos del mismo proyecto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en un solo archivo para todo el ensamblado.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Inserta uno o varios recursos (.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] en formato binario y en otros tipos de extensiones) en un archivo .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos de [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] incluidos en los archivos [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] de origen.  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Agrega el elemento **\<hostInBrowser />** al manifiesto de aplicación (*nombreproyecto*.exe.manifest) cuando se compila un proyecto [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [MSBuild](http://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
