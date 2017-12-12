---
title: Archivos de respuesta de MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
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
caps.latest.revision: "3"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: a9ceab64ec0009dd143f42e1b94538690780f1bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-response-files"></a>Archivos de respuesta de MSBuild
Los archivos de respuesta (.rsp) son archivos de texto que contienen modificadores de línea de comandos de MSBuild.exe. Cada modificador puede estar en una línea independiente o todos los modificadores pueden aparecen en una sola línea. Las líneas de comentario van precedidas del símbolo **#**. El modificador **@** se usa para pasar otro archivo de respuesta a MSBuild.exe.  
  
 El archivo de respuesta automática es un archivo .rsp especial que MSBuild.exe usa automáticamente al crear un proyecto. Este archivo, MSBuild.rsp, debe estar en el mismo directorio que MSBuild.exe, de lo contrario no se encontrará. Puede editar este archivo para especificar los modificadores de línea de comandos predeterminados a MSBuild.exe. Por ejemplo, si usa el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **/logger** a MSBuild.rsp y MSBuild.exe usará el registrador cada vez que se compila un proyecto.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)