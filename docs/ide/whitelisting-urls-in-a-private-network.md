---
title: "Inclusión en lista blanca de direcciones URL en una red privada | Microsoft Docs"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bc7db7b6a1d3e1d39b5fb3b128c28da37a9538b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="whitelisting-urls-in-a-private-network"></a>Inclusión en lista blanca de direcciones URL en una red privada    
Si usa Visual Studio en una red privada en la que se utiliza un dispositivo de seguridad (por ejemplo, un firewall), es posible que Visual Studio no pueda conectarse a algunos recursos de red. Entre estos recursos se incluyen Visual Studio Team Services (VSTS) para el inicio de sesión y la concesión de licencias, NuGet y los servicios de Azure. Si se produce un error en Visual Studio al conectarse a uno de estos recursos, verá el mensaje de error siguiente:  

  **Se ha terminado la conexión: An unexpected error occurred on send** (Se ha producido un error inesperado en el envío)  

Visual Studio usa el protocolo de Seguridad de la capa de transporte (TLS) 1.2 para conectarse a recursos de red. Los dispositivos de seguridad de algunas redes privadas bloquean ciertas conexiones de servidor cuando Visual Studio usa TLS 1.2. Para corregir el error, habilite las conexiones para las direcciones URL siguientes:

- https://management.core.windows.net  

- https://app.vssps.visualstudio.com  

- https://login.microsoftonline.com  

- https://login.live.com  

- https://go.microsoft.com  

- https://graph.windows.net  

- https://app.vsspsext.visualstudio.com  

- *.azurewebsites.net (para las conexiones de Azure)  

- *.nuget.org (para las conexiones de NuGet)  

- *.visualstudio.com  

- cdn.vsassets.io (hospeda contenido de la red de entrega de contenido, o red CDN)  

- *.gallerycdn.vsassets.io (hospeda extensiones de VSTS)  

- static2.sharepointonline.com (hospeda los recursos que Visual Studio usa en el kit de interfaz de usuario de tejido de Office, como las fuentes)

> [!NOTE]
>  Es posible que las direcciones URL de servidores NuGet privados no se incluyan en la lista anterior. Puede comprobar los servidores NuGet que usa si abre %APPData%\Nuget\NuGet.Config.  

## <a name="see-also"></a>Vea también  
[Se necesita autorización del Proxy (error)](../ide/reference/proxy-authorization-required.md)  
[Entorno conectado](../ide/connected-environment.md)  
[Instalar Visual Studio detrás de un firewall o servidor proxy](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)  
