---
title: Recopilar datos de seguimiento de eventos para Windows (ETW) | Microsoft Docs
description: Obtenga información sobre cómo usar Seguimiento de eventos para Windows (ETW) para determinar dónde se producen problemas de rendimiento en la aplicación. Los datos se consultan con VSPerfReport.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 853e27c51b626ef63a7e0924d4c0164a6386cda2
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801553"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Procedimiento Recopilar datos de seguimiento de eventos para Windows (ETW)

Seguimiento de eventos para Windows (ETW) es una eficaz utilidad de seguimiento de nivel de kernel que activa el kernel de registro del generador de perfiles o eventos definidos por la aplicación. Los datos recopilados del proveedor de eventos se pueden ver utilizando la opción /**Summary: ETW** de la herramienta de línea de comandos [VSPerfReport](../profiling/vsperfreport.md). Utilice este informe para determinar dónde se producen problemas de rendimiento en la aplicación.

> [!NOTE]
> Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Para habilitar proveedores de seguimiento de eventos

1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.

2. En **Páginas de propiedades**, haga clic en las propiedades de **Eventos de Windows**.

3. En la lista **Seleccionar proveedor de seguimiento de eventos del que recopilar datos**, seleccione los proveedores de eventos que desea utilizar para generar perfiles de la aplicación.

## <a name="see-also"></a>Vea también

[Configuración de sesiones de rendimiento](../profiling/configuring-performance-sessions.md)
