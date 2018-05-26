---
title: Implementar en la carpeta local
description: Implementar una aplicación en una carpeta local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
1. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **publicar** (para los formularios Web Forms, **Publicar Web App**).

    Si previamente ha configurado ningún perfil de publicación, la **publicar** aparece el panel. Haga clic en **nuevo perfil**.

1. En el **publicar** cuadro de diálogo, seleccione **carpeta**, haga clic en **examinar**y cree una nueva carpeta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Para una aplicación de formularios Web Forms, elija **personalizado** en el cuadro de diálogo Publicar, escriba un nombre de perfil y elija **Aceptar**.

1. Haga clic en **Crear perfil** en la lista desplegable (**publicar** es el valor predeterminado).

1. En el **publicar** cuadro de diálogo, haga clic en el **configuración** vincular y, a continuación, seleccione la **configuración** ficha.

1. Establezca la configuración en **depurar**, seleccione **eliminar todos los archivos existentes antes de publicar**y, a continuación, haga clic en **guardar**.

    > [!NOTE]
    > Si usa una versión de lanzamiento, deshabilita la depuración en el archivo web.config al publicar.

1. Haga clic en **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    La aplicación se publica un **depurar** configuración del proyecto en la carpeta local. El progreso se muestra en la ventana de salida.

1. Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio en el directorio local configurado para la aplicación ASP.NET (en este ejemplo, **C:\Publish**) en el equipo de Windows Server. En este tutorial, se supone que va a copiar manualmente, pero también puede usar otras herramientas como PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    >  Si necesita realizar cambios en el código o volver a generar, debe volver a publicar y repita este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.    Si no lo hace así, recibirá un `cannot find or open the PDB file` advertencia en Visual Studio cuando se intenta depurar el proceso.

1. En el servidor de Windows, compruebe que puede ejecutar correctamente la aplicación, abra la aplicación en el explorador.

    Si la aplicación no se ejecuta correctamente, puede haber una discrepancia entre la versión de ASP.NET instaladas en el servidor y el equipo de Visual Studio, o que tenga un problema con la configuración de IIS o el sitio Web. Volver a comprobar los pasos anteriores.
