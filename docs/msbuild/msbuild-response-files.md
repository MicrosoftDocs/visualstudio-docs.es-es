---
title: "Archivos de respuesta de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "archivos .rsp"
  - "MSBuild, archivos .rsp"
  - "MSBuild, archivos de respuesta"
  - "archivos de respuesta, MSBuild"
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Archivos de respuesta de MSBuild
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los archivos de respuesta \(.rsp\) son archivos de texto que contienen modificadores de la línea de comandos de MSBuild.exe.  Cada modificador puede estar en una línea independiente o todos los modificadores pueden estar en una única línea.  Las líneas de comentario van precedidas por el símbolo **\#**.  El modificador **@** se utiliza para pasar otro archivo de respuesta a MSBuild.exe.  
  
 El archivo de respuesta automática es un archivo .rsp especial que MSBuild.exe utiliza automáticamente al compilar un proyecto.  Este archivo, MSBuild.rsp, debe estar en el mismo directorio que MSBuild.exe, de lo contrario no se encontrará.  Puede editar este archivo para especificar los modificadores de la línea de comandos predeterminados a MSBuild.exe.  Por ejemplo, si utiliza el mismo registrador cada vez que compila un proyecto, puede agregar el modificador **\/logger** a MSBuild.rsp y MSBuild.exe utilizará el registrador cada vez que compile un proyecto.  
  
## Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md)