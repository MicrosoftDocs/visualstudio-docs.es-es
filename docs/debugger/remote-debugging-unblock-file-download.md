---
title: Desbloquear la descarga de herramientas remotas
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfc212dff46cea4de494f46a439026c7d5a851bb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905350"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedimiento Desbloquear la descarga de las herramientas remotas en Windows Server

La configuración de seguridad predeterminada en Internet Explorer en Windows Server puede hacer mucho tiempo descargar los componentes, como las herramientas remotas.

* Configuración de seguridad mejorada está habilitada en Internet Explorer, lo que evita tener que abrir los sitios Web y obtener acceso a recursos web, a menos que se permita explícitamente el dominio que contiene el recurso (es decir, de confianza). Si bien puede deshabilitar a esta configuración, no se recomienda, ya que puede presentar un riesgo de seguridad.

* En Windows Server 2016, un valor predeterminado en **opciones de Internet** > **seguridad** > **Internet**  >   **Personalizar nivel** > **descargas** también deshabilita las descargas de archivos. Si elige descargar las herramientas remotas directamente en Windows Server, debe habilitar la descarga de archivos.

Para descargar las herramientas de Windows Server, se recomienda uno de los siguientes:

* Descargue las herramientas remotas en un equipo diferente, como el una ejecución de Visual Studio y, a continuación, copie el *.exe* archivo a Windows Server.

* Ejecutar el depurador remoto [desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon) en el equipo de Visual Studio.

* Descargue las herramientas remotas directamente en Windows Server y acepte las indicaciones para agregar sitios de confianza. Sitios Web modernos suelen incluyen muchos recursos de terceros, por lo que esto puede dar lugar a numerosos mensajes. Además, los vínculos de redirigida deba agregarse manualmente. Puede agregar algunos de los sitios de confianza antes de comenzar la descarga. Vaya a **opciones de Internet > seguridad > sitios de confianza > sitios** y agregue los siguientes sitios.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * acerca de: en blanco

  Las versiones anteriores del depurador en my.visualstudio.com, agregue estos sitios adicionales para asegurarse de que ese inicio de sesión es correcta:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * Login.Live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.STS.Microsoft.com
  * auth.GFX.ms
  * app.vssps.visualstudio.com
  * vlscppe.Microsoft.com
  * Query.prod.cms.RT.Microsoft.com

    Si elige agregar estos dominios al descargar las herramientas remotas y luego elija **agregar** cuando se le solicite.

    ![Cuadro de diálogo de contenido bloqueado](../debugger/media/remotedbg-blocked-content.png)

    Al descargar el software, obtendrá algunas solicitudes adicionales para conceder permiso para cargar varios scripts de sitios web y recursos. En my.visualstudio.com, le recomendamos que agregue los dominios adicionales para asegurarse de que ese inicio de sesión es correcta.