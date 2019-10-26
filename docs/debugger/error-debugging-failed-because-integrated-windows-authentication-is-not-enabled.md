---
title: 'Error: no se pudo realizar la depuración porque la autenticación integrada de Windows no está habilitada | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c508951a3b54a7f84f142c5029b5305c8ef579ea
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911548"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Error: La depuración produjo un error porque no está habilitada la autenticación de Windows integrada
La autenticación del usuario que solicita la depuración no pudo realizarse debido a un error de autenticación. Esto problema puede producirse cuando intenta desplazarse a un aplicación web o a un servicio Web XML. Una causa de este error es que la autenticación de Windows integrada no esté habilitada. Para habilitarla, siga los pasos descritos en "Para habilitar la autenticación de Windows integrada".

 Si la autenticación de Windows integrada está habilitada y sigue apareciendo este error, entonces es posible que este causado porque la opción **Autenticación implícita para servidores de dominio Windows** esté deshabilitada. En este caso debe ponerse en contacto con su administrador de red.

### <a name="to-enable-integrated-windows-authentication"></a>Para habilitar la autenticación de Windows integrada

1. Inicie sesión en el servidor web con una cuenta de administrador.

2. Haga clic en **Inicio** y después en **Panel de control**.

3. En el **Panel de control**, haga doble clic en **Herramientas administrativas**.

4. Haga doble clic en **Internet Information Services**.

5. Haga clic en el nodo del servidor web.

     Se abre una carpeta **Sitios Web** bajo el nombre del servidor.

6. Puede configurar la autenticación para todos los sitios Web o para sitios Web individuales. Para configurar la autenticación de todos los sitios web, haga clic con el botón derecho del mouse en la carpeta **Sitios web** y elija **Propiedades** en el menú de acceso directo. Para configurar la autenticación de un sitio web en particular, abra la carpeta **Sitios web**, haga clic con el botón derecho del mouse en el sitio web que desee y, a continuación, elija **Propiedades**.

     Aparecerá el cuadro de diálogo **Propiedades**.

7. Haga clic en la ficha **Seguridad de directorios**.

8. En la sección **Acceso anónimo y control de autenticación**, haga clic en **Editar**.

     Aparecerá el cuadro de diálogo **Métodos de autenticación**.

9. En **Acceso autenticado**, seleccione **Autenticación de Windows integrada**.

10. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Métodos de autenticación**.

11. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Propiedades**.

12. Cierre la ventana **Internet Information Services**.

### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Para habilitar la autenticación de Windows integrada en Windows Vista/IIS 7

1. Inicie sesión en el servidor web con una cuenta de administrador.

2. Active Autenticación de Windows y Compatibilidad con la administración de II6 si no lo hizo previamente; para ello, siga estos pasos:

    1. Haga clic en **Inicio**y en **Panel de control** ; a continuación, haga clic en **programas**.

    2. En **Programas y características**, haga clic en **Activar o desactivar las características de Windows**.

         Aparecerá el cuadro de diálogo Control de cuentas de usuario y se le pedirá permiso para continuar.

    3. Haga clic en **Continuar**.

         Aparecerá el cuadro de diálogo Características de Windows.

    4. En la lista de características, expanda el nodo **Internet Information Services**.

    5. En **Internet Information Services**, expanda el nodo **Servicios World Wide Web**.

    6. En **Servicios World Wide Web**, haga clic en **Seguridad**.

    7. Haga clic en **Autenticación de Windows**.

    8. En **Internet Information Services**, expanda el nodo **Herramientas de administración web**.

    9. En **Herramientas de administración web**, expanda el nodo **Compatibilidad con la administración de IIS 6** y después active la casilla **Compatibilidad con la configuración de IIS 6 y metabase de IIS 6**.

    10. En **Herramientas de administración web**, seleccione **Consola de administración de IIS** y haga clic en **Aceptar**.

    11. Reinicie el equipo para que surtan efecto los cambios.

3. Haga clic en **Inicio** y después en **Panel de control**.

4. Haga clic en **Vista clásica** y, a continuación, haga doble clic en **Herramientas administrativas**.

5. En la columna **Nombre**, haga doble clic en **Administrador de Internet Information Services (IIS)** .

6. En la columna **Conexiones**, expanda el nodo del servidor.

     Se abre una carpeta **Sitios Web** bajo el nombre del servidor.

7. Expanda el nodo **Sitios web** y haga clic en el sitio web en el que desea habilitar la autenticación de Windows integrada.

8. El nombre del panel central es reemplazado por el nombre del sitio web seleccionado. En este panel, bajo el encabezado **IIS**, haga doble clic en **Autenticación**.

     El título del panel cambia a **Autenticación**.

9. En el panel **Autenticación**, en la columna **nombre**, haga clic con el botón derecho del mouse en **Autenticación de Windows** y, a continuación, haga clic en **Habilitar**.

10. Cierre la ventana **Administrador de Internet Information Services (IIS)** .

## <a name="see-also"></a>Vea también
- [Depurar aplicaciones web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
- [Autenticación implícita de Microsoft](/windows/win32/secauthn/microsoft-digest-authentication)
- [Ejecutar aplicaciones web en Windows Vista con IIS 7,0 y Visual Studio](https://msdn.microsoft.com/Library/262a82ac-dd0e-4096-86c6-fb463e88be66)