---
title: Implementar mediante Web Deploy
description: Implementar una aplicación con Web Deploy en Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794214"
---
Si ha instalado Web Deploy mediante el instalador de plataforma Web, puede implementar la aplicación directamente desde Visual Studio.

1. Inicie Visual Studio con privilegios de administrador y vuelva a abrir el proyecto.

    Se requieren privilegios de administrador para implementar la aplicación con Web Deploy.

1. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Publicar**.

    Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **nuevo perfil**.

1. Para **seleccionar un destino de publicación**, seleccione **IIS, FTP, etc.** y haga clic en **publicar**.

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Especifique los parámetros de configuración de corrección para el programa de instalación IIS.

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si no resuelve un nombre de host al intentar validar en los siguientes pasos el **Server** texto cuadro, pruebe la dirección IP. Incluir `http://` como prefijo en el **Server** campo.  Asegúrese de que utiliza el puerto 80 en el **Server** texto cuadro y asegúrese de que el puerto 80 y el puerto 8172 están abiertos en el firewall.

1. Elija **validar**. Si se valida la configuración de la conexión, puede intentar publicar.

1. Haga clic en **publicar** para publicar la aplicación.

    La ficha salida indica si la publicación sea correcta y que el explorador, a continuación, abre la aplicación.

    Si se produce un error que haga mención Web Deploy, vuelva a comprobar los pasos de instalación de Web Deploy y asegúrese de que estén abiertos los puertos correctos (Web Deploy también requiere el puerto 8172 esté abierto en el servidor).

    Si la aplicación se implementa correctamente, pero no se ejecuta correctamente, puede haber un problema con la configuración de IIS, la instalación de ASP.NET o la configuración del sitio Web. En el servidor de Windows, abra el sitio Web de IIS para los mensajes de error más específicos y, a continuación, volver a comprobar los pasos anteriores.
