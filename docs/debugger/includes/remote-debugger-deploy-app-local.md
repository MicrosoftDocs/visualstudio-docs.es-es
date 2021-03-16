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
ms.openlocfilehash: b6ceee76d8c24ccddb41e47c0865d96c79e6fc32
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249930"
---
1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y seleccione **Publicar** (para Web Forms, **Publicar aplicación web**).

    Si previamente ha configurado algún perfil de publicación, aparece el panel **Publicar**. Haga clic en **Nuevo perfil**.

1. En el cuadro de diálogo **Publicar**, seleccione **Carpeta**, haga clic en **Examinar** y cree una carpeta, **C:\Publish**.

   ::: moniker range=">=vs-2019"

   :::image type="content" source="../media/vs-2019/remotedbg-publish-local.png" alt-text="Captura de pantalla del cuadro de diálogo Elegir un destino de publicación en Visual Studio con la carpeta &quot;C:\Publish&quot; seleccionada como destino de publicación.":::

   Haga clic en **Finalizar** para guardar el perfil de publicación.
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Captura de pantalla del cuadro de diálogo Elegir un destino de publicación en Visual Studio con la carpeta "bin\Release\Publish" seleccionada como destino de publicación.](../media/remotedbg_publish_local.png)
   En el caso de una aplicación de Web Forms, elija **Personalizado** en el cuadro de diálogo Publicar, escriba un nombre de perfil y elija **Aceptar**.

   Haga clic en **Crear perfil** en la lista desplegable (**Publicar**  es el valor predeterminado).
   ::: moniker-end

1. Cambie a una configuración de depuración.

   ::: moniker range=">=vs-2019"
   Elija **Editar** para editar el perfil y, a continuación, seleccione **Configuración**. Elija una configuración de **depuración** y, después, en **Quitar archivos adicionales en destino** en las **Opciones de publicación de archivos**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   En el cuadro de diálogo **Configuración**, haga clic en **Siguiente** para habilitar la depuración, elija una configuración de **Depuración** y, después, en **Quitar archivos adicionales en destino** en las **Opciones de publicación de archivos**.
   ::: moniker-end

   > [!NOTE]
   > Si usa una compilación de versión, deshabilite la depuración en el archivo *web.config* al realizar la publicación.

1. Haga clic en **Publicar**.

    ![Captura de pantalla de la pestaña Configuración del cuadro de diálogo Publicar. La configuración está establecida en Depurar y el botón Publicar está seleccionado.](../media/remotedbg_publish_debug_config.png)

    La aplicación publica una configuración de **Depurar** del proyecto en la carpeta local. El progreso se muestra en la ventana de salida.

1. Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio a un directorio local configurado para la aplicación de ASP.NET (en este ejemplo, **C:\Publish**) en el equipo de Windows Server. En este tutorial, se supone que la copia se realiza manualmente, pero puede usar otras herramientas como PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    > Si necesita realizar cambios en el código o recompilar, debe volver a publicar y repetir este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos. Si no lo hace, recibirá una advertencia `cannot find or open the PDB file` en Visual Studio al intentar depurar el proceso.

1. En Windows Server, compruebe que puede ejecutar la aplicación correctamente abriendo la aplicación en el explorador.

    Si la aplicación no se ejecuta correctamente, puede que haya una discrepancia entre la versión de ASP.NET instalada en el servidor y el equipo de Visual Studio, o puede que haya un problema con la configuración del sitio web o IIS. Vuelva a comprobar los pasos anteriores.
