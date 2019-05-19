---
title: Se necesita autorización de proxy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 520c31f671aee05663a5471aca05cfe06313b168
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65847032"
---
# <a name="proxy-authorization-required"></a>Se necesita autorización de proxy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El **necesita autorización de Proxy** error suele producirse cuando los usuarios se conectan a recursos en línea de Visual Studio a través de un servidor proxy y el servidor proxy bloquea las llamadas.

Para corregir este error, pruebe uno o varios de los pasos siguientes:

- Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales en el cuadro de diálogo.

- Si el paso anterior no resuelve el problema, puede que el servidor proxy no pida credenciales para direcciones http://go.microsoft.com, pero que sí lo haga para direcciones *.visualStudio.com. Estos servidores, es preciso agregar las siguientes direcciones URL a la lista de permitidos para desbloquear todos los escenarios de inicio de sesión en Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- Puede quitar el http://go.microsoft.com de direcciones de la lista de permitidos para que el cuadro de diálogo de autenticación de proxy aparezca para ambas la http://go.microsoft.com dirección y los puntos de conexión de servidor cuando se reinicie Visual Studio.

- Si desea usar las credenciales predeterminadas con el proxy, realice lo siguiente:

   1. Busque devenv.exe.config (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio 14.0\Common7\IDE** (o en **%Archivos de programa (x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).

   2. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

      ```xml
      <defaultProxy enabled="true" useDefaultCredentials="true">
          <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
      </defaultProxy>
      ```

      Insertar la dirección de proxy correcta para la red en `proxyaddress="<http://<yourproxy:port#>`.

- Siga las instrucciones de [esta entrada de blog](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para agregar código que le permite usar el proxy.
