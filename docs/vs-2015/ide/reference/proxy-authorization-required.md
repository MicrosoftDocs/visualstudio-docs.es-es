---
title: Se necesita autorización de proxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7456e60b42b18ad706b951ee58ca5c33f05cabc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665713"
---
# <a name="proxy-authorization-required"></a>Se necesita autorización de proxy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Normalmente, el error de **autorización de proxy** se produce cuando los usuarios están conectados a recursos de Visual Studio online a través de un servidor proxy y el servidor proxy bloquea las llamadas.

Para corregir este error, pruebe uno o varios de los pasos siguientes:

- Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales en el cuadro de diálogo.

- Si el paso anterior no resuelve el problema, puede que el servidor proxy no pida credenciales para direcciones http://go.microsoft.com, pero que sí lo haga para direcciones *.visualStudio.com. Para estos servidores, debe agregar las siguientes direcciones URL a la lista de permitidos para desbloquear todos los escenarios de inicio de sesión en Visual Studio:

  - *.windows.net

  - *.microsoftonline.com

  - *.visualstudio.com

  - *.microsoft.com

  - *.live.com

- Puede quitar la dirección http://go.microsoft.com de la lista de permitidos para que se muestre el cuadro de diálogo de autenticación de proxy para la dirección http://go.microsoft.com y los puntos de conexión del servidor cuando se reinicie Visual Studio.

- Si desea usar las credenciales predeterminadas con el proxy, haga lo siguiente:

   1. Busque devenv.exe.config (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio 14.0\Common7\IDE** (o en **%Archivos de programa (x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Inserte la dirección de proxy correcta para la red en `proxyaddress="<http://<yourproxy:port#>`.

- Siga las instrucciones de [esta entrada de blog](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para agregar código que le permita usar el proxy.
