---
title: Procedimiento Ejecutar el proceso de trabajo en una cuenta de usuario | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- user accounts, aspnet_wp.exe
- ASP.NET, debugging Web applications
- tools, aspnet_wp.exe
- ASP.NET, tools
- aspnet_wp.exe
ms.assetid: b58e97b1-e62a-4318-aea4-52276ea20735
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ebb8ec1fe10f6fbc5c367cb0ed127e048351b0e4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157867"
---
# <a name="how-to-run-the-worker-process-under-a-user-account"></a>Procedimiento Ejecutar un proceso de trabajo en una cuenta de usuario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para configurar el equipo de forma que pueda ejecutar el proceso de trabajo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] (aspnet_wp.exe o w3wp.exe) bajo una cuenta de usuario, siga estos pasos.  
  
## <a name="procedure"></a>Procedimiento  
  
#### <a name="to-run-aspnetwpexe-under-a-user-account"></a>Para ejecutar aspnet_wp.exe en una cuenta de usuario  
  
1. Abra el archivo machine.config, ubicado en el equipo en la carpeta CONFIG, en la ruta de acceso en la que instaló el motor en tiempo de ejecución.  
  
2. Busque la sección &lt;processModel&gt; y cambie los atributos "user" y "password" por el nombre y la contraseña de la cuenta de usuario con la que quiera que se ejecute aspnet_wp.exe.  
  
3. Guarde el archivo machine.config.  
  
4. En [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], IIS 6.0 está instalado de manera predeterminada. El proceso de trabajo correspondiente es w3wp.exe. Para que se ejecute en el modo de IIS 6.0 con aspnet_wp.exe como proceso de trabajo, debe seguir estos pasos:  
  
    1. Haga clic en **Inicio**, haga clic en **Herramientas administrativas** y, a continuación, elija **Internet Information Services**.  
  
    2. En el cuadro de diálogo **Internet Information Services** , haga clic con el botón secundario del mouse en la carpeta **Sitios Web** y elija **Propiedades**.  
  
    3. En el cuadro de diálogo **Propiedades de sitios Web** , elija **Servicio**.  
  
    4. Seleccione **Ejecutar el servicio WWW en el Modo aislado de IIS 6.0**.  
  
    5. Cierre el cuadro de diálogo **Propiedades** y el **Administrador de servicios Internet**.  
  
5. Abra un símbolo de comandos de Windows y restablezca el servidor ejecutando:  
  
    ```  
    iisreset  
    ```  

    o  
  
    ```  
    net stop iisadmin /y  
    net start w3svc  
    ```  
  
6. Busque la carpeta de archivos temporales de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , que debe estar ubicada en la misma ruta de acceso que la carpeta CONFIG. Haga clic con el botón secundario en la carpeta de archivos [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] temporales y elija **Propiedades** en el menú contextual.  
  
7. En el cuadro de diálogo **Propiedades de los archivos ASP.NET temporales** , haga clic en la ficha **Seguridad** .  
  
8. Haga clic en **Avanzado**.  
  
9. En el cuadro de diálogo **Configuración de seguridad avanzada para archivos temporales de ASP.NET** , haga clic en **Agregar**.  
  
    Aparecerá el cuadro de diálogo **Seleccionar usuarios, equipos o grupos** .  
  
10. Escriba el nombre del usuario en el cuadro **Escriba el nombre de objeto a seleccionar** y, a continuación, haga clic en **Aceptar**. El nombre de usuario debe seguir este formato: Nombredominio\nombreusuario.  
  
11. En el cuadro de diálogo **Entrada de permiso para archivos temporales de ASP.NET** , dé al usuario **Control total**y, a continuación, haga clic en **Aceptar** para cerrar el cuadro de diálogo **Entrada de permiso para archivos temporales de ASP.NET** .  
  
12. Aparecerá el cuadro de diálogo **Seguridad** , y le preguntará si realmente desea cambiar los permisos en una carpeta del sistema. Haga clic en **Sí**.  
  
13. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Propiedades de los archivos ASP.NET temporales** .  
  
## <a name="see-also"></a>Vea también  
[Depuración ASP.NET: Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md)  
