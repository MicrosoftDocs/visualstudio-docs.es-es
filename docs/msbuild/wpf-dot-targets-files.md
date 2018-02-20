---
title: Archivos .Targets de WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- combining tasks into a .targets file to build an MSBuild project [WPF MSBuild]
- WPF .targets files [WPF MSBuild], introduction
- WPF .targets files [WPF MSBuild]
ms.assetid: e85a3ff4-dedd-4ff4-9b22-3a1e94755362
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6f1fbf6f4a5e1cc0c49b6d7ad7513d17eb07b3c2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="wpf-targets-files"></a>Archivos .Targets de WPF
[!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] extiende la herramienta [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] agregando un conjunto de tareas específicas de [!INCLUDE[TLA2#tla_wpf](../msbuild/includes/tla2sharptla_wpf_md.md)] que se combinan en un archivo .targets especial, **Microsoft.WinFX.targets**. Este archivo combina el conjunto de tareas de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] que se necesitan para compilar un proyecto de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] en [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Archivos .Targets](../msbuild/msbuild-dot-targets-files.md)   
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)