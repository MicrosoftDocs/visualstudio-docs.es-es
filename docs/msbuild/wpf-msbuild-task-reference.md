---
title: "Referencia de tareas de MSBuild para WPF | Microsoft Docs"
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
  - "tareas de compilación [WPF MSBuild], motor de compilación de Microsoft"
  - "tareas de compilación mediante el motor de compilación de Microsoft [WPF MSBuild], compilar marcado y procesar recursos"
  - "referencia de tareas de MSBuild para WPF [WPF MSBuild]"
  - "referencia de tareas de MSBuild para WPF [WPF MSBuild], tabla de términos y definiciones"
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Referencia de tareas de MSBuild para WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de compilación de Windows Presentation Foundation \(WPF\) amplía el motor de compilación de Microsoft \(MSBuild\) con un conjunto adicional de tareas de compilación, incluidas las tareas para compilar marcado y procesar recursos.  
  
## En esta sección  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Clasifica un conjunto de recursos de código fuente como los que se van a incrustar en un ensamblado.  Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Genera un ensamblado si al menos una página de un [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] del proyecto hace referencia a un tipo declarado localmente en ese proyecto.  El ensamblado generado se quita una vez completado el proceso de compilación, o si éste no se produce.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Devuelve el subdirectorio del motor en tiempo de ejecución actual de [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)].  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Convierte archivos de proyecto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] no adaptables al formato binario compilado.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 Realiza una compilación de marcado de segundo paso en los archivos [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] que hacen referencia a tipos del mismo proyecto.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en un solo archivo para todo el ensamblado.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Incrusta uno o varios recursos \(.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en formato binario y otros tipos de extensiones\) en un archivo .resources.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Comprueba, actualiza o quita identificadores únicos \(UID\) para buscar todos los elementos [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] incluidos en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 Agrega el elemento **\<hostInBrowser\/\>** al manifiesto de aplicación \(*projectname*.exe.manifest\) cuando se compila un proyecto de [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## Vea también  
 [MSBuild](http://msdn.microsoft.com/es-es/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)