---
title: 'Error: Depuración produjo un error porque no está habilitada la autenticación integrada de Windows | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b922e8e8fde8b185207810d107afb9a9c5a6e05
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757259"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Error: La depuración produjo un error porque no está habilitada la autenticación de Windows integrada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La autenticación del usuario que solicita la depuración no pudo realizarse debido a un error de autenticación. Esto problema puede producirse cuando intenta desplazarse a un aplicación web o a un servicio Web XML. Una causa de este error es que la autenticación de Windows integrada no esté habilitada. Para habilitarla, siga los pasos descritos en "Para habilitar la autenticación de Windows integrada".  
  
 Si ha habilitado la autenticación integrada de Windows y sigue apareciendo este error, es posible que este error se produce porque **autenticación implícita para Windows dominio servidores** está habilitado. En este caso debe ponerse en contacto con su administrador de red.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Para habilitar la autenticación de Windows integrada  
  
1.  Inicie sesión en el servidor web con una cuenta de administrador.  
  
2.  Haga clic en **iniciar** y, a continuación, haga clic en **Panel de Control**.  
  
3.  En **Panel de Control**, haga doble clic en **herramientas administrativas**.  
  
4.  Haga doble clic en **Internet Information Services**.  
  
5.  Haga clic en el nodo del servidor web.  
  
     Un **sitios Web** se abre una carpeta bajo el nombre del servidor.  
  
6.  Puede configurar la autenticación para todos los sitios Web o para sitios Web individuales. Para configurar la autenticación para todos los sitios Web, haga clic en el **sitios Web** carpeta y, a continuación, haga clic en **propiedades**. Para configurar la autenticación de un sitio Web, abra el **sitios Web** carpeta, haga clic en el sitio Web individual y, a continuación, haga clic en **propiedades**.  
  
     El **propiedades** se muestra el cuadro de diálogo.  
  
7.  Haga clic en el **seguridad de directorios** ficha.  
  
8.  En el **control de acceso y la autenticación anónima** sección, haga clic en **editar**.  
  
     El **métodos de autenticación** se muestra el cuadro de diálogo.  
  
9. En **acceso autenticado**, seleccione **autenticación de Windows integrada**.  
  
10. Haga clic en **Aceptar** para cerrar el **métodos de autenticación** cuadro de diálogo.  
  
11. Haga clic en **Aceptar** para cerrar el **propiedades** cuadro de diálogo.  
  
12. Cerrar la **Internet Information Services** ventana.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Para habilitar la autenticación de Windows integrada en Windows Vista/IIS 7  
  
1.  Inicie sesión en el servidor web con una cuenta de administrador.  
  
2.  Active Autenticación de Windows y Compatibilidad con la administración de II6 si no lo hizo previamente; para ello, siga estos pasos:  
  
    1.  Haga clic en **iniciar**, haga clic en **Panel de Control** y, a continuación, haga clic en **programas**.  
  
    2.  En **programas y características**, haga clic en **o desactivar las características de Windows Active**.  
  
         Aparecerá el cuadro de diálogo Control de cuentas de usuario y se le pedirá permiso para continuar.  
  
    3.  Haga clic en **Continuar**.  
  
         Aparecerá el cuadro de diálogo Características de Windows.  
  
    4.  En la lista de características, expanda el **Internet Information Services** nodo.  
  
    5.  En **Internet Information Services**, expanda el **servicios World Wide Web** nodo.  
  
    6.  En **servicios World Wide Web**, haga clic en **seguridad**.  
  
    7.  Haga clic en **Windows autenticación**.  
  
    8.  En **Internet Information Services**, expanda el **herramientas de administración Web** nodo.  
  
    9. En **herramientas de administración Web**, expanda el **compatibilidad con la administración de IIS 6** nodo y seleccione el **la Metabase de IIS 6 y compatibilidad con la configuración de IIS 6** casilla de verificación.  
  
    10. En **herramientas de administración Web**, seleccione **consola de administración IIS** y haga clic en **Aceptar.**  
  
    11. Reinicie el equipo para que surtan efecto los cambios.  
  
3.  Haga clic en **iniciar** y, a continuación, haga clic en **Panel de Control**.  
  
4.  Haga clic en **vista clásica**y, a continuación, haga doble clic en **herramientas administrativas**.  
  
5.  En el **nombre** columna y haga doble clic en **Internet Information Services (IIS) Manager**.  
  
6.  En el **conexiones** columna, expanda el nodo para el servidor.  
  
     Un **sitios Web** se abre una carpeta bajo el nombre del servidor.  
  
7.  Expanda el **sitios Web** nodo y haga clic en el sitio Web para el que desea habilitar la autenticación integrada de Windows.  
  
8.  El nombre del panel central es reemplazado por el nombre del sitio web seleccionado. En este panel, bajo el **IIS** encabezado, haga doble clic en **autenticación**.  
  
     El título del panel cambia a **autenticación**.  
  
9. En el **autenticación** panel, en el **nombre** columna, haga clic en **Windows autenticación** y, a continuación, haga clic en **habilitar**.  
  
10. Cerrar la **Internet Information Services (IIS) Manager** ventana.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones Web: Errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Autenticación implícita de Microsoft](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Ejecutar aplicaciones Web en Windows Vista con IIS 7.0 y Visual Studio](http://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)



