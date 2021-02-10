---
title: Referencia de tareas de MSBuild para WPF | Microsoft Docs
description: Vea una referencia de tarea para el proceso de compilación de Windows Presentation Foundation (WPF), que extiende MSBuild con tareas adicionales.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 94050565e6c5619781434c7a18307bfbf80b51f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933679"
---
# <a name="wpf-msbuild-task-reference"></a>Referencia de tareas de MSBuild para WPF

El proceso de compilación de Windows Presentation Foundation (WPF) amplía Microsoft Build Engine (MSBuild) con un conjunto adicional de tareas de compilación, incluidas tareas para compilar marcado y procesar recursos.

## <a name="in-this-section"></a>En esta sección

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Clasifica un conjunto de recursos de origen como los que se insertarán en un ensamblado. Si un recurso no es localizable, se incrusta en el ensamblado de aplicación principal; de lo contrario, se incrusta en un ensamblado satélite.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Genera un ensamblado si al menos una página de XAML del proyecto hace referencia a un tipo declarado localmente en ese proyecto. El ensamblado generado se quita una vez completado el proceso de compilación, o si este no se produce.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Devuelve el directorio del entorno de ejecución de .NET Framework actual.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Convierte archivos de proyecto de XAML no localizables en un formato binario compilado.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Realiza una compilación de marcado de segundo paso en archivos de XAML que hacen referencia a los tipos del mismo proyecto.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Combina los atributos y los comentarios de localización de uno o varios archivos de formato binario XAML en un solo archivo para todo el ensamblado.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Inserta uno o varios recursos ( *.jpg*, *.ico*, *.bmp*, XAML en formato binario y en otros tipos de extensiones) en un archivo *.resources*.

- [UidManager](../msbuild/uidmanager-task.md)

 Comprueba, actualiza o quita identificadores únicos (UID) para buscar todos los elementos XAML incluidos en los archivos XAML de origen.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Agrega el elemento **\<hostInBrowser />** al manifiesto de aplicación ( *\<projectname>.exe.manifest*) cuando se compila un proyecto de aplicación de explorador XAML (XBAP).

## <a name="see-also"></a>Vea también

- [MSBuild](../msbuild/msbuild.md)