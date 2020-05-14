---
title: Desbloqueo de la descarga de herramientas remotas
ms.date: 07/19/2018
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a243033bf5831952d83fdf688302651e02b76b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62903034"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>Procedimiento Desbloqueo de la descarga de herramientas remotas en Windows Server

La configuración de seguridad predeterminada de Internet Explorer en Windows Server puede hacer que tarden mucho tiempo en descargarse componentes como las herramientas remotas.

* La configuración de seguridad mejorada está habilitada en Internet Explorer, lo que impide abrir sitios web y obtener acceso a recursos web, a menos que el dominio que contiene el recurso se permita explícitamente (es decir, se confíe en él). Aunque puede deshabilitar esta configuración, no se recomienda porque puede suponer un riesgo para la seguridad.

* En Windows Server 2016, una configuración predeterminada en **Opciones de Internet** > **Seguridad** > **Internet** > **Nivel personalizado** > **Descargas** deshabilita también las descargas de archivos. Si decide descargar las herramientas remotas directamente en Windows Server, debe habilitar la descarga de archivos.

Para descargar las herramientas en Windows Server, se recomienda una de las siguientes opciones:

* Descargue las herramientas remotas en otro equipo, como el que ejecuta Visual Studio, y copie el archivo *.exe* en Windows Server.

* Ejecute el depurador remoto [desde un recurso compartido de archivos](../debugger/remote-debugging.md#fileshare_msvsmon) en la máquina de Visual Studio.

* Descargue las herramientas remotas directamente en Windows Server y acepte los avisos para agregar sitios de confianza. Los sitios web modernos suelen incluir muchos recursos de terceros, por lo que esto puede dar lugar a numerosos avisos. Además, es posible que sea necesario agregar manualmente los vínculos redireccionados. Puede optar por agregar algunos de los sitios de confianza antes de comenzar la descarga. Vaya a **Opciones de Internet > Seguridad > Sitios de confianza > Sitios** y agregue los sitios siguientes.

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * about:blank

  En el caso de versiones anteriores del depurador en my.visualstudio.com, agregue estos sitios adicionales para asegurarse de que el inicio de sesión se ha realizado correctamente:

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline-p.com
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    Si decide agregar estos dominios mientras descarga las herramientas remotas, elija **Agregar** cuando se le solicite.

    ![Cuadro de diálogo Contenido bloqueado](../debugger/media/remotedbg-blocked-content.png)

    Al descargar el software, se obtienen algunas solicitudes adicionales para conceder permiso para cargar varios scripts y recursos de sitios web. En my.visualstudio.com, se recomienda agregar los dominios adicionales para asegurarse de que el inicio de sesión se realiza correctamente.