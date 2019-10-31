---
title: Busque el proceso ASP.NET en ejecución | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187657"
---
# <a name="find-the-name-of-the-aspnet-process"></a>Buscar el nombre de un proceso de ASP.NET

Para depurar una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] en ejecución, el depurador de Visual Studio debe asociarse al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proceso por nombre.

**Para averiguar qué proceso está ejecutando una aplicación de ASP.NET:**

1. Con la aplicación en ejecución, en Visual Studio, seleccione **Depurar** > **asociar al proceso**.

1. En el cuadro de diálogo **asociar al proceso** , escriba las primeras letras de los nombres de proceso de la lista siguiente o escríbalos en el cuadro de búsqueda. El que se está ejecutando es el que ejecuta la aplicación ASP.NET. Adjunte a ese proceso para depurar la aplicación.

    - *w3wp. exe* es IIS 6,0 y versiones posteriores.
    - *aspnet_wp. exe* es versiones anteriores de IIS.
    - *iisexpress. exe* es iisexpress.
    - *dotnet. exe* es ASP.net Core.
    - *Inetinfo. exe* es una aplicación ASP más antigua que se ejecuta en proceso.

>[!NOTE]
>Visual Studio 2012 y versiones anteriores [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código pueden estar en el sistema de archivos y ejecutarse en el servidor de prueba *webdev. WebServer. exe* o *webdev. WebServer40. exe*. En este caso, para la depuración local, adjunte a *webdev. WebServer. exe* o *webdev. WebServer40. exe* en lugar del proceso de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

**Vea también:**

- [Adjuntar a un proceso en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Requisitos previos para la depuración remota de aplicaciones Web](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)
- [Depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)