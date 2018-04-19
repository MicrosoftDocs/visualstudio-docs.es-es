---
title: Corrección de errores Se necesita autorización de proxy | Microsoft Docs
ms.custom: ''
ms.date: 09/22/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 06cdc1651aa7f45e03d260080da5a623d6258661
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2018
---
# <a name="proxy-authorization-required"></a>Se necesita autorización de proxy

Por lo general, este error se produce cuando los usuarios están conectados a Internet a través de un servidor proxy y este bloquea las llamadas que hace Visual Studio a algunos recursos de red.

## <a name="to-correct-this-error"></a>Para corregir este error

- Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales en el cuadro de diálogo.

- Si el paso anterior no resuelve el problema, puede deberse a que el servidor proxy no pide credenciales para direcciones http://go.microsoft.com, pero sí lo hace para direcciones *.visualStudio.com. Para estos servidores, necesitará incluir en una lista de permitidos la siguiente lista de direcciones URL para desbloquear todos los escenarios de inicio de sesión en Visual Studio:

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoft.com

    - *.live.com

- En caso contrario puede quitar la dirección http://go.microsoft.com de la lista de permitidos para que el cuadro de diálogo de autenticación de proxy aparezca para la dirección http://go.microsoft.com y para los puntos de conexión del servidor cuando se reinicie Visual Studio.

    O

- Si desea usar las credenciales predeterminadas con el proxy, haga lo siguiente:

    1. Busque **devenv.exe.config** (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** o **%Archivos de programa (x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**.

    1. En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        Debe insertar la dirección correcta del proxy de la red en `proxyaddress="<http://<yourproxy:port#>`.

    O

- También puede seguir las instrucciones de [esta publicación](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para agregar código que le permitirá usar el proxy.
