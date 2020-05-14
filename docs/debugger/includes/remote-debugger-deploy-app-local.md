---
title: Implementar en una carpeta local
description: Implementación de una aplicación en una carpeta local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 3fa0569739ee81ec4b2aa0eec8157068ffc949cd
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149222"
---
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Publicar** (para Web Forms, **Publicar aplicación web**).

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Nuevo perfil**.

1. En el cuadro de diálogo **Publicar**, seleccione **Carpeta**, haga clic en **Examinar** y cree una carpeta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    En el caso de una aplicación de Web Forms, elija **Personalizado** en el cuadro de diálogo Publicar, escriba un nombre de perfil y elija **Aceptar**.

1. Haga clic en **Crear perfil** en la lista desplegable (**Publicar**  es el valor predeterminado).

1. En el cuadro de diálogo **Publicar**, haga clic en el vínculo **Configuración** y, después, seleccione la pestaña **Configuración**.

1. Establezca la configuración en **Depurar**, seleccione **Eliminar todos los archivos existentes antes de publicar** y, después, haga clic en **Guardar**.

    > [!NOTE]
    > Si usa una compilación de versión, deshabilite la depuración en el archivo web.config al realizar la publicación.

1. Haga clic en **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")

    La aplicación publica una configuración de **Depurar** del proyecto en la carpeta local. El progreso se muestra en la ventana de salida.

1. Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio a un directorio local configurado para la aplicación de ASP.NET (en este ejemplo, **C:\Publish**) en el equipo de Windows Server. En este tutorial, se supone que la copia se realiza manualmente, pero puede usar otras herramientas como PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    > Si necesita realizar cambios en el código o recompilar, debe volver a publicar y repetir este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.    Si no lo hace, recibirá una advertencia `cannot find or open the PDB file` en Visual Studio al intentar depurar el proceso.

1. En Windows Server, compruebe que puede ejecutar la aplicación correctamente abriendo la aplicación en el explorador.

    Si la aplicación no se ejecuta correctamente, puede que haya una discrepancia entre la versión de ASP.NET instalada en el servidor y el equipo de Visual Studio, o puede que haya un problema con la configuración del sitio web o IIS. Vuelva a comprobar los pasos anteriores.
