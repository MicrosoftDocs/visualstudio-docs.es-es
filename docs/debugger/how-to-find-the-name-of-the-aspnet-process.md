---
title: Búsqueda del proceso ASP.NET en ejecución | Microsoft Docs
description: Aprenda a depurar una aplicación de ASP.NET en ejecución. Puede adjuntar el depurador de Visual Studio al proceso de ASP.NET por nombre.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 11526639975924fd9984dce33a08e54c9a5405b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877660"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Búsqueda del el nombre de un proceso de ASP.NET

Para depurar una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en ejecución, el depurador de Visual Studio debe adjuntarse al proceso [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] por nombre.

**Para averiguar qué proceso está ejecutando una aplicación de ASP.NET, siga estos pasos:**

1. En Visual Studio, con la aplicación en ejecución, seleccione **Depurar** > **Adjuntar al proceso**.

1. En el cuadro de diálogo **Adjuntar al proceso**, escriba las primeras letras de los nombres de proceso de la lista siguiente o escríbalos en el cuadro de búsqueda. El que se está ejecutando es el que ejecuta la aplicación de ASP.NET. Adjúntela a ese proceso para depurar la aplicación.

    - *w3wp.exe* pertenece a IIS 6.0 y versiones posteriores.
    - *aspnet_wp.exe* pertenece a versiones anteriores de IIS.
    - *iisexpress.exe* pertenece a IISExpress.
    - *dotnet.exe* pertenece a ASP.NET Core.
    - *inetinfo.exe* pertenece a aplicaciones de ASP anteriores que se ejecutan en el mismo proceso.

>[!NOTE]
>Visual Studio 2012 y las versiones anteriores de código [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] pueden estar en el sistema de archivos y ejecutarse en el servidor de prueba *WebDev.WebServer.exe* o *WebDev.WebServer40.exe*. En este caso, para la depuración local, se debe adjuntar a *WebDev.WebServer.exe* o a *WebDev.WebServer40.exe*, no al proceso [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Vea también:**

- [Adjuntar a un proceso en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Requisitos previos para la depuración remota de aplicaciones web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)