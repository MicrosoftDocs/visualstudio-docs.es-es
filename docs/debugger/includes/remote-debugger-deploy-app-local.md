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
ms.openlocfilehash: a55b2a12c9a45c5a3952e3e6f4e1627bec8ba520
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
1. En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **publicar** (para los formularios Web Forms, **Publicar Web App**).

2. En el **publicar** cuadro de diálogo, seleccione **carpeta**, haga clic en **examinar**y cree una nueva carpeta, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Para una aplicación de formularios Web Forms, elija **personalizado** en el cuadro de diálogo Publicar, escriba un nombre de perfil y elija **Aceptar**.

3. Haga clic en **Publicar**.

    Visual Studio publica el proyecto en la carpeta. El progreso se muestra en la ventana de salida.

4. En el **publicar** cuadro de diálogo, haga clic en el **configuración** vincular y, a continuación, seleccione la **configuración** ficha.

5. Establezca la configuración en **depurar**, seleccione **eliminar todos los archivos existentes antes de publicar**y, a continuación, haga clic en **guardar**.

    > [!NOTE]
    > Si usa una versión de lanzamiento, deshabilita la depuración en el archivo web.config al publicar.

6. Haga clic en **Publicar**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    La aplicación se publica un **depurar** configuración del proyecto en la carpeta local.

5. Copie el directorio del proyecto ASP.NET desde el equipo de Visual Studio en el directorio local configurado para la aplicación ASP.NET (en este ejemplo, **C:\Publish**) en el equipo de Windows Server. En este tutorial, se supone que va a copiar manualmente, pero también puede usar otras herramientas como PowerShell, Xcopy o Robocopy.

    > [!CAUTION]
    >  Si necesita realizar cambios en el código o volver a generar, debe volver a publicar y repita este paso. El archivo ejecutable que copió en el equipo remoto debe coincidir exactamente con el origen local y los símbolos.

6. En el servidor de Windows, compruebe que puede ejecutar correctamente la aplicación, abra la aplicación en el explorador.

    Si la aplicación no se ejecuta correctamente, puede haber una discrepancia entre la versión de ASP.NET instaladas en el servidor y el equipo de Visual Studio, o que tenga un problema con la configuración de IIS o el sitio Web. Volver a comprobar los pasos anteriores.