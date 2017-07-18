---
title: "Se necesita autorización de proxy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 537928b9ce99cbda9873500780719353d34fcbe1
ms.contentlocale: es-es
ms.lasthandoff: 07/14/2017

---
# <a name="proxy-authorization-required"></a>Se necesita autorización de proxy
Por lo general, este error se produce cuando los usuarios están conectados a Visual Studio Online a través de un servidor proxy y el servidor proxy bloquea las llamadas. Visual Studio Online se usa para mantener la sesión del usuario iniciada en el IDE.  
  
## <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Reinicie Visual Studio. Debe aparecer un cuadro de diálogo de autenticación de proxy. Escriba sus credenciales en el cuadro de diálogo.  
  
-   Si el paso anterior no resuelve el problema, puede deberse a que el servidor proxy no pide credenciales para direcciones http://go.microsoft.com, pero sí lo hace para direcciones *.visualStudio.com. Para estos servidores, necesitará incluir en una lista blanca la siguiente lista para desbloquear todos los escenarios de inicio de sesión en Visual Studio:  
  
    -   *.windows.net  
  
    -   *.microsoftonline.com  
  
    -   *.visualstudio.com  
  
    -   *.microsoft.com  
  
    -   *.live.com  
  
-   En caso contrario puede quitar la dirección http://go.microsoft.com de la lista blanca para que el cuadro de diálogo de autenticación de proxy aparezca para la dirección http://go.microsoft.com y para los puntos de conexión del servidor cuando se reinicie Visual Studio.  
  
-   O  
  
-   Si desea usar las credenciales predeterminadas con el proxy, haga lo siguiente:  
  
    1.  Busque devenv.exe.config (el archivo de configuración de devenv.exe) en: **%Archivos de programa%\Microsoft Visual Studio 14.0\Common7\IDE** (o en **%Archivos de programa (x86)%\Microsoft Visual Studio 14.0\Common7\IDE**).  
  
    2.  En el archivo de configuración, busque el bloque `<system.net>` y agregue este código:  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         Debe insertar la dirección correcta del proxy de la red en `proxyaddress="<http://<yourproxy:port#>`.  
  
-   O  
  
-   También puede seguir las instrucciones de [esta publicación](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) para agregar código que le permitirá usar el proxy.
