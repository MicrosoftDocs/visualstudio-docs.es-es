---
title: Solución de problemas de instalación o actualización
description: En ocasiones, algo no sale según lo previsto. Si se produce un error en la actualización o instalación de Visual Studio, esta página puede ayudarle.
ms.date: 09/13/2019
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 24a6a642528fbf8fed7b8000434a963e32cc85ee
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594492"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Solución de problemas de instalación y actualización de Visual Studio

> [!IMPORTANT]
> ¿Tiene un problema con la instalación? Podemos ayudarle. Disponemos de una opción de soporte de [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo en inglés).

Esta guía incluye instrucciones paso a paso que deberían resolver la mayoría de los problemas de instalación.

## <a name="online-installations"></a>Instalaciones en línea

Los pasos siguientes están optimizados para una instalación típica en línea. Para un problema que afecta a una instalación sin conexión, consulte [Solución de problemas de una instalación sin conexión](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Paso 1: Comprobación de si este problema es un problema conocido

::: moniker range="vs-2017"

Existen algunos problemas conocidos con el instalador de Visual Studio en los que está trabajando Microsoft para intentar resolverlos. Para ver si hay una solución para el problema, vea la [sección de problemas conocidos de nuestras notas de la versión](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Existen algunos problemas conocidos con el instalador de Visual Studio en los que está trabajando Microsoft para intentar resolverlos. Para ver si hay una solución para el problema, vea la [sección de problemas conocidos de nuestras notas de la versión](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Paso 2: Consulta con la comunidad de desarrolladores

Busque el mensaje de error en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Puede que otros miembros de la comunidad hayan documentado una solución para su problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Paso 3: Eliminación del directorio del instalador de Visual Studio para corregir problemas de actualización

El programa previo del instalador de Visual Studio es un ejecutable mínimo de poco peso que instala el resto del instalador de Visual Studio. Puede que con la eliminación de los archivos del instalador de Visual Studio y la ejecución repetida del programa previo se resuelvan algunos errores de actualización.

> [!NOTE]
> Al realizar las acciones siguientes, se reinstalan los archivos del Instalador de Visual Studio y se restablecen los metadatos de la instalación.

::: moniker range="vs-2017"

1. Cierre el instalador de Visual Studio.
2. Elimine el directorio del instalador de Visual Studio. Normalmente, el directorio es `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Ejecute al programa previo del instalador de Visual Studio. Puede encontrar el programa previo en su carpeta de descargas con un nombre de archivo que sigue un patrón `vs_[Visual Studio edition]__*.exe`. Si no encuentra esa aplicación, puede descargar el programa previo; para ello, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) y haga clic en **Descargar** en su edición de Visual Studio. Entonces, ejecute el ejecutable para restablecer sus metadatos de instalación.
4. Intente instalar o actualizar de nuevo Visual Studio. Si el Instalador sigue dando error, vaya al paso siguiente.

::: moniker-end

::: moniker range="vs-2019"

1. Cierre el instalador de Visual Studio.
2. Elimine el directorio del instalador de Visual Studio. Normalmente, el directorio es `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Ejecute al programa previo del instalador de Visual Studio. Puede encontrar el programa previo en su carpeta de descargas con un nombre de archivo que sigue un patrón `vs_[Visual Studio edition]__*.exe`. Si no encuentra esa aplicación, puede descargar el programa previo; para ello, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) y haga clic en **Descargar** en su edición de Visual Studio. Entonces, ejecute el ejecutable para restablecer sus metadatos de instalación.
4. Intente instalar o actualizar de nuevo Visual Studio. Si el Instalador sigue dando error, vaya al paso siguiente.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Paso 4: Notificación de un problema

En algunas situaciones, como las relacionadas con los archivos dañados, los problemas se pueden examinar caso por caso. Para que podamos ayudarle, realice lo siguiente:

::: moniker range="vs-2017"

1. Recopile sus registros de configuración. Vea [Cómo obtener los registros de instalación de Visual Studio](#installation-logs) para más información.
2. Abra el instalador de Visual Studio y luego haga clic en **Notificar un problema** para abrir la herramienta de comentarios de Visual Studio.
![Puede desplazarse con la tecla de tabulación hasta el botón Proporcionar comentarios para abrir la herramienta de comentarios](media/report-a-problem.png).
3. Asigne un título a su informe de problema y proporcione los detalles pertinentes. Haga clic en **Siguiente** para ir a la sección **Datos adjuntos** y luego adjunte el archivo de registro generado (normalmente, el archivo está en `%TEMP%\vslogs.zip`).
4. Haga clic en **Siguiente** para revisar el informe del problema y luego haga clic en **Enviar**.

::: moniker-end

::: moniker range="vs-2019"

1. Recopile sus registros de configuración. Vea [Cómo obtener los registros de instalación de Visual Studio](#installation-logs) para más información.
2. Abra el instalador de Visual Studio y luego haga clic en **Notificar un problema** para abrir la herramienta de comentarios de Visual Studio.
![Puede desplazarse con la tecla de tabulación hasta el botón Proporcionar comentarios para abrir la herramienta de comentarios](media/vs-2019/vs-installer-report-problem.png).
3. Asigne un título a su informe de problema y proporcione los detalles pertinentes. Haga clic en **Siguiente** para ir a la sección **Datos adjuntos** y luego adjunte el archivo de registro generado (normalmente, el archivo está en `%TEMP%\vslogs.zip`).
4. Haga clic en **Siguiente** para revisar el informe del problema y luego haga clic en **Enviar**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Paso 5: Ejecutar InstallCleanup.exe para quitar los archivos de instalación

Como último recurso, también puede [quitar Visual Studio](remove-visual-studio.md) para eliminar todos los archivos de instalación y la información de producto.

1. Siga las instrucciones de [Quitar Visual Studio](remove-visual-studio.md).
2. Vuelva a ejecutar el programa previo que se describe en [Paso 3: Eliminación del directorio del Instalador de Visual Studio para corregir problemas de actualización](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Intente instalar o actualizar de nuevo Visual Studio.

### <a name="step-6---contact-us-optional"></a>Paso 6: Póngase en contacto con nosotros (opcional)

Si no ha podido instalar o actualizar Visual Studio con ninguno de los pasos anteriores, póngase en contacto con nosotros con nuestra opción de soporte de [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo en inglés) a fin de obtener más asistencia.

## <a name="offline-installations"></a>Instalaciones sin conexión

Esta es una tabla de incidencias conocidas y algunas soluciones que podrían servirle de ayuda al crear una [instalación sin conexión](create-an-offline-installation-of-visual-studio.md) y luego realizar la instalación desde un diseño local.

| Problema       | Elemento                   | Soluciones |
| ----------- | ---------------------- | -------- |
| Los usuarios no tienen acceso a los archivos. | permisos (ACL) | Asegúrese de que ajusta los permisos (ACL) de manera que concedan acceso de lectura a otros usuarios *antes* de compartir la instalación sin conexión. |
| Las nuevas cargas de trabajo, componentes o idiomas no se instalarán.  | `--layout`  | Asegúrese de que tiene acceso a Internet si instala desde un diseño parcial y selecciona cargas de trabajo, componentes o idiomas que no estaban descargados previamente en ese diseño parcial. |

Para obtener más información sobre cómo resolver incidencias con una [instalación de red](create-a-network-installation-of-visual-studio.md), consulte [Solución de problemas relacionados con la red al instalar o usar Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Registros de instalación

Los registros de instalación son necesarios para solucionar la mayoría de los problemas de instalación. Cuando se envía un problema mediante el uso de [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio.md) del Instalador de Visual Studio, estos registros se incluyen automáticamente en el informe.

Si se pone en contacto con el Soporte técnico de Microsoft, puede que necesite proporcionar estos registros de instalación mediante la [herramienta de recopilación de registros de Microsoft Visual Studio y .NET Framework](https://aka.ms/vscollect). La herramienta de recopilación de registros recopila registros de instalación de todos los componentes instalados por Visual Studio, incluido .NET Framework, Windows SDK y SQL Server. También recopila información del equipo, un inventario de Windows Installer y la información de registro de eventos de Windows para el Instalador de Visual Studio, Windows Installer y Restaurar sistema.

Para recopilar los registros:

1. [Descargue la herramienta](https://aka.ms/vscollect).
2. Abra un símbolo del sistema administrativo.
3. Ejecute `Collect.exe` desde el directorio donde guardó la herramienta.
4. Busque el archivo `vslogs.zip` resultante en el directorio `%TEMP%`, por ejemplo, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> La herramienta debe ejecutarse en la misma cuenta de usuario en la que se ejecutó la instalación que dio error. Si ejecuta la herramienta desde una cuenta de usuario diferente, establezca la opción `–user:<name>` para especificar la cuenta de usuario en la que se ejecutó la instalación con errores. Ejecute `Collect.exe -?` desde un símbolo del sistema de administrador para obtener información adicional sobre las opciones y el uso.

## <a name="live-help"></a>Ayuda en directo

Si las soluciones incluidas en esta guía de solución de problemas no le ayudan a instalar o actualizar Visual Studio, use nuestra opción de soporte de [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo en inglés) para obtener más asistencia.

## <a name="see-also"></a>Vea también

* [Quitar Visual Studio](remove-visual-studio.md)
* [Instalación y uso de Visual Studio y de servicios de Azure detrás de un firewall o servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
