---
title: Archivos .Targets de WPF | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c61e305868045664af7333bbb7dcce0beed54370
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56623182"
---
# <a name="wpf-targets-files"></a>Archivos .targets de WPF
[!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)] extiende la herramienta [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] mediante la incorporación de un conjunto de tareas específicas de [!INCLUDE[TLA2#tla_wpf](../msbuild/includes/tla2sharptla_wpf_md.md)] que se combinan en un archivo *.targets* especial, *Microsoft.WinFX.targets*. Este archivo combina el conjunto de tareas de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] que se necesitan para compilar un proyecto de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] en [!INCLUDE[TLA#tla_winclient](../misc/includes/tlasharptla_winclient_md.md)].

## <a name="see-also"></a>Vea también
- [Archivos .targets de MSBuild](../msbuild/msbuild-dot-targets-files.md)
- [Referencia de MSBuild](../msbuild/msbuild-reference.md)
- [Compilar una aplicación de WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)