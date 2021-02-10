---
title: Un proceso ha detectado un error irrecuperable
description: Conozca los procesos que pueden encontrarse con errores irrecuperables durante las operaciones normales de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/10/2020
ms.topic: troubleshooting
helpviewer_keywords:
- unrecoverable error
- error, process
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e2ff53ecf1e3f3b377180fe85f972dca665b81f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909157"
---
# <a name="visual-studio-unrecoverable-process-error"></a>Error irrecuperable del proceso de Visual Studio

Visual Studio usa varios procesos fuera de proceso para ejecutar las tareas en segundo plano necesarias, como Live Unit Testing, analizadores de código, etc. Estos procesos se ejecutan fuera de proceso para proporcionar ventajas de rendimiento a Visual Studio, como permitirle responder con mayor rapidez cuando se ejecutan trabajos de larga ejecución que consumen muchos recursos. Además, dado que Visual Studio es un proceso de 32 bits, la ejecución de procesos fuera de proceso proporciona a los trabajos que consumen mucha memoria un mayor espacio de memoria en el que operar.

Si el proceso *ServiceHub.RoslynCodeAnalysisService.exe* o *ServiceHub.RoslynCodeAnalysisService32.exe* finalizan por algún motivo, aparece una barra de información emergente con el mensaje siguiente:

**"Unfortunately, a process used by Visual Studio has encountered an unrecoverable error. We recommend saving your work, and then closing and restarting Visual Studio." (Lamentablemente, un proceso usado por Visual Studio ha detectado un error irrecuperable. Le recomendamos que guarde su trabajo y, después, cierre y reinicie Visual Studio).**

Si ve este mensaje, debe guardar el trabajo y, después, cerrar y reiniciar Visual Studio.

## <a name="list-of-processes"></a>Lista de procesos

A continuación encontrará una lista de procesos fuera de proceso usados por Visual Studio. Esta lista incluye los procesos que se ejecutan en escenarios o flujos de trabajo específicos y que, en la mayoría de casos, no se ejecutan todos al mismo tiempo.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- MSBuild.exe
- PerfWatson2.exe
- ScriptedSandbox64.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.RoslynCodeAnalysisService.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.VSDetouredHost.exe
- VBCSCompiler.exe
- VsHub.exe
- vstest.discoveryengine.x86.exe
- WaAppAgent.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe

Si alguno de estos procesos finaliza inesperadamente, alguna funcionalidad de Visual Studio deja de funcionar. En algunos procesos, la pérdida de funcionalidad puede ser insignificante. En otros casos, afecta a la estabilidad de Visual Studio y se muestra un mensaje de error.

> [!NOTE]
> Si experimenta un problema que no se menciona en esta página, infórmenos a través de la herramienta [Notificar un problema](../../ide/how-to-report-a-problem-with-visual-studio.md) que aparece tanto en el Instalador de Visual Studio como en el IDE de Visual Studio.
