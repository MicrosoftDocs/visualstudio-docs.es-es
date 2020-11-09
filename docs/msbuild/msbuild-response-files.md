---
title: Archivos de respuesta de MSBuild | Microsoft Docs
description: Obtenga información sobre los archivos de respuesta de MSBuild o .rsp, archivos de texto que contienen modificadores de la línea de comandos de MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b18ad00c3be8c3684551f28bc170dbd4a8428533
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049144"
---
# <a name="msbuild-response-files"></a>Archivos de respuesta de MSBuild

Los archivos de respuesta ( *.rsp* ) son archivos de texto que contienen modificadores de línea de comandos de *MSBuild.exe*. Cada modificador puede estar en una línea independiente o todos los modificadores pueden aparecen en una sola línea. Las líneas de comentario van precedidas del símbolo **#** . El modificador **@** se usa para pasar otro archivo de respuesta a *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

El archivo de respuesta automática es un archivo *.rsp* especial que *MSBuild.exe* usa automáticamente al compilar un proyecto. Este archivo, *MSBuild.rsp* , debe estar en el mismo directorio que *MSBuild.exe* , de lo contrario, no se encuentra. Puede editar este archivo para especificar los modificadores de línea de comandos predeterminados para *MSBuild.exe*. Por ejemplo, si usa el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **-logger** a *MSBuild.rsp* y *MSBuild.exe* usará el registrador cada vez que se compile un proyecto.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

En la versión 15.6 y posteriores, MSBuild busca en los directorios primarios del proyecto un archivo denominado *Directory.Build.rsp*.  Esto puede resultar útil en un repositorio de código fuente para proporcionar argumentos predeterminados durante las compilaciones de línea de comandos.  También se puede utilizar para especificar los argumentos de línea de comandos de las compilaciones hospedadas.

## <a name="see-also"></a>Vea también

- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)
