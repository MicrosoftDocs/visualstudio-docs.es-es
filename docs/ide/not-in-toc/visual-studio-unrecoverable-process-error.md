---
title: Error irrecuperable del proceso de Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editor
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 703e27a95d6a0f4b680ad6a729dc974dfe98fc11
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# Error irrecuperable del proceso de Visual Studio

Visual Studio 2017 usa varios procesos fuera de proceso para ejecutar las tareas en segundo plano necesarias, como pruebas unitarias en vivo, analizadores de código y mucho más. Estos procesos se ejecutan fuera de proceso para proporcionar ventajas de rendimiento a Visual Studio, como permitirle responder con mayor rapidez cuando se ejecutan trabajos de larga ejecución que consumen muchos recursos. Además, dado que Visual Studio es un proceso de 32 bits, la ejecución de procesos fuera de proceso proporciona a los trabajos que consumen mucha memoria un mayor espacio de memoria en el que operar.

Si alguno de estos procesos necesarios se detiene por cualquier razón, aparecerá una barra de información emergente con el mensaje siguiente:

"Unfortunately, a process used by Visual Studio has encountered an unrecoverable error. We recommend saving your work, and then closing and restarting Visual Studio." (Desafortunadamente, un proceso usado por Visual Studio ha encontrado un error irrecuperable. Le recomendamos que guarde su trabajo y, después, cierre y reinicie Visual Studio).

Si ve este mensaje, debe guardar inmediatamente el trabajo y, después, cerrar y reiniciar Visual Studio. Si no lo hace, Visual Studio puede bloquearse en cualquier momento.

## Lista de procesos

A continuación se muestra una lista de procesos fuera de proceso usados por Visual Studio que deben estar en ejecución para que Visual Studio funcione correctamente.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe
