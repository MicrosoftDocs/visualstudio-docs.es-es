---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
Si ha instalado Web Deploy mediante el instalador de plataforma Web, puede implementar la aplicación directamente desde Visual Studio.

1. Inicie Visual Studio con privilegios de administrador y vuelva a abrir el proyecto.

    Se requieren privilegios de administrador para implementar la aplicación con Web Deploy.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Publicar**.

3. Para **seleccionar un destino de publicación**, seleccione **IIS, FTP, etc.** y haga clic en **publicar**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. Especifique los parámetros de configuración de corrección para el programa de instalación IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si no resuelve un nombre de host al intentar validar en los siguientes pasos el **Server** texto cuadro, pruebe la dirección IP. Incluir `http://` como prefijo en el **Server** campo.  Asegúrese de que utiliza el puerto 80 en el **Server** texto cuadro y asegúrese de que el puerto 80 está abierto en el firewall.

6. Haga clic en **siguiente**, elija un **depurar** configuración y elija **quitar archivos adicionales en destino** en el **publicar archivos** Opciones.

    > [!NOTE]
    > Si elige una configuración de lanzamiento, deshabilita la depuración en el archivo web.config al publicar.

5. Haga clic en **Prev**y, a continuación, elija **validar**. Si se valida la configuración de la conexión, puede intentar publicar.

6. Haga clic en **publicar** para publicar la aplicación.

    La ficha salida indica si la publicación sea correcta y que el explorador, a continuación, abre la aplicación.

    Si se produce un error que haga mención Web Deploy, vuelva a comprobar los pasos de instalación de Web Deploy y asegúrese de que estén abiertos los puertos correctos (Web Deploy también requiere el puerto 8172 esté abierto en el servidor).

    Si la aplicación se implementa correctamente, pero no se ejecuta correctamente, puede haber un problema con la configuración de IIS, la instalación de ASP.NET o la configuración del sitio Web. En el servidor de Windows, abra el sitio Web de IIS para los mensajes de error más específicos y, a continuación, volver a comprobar los pasos anteriores.