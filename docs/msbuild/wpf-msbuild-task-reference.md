---
title: Referencia de tareas de MSBuild para WPF | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 121c3da6d3e2609c1a271177e089e0f38a0d89fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639107"
---
# <a name="wpf-msbuild-task-reference"></a>Referencia de tareas de MSBuild para WPF
El proceso de compilación de Windows Presentation Foundation (WPF) amplía Microsoft Build Engine (MSBuild) con un conjunto adicional de tareas de compilación, incluidas tareas para compilar marcado y procesar recursos.

## <a name="in-this-section"></a>En esta sección
- [FileClassifier](../msbuild/fileclassifier-task.md)

 Clasifica un conjunto de recursos de origen como los que se insertarán en un ensamblado. Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Genera un ensamblado si al menos una página de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] del proyecto hace referencia a un tipo declarado localmente en ese proyecto. El ensamblado generado se quita una vez completado el proceso de compilación, o si este no se produce.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Devuelve el directorio del runtime [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] actual.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Convierte archivos de proyecto de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] no localizables en un formato binario compilado.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Realiza una compilación de marcado de segundo paso en archivos de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] que hacen referencia a los tipos del mismo proyecto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Combina los atributos y los comentarios de localización de uno o varios archivos de formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en un solo archivo para todo el ensamblado.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Inserta uno o varios recursos (*.jpg*, *.ico*, *.bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en formato binario y en otros tipos de extensiones) en un archivo *.resources*.

- [UidManager](../msbuild/uidmanager-task.md)

 Comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos de [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] incluidos en los archivos [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de origen.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Agrega el elemento **\<hostInBrowser />** al manifiesto de aplicación (*\<nombreproyecto>.exe.manifest*) cuando se compila un proyecto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].

## <a name="see-also"></a>Vea también
- [MSBuild](../msbuild/msbuild.md)