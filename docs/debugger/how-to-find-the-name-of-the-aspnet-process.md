---
title: 'Cómo: buscar el nombre del proceso de ASP.NET | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 899860baf5461eb798341cebf775ccde488915b7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Cómo: Buscar el nombre de un proceso de ASP.NET
Para establecer una asociación a una aplicación [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] que se está ejecutando, es preciso conocer el nombre del proceso [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  

-   Si está ejecutando ASP.NET Core en IIS o en IISExpress, el nombre del proceso es dotnet.exe.

-   Si está ejecutando ASP.NET en IIS 6.0 más adelante, el nombre es w3wp.exe.  
  
-   Si está ejecutando ASP.NET en una versión anterior de IIS, el nombre es aspnet_wp.exe.

-   Si está ejecutando ASP.NET en IISExpress, el nombre es iisexpress.exe.
  
Para las aplicaciones compiladas con versiones de Visual Studio anteriores a Visual Studio 2012, la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código puede residir en el sistema de archivos y ejecutarse en el servidor de pruebas WebDev.WebServer.exe o WebDev.WebServer40.exe. En ese caso, debe adjuntar a WebDev.WebServer.exe o WebDev.WebServer40.exe en lugar de la [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proceso. Este escenario sólo se aplica a la depuración local.
  
Las aplicaciones ASP anteriores se ejecutan dentro del proceso de IIS inetinfo.exe cuando se ejecutan en proceso.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Para determinar la versión de IIS en la que se está ejecutando la aplicación  

1.  Asegúrese de que se ejecuta la aplicación y, a continuación, desde Visual Studio, use la [adjuntar al proceso](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) comando.

2.  Escriba la primera letra de un nombre de proceso como w3wp.exe para encontrar rápidamente los procesos en el **procesos disponibles** lista.

    Los procesos disponibles en la lista en este tema indican qué versiones de IIS están disponibles y qué proceso está ejecutando la aplicación.

    > [!NOTE]
    > A partir de 2017 de Visual Studio, puede usar el cuadro de búsqueda para buscar el nombre del proceso.
  
## <a name="see-also"></a>Vea también  
 [Adjuntar a un proceso en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Requisitos previos para la depuración de aplicaciones Web remota](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Depurar aplicaciones ASP.](../debugger/how-to-enable-debugging-for-aspnet-applications.md)