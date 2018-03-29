---
title: Archivos de respuesta de MSBuild | Microsoft Docs
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
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: ''
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 40a9f7b6e1456c511e70937ac6a1cff23dad30d0
ms.sourcegitcommit: a80e7ef2f0a0f6d906a44f4d696aeb208bc1ad70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2018
---
# <a name="msbuild-response-files"></a>Archivos de respuesta de MSBuild
Los archivos de respuesta (.rsp) son archivos de texto que contienen modificadores de línea de comandos de MSBuild.exe. Cada modificador puede estar en una línea independiente o todos los modificadores pueden aparecen en una sola línea. Las líneas de comentario van precedidas del símbolo **#**. El modificador **@** se usa para pasar otro archivo de respuesta a MSBuild.exe.  
  
## <a name="msbuildrsp"></a>MSBuild.rsp
El archivo de respuesta automática es un archivo .rsp especial que MSBuild.exe usa automáticamente al crear un proyecto. Este archivo, MSBuild.rsp, debe estar en el mismo directorio que MSBuild.exe, de lo contrario no se encontrará. Puede editar este archivo para especificar los modificadores de línea de comandos predeterminados a MSBuild.exe. Por ejemplo, si usa el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **/logger** a MSBuild.rsp y MSBuild.exe usará el registrador cada vez que se compila un proyecto.  

## <a name="directorybuildrsp"></a>Directory.Build.rsp
En la versión 15.6 y posteriores, MSBuild buscará en los directorios primarios del proyecto un archivo denominado `Directory.Build.rsp`.  Esto puede resultar útil en un repositorio de código fuente para proporcionar argumentos predeterminados durante las compilaciones de línea de comandos.  También se puede utilizar para especificar los argumentos de línea de comandos de las compilaciones hospedadas.

## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)