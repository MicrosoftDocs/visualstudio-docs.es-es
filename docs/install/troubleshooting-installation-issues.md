---
title: Solucionar problemas de instalación con Visual Studio 2017
description: En ocasiones, algo no sale según lo previsto. Si se produce un error en la actualización o instalación de Visual Studio, esta página puede ayudarle.
ms.date: 11/21/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02ed2724f82923ed2157133c3c36b9ff06a1b7d5
ms.sourcegitcommit: 4667e6ad223642bc4ac525f57281482c9894daf4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/20/2018
ms.locfileid: "36282959"
---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Solución de problemas de instalación y actualización de Visual Studio 2017

## <a name="symptoms"></a>Síntomas

Cuando intenta instalar o actualizar Visual Studio 2017, la operación da error.

## <a name="workaround"></a>Solución

Para solucionar este problema, siga estos pasos:

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Paso 1: Comprobación de si este problema es un problema conocido

Existen algunos problemas conocidos con el instalador de Visual Studio en los que está trabajando Microsoft para intentar resolverlos. Para ver si hay una solución para el problema, vea la [sección de problemas conocidos de nuestras notas de la versión](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

### <a name="step-2---check-with-the-developer-community"></a>Paso 2: Consulta con la comunidad de desarrolladores

Busque el mensaje de error en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Puede que otros miembros de la comunidad hayan documentado una solución para su problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Paso 3: Eliminación del directorio del instalador de Visual Studio para corregir problemas de actualización

El programa previo del instalador de Visual Studio es un ejecutable mínimo de poco peso que instala el resto del instalador de Visual Studio. Puede que con la eliminación de los archivos del instalador de Visual Studio y la ejecución repetida del programa previo se resuelvan algunos errores de actualización.

>[!NOTE]
Al realizar las acciones siguientes, se reinstalan los archivos del Instalador de Visual Studio y se restablecen los metadatos de la instalación.

1. Cierre el instalador de Visual Studio.
2. Elimine el directorio del instalador de Visual Studio. Normalmente, el directorio es `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Ejecute al programa previo del instalador de Visual Studio. Puede encontrar el programa previo en su carpeta de descargas con un nombre de archivo que sigue un patrón `vs_[Visual Studio edition]__*.exe`. Si no encuentra esa aplicación, puede descargar el programa previo; para ello, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/) y haga clic en **Descargar** en su edición de Visual Studio. Ejecute el ejecutable para restablecer sus metadatos de instalación.
4. Intente instalar o actualizar de nuevo Visual Studio. Si el Instalador sigue dando error, vaya al paso siguiente.

### <a name="step-4---report-a-problem"></a>Paso 4: Notificación de un problema

En algunas situaciones, como las relacionadas con los archivos dañados, los problemas se pueden examinar caso por caso:

1. Recopile sus registros de configuración. Vea [Cómo obtener los registros de instalación de Visual Studio](#how-to-get-the-visual-studio-installation-logs) para más información.
2. Abra el instalador de Visual Studio y luego haga clic en **Notificar un problema** para abrir la herramienta de comentarios de Visual Studio.
![Puede desplazarse con la tecla de tabulación hasta el botón Proporcionar comentarios para abrir la herramienta de comentarios](media/report-a-problem.png).
3. Asigne un título a su informe de problema y proporcione los detalles pertinentes. Haga clic en **Siguiente** para ir a la sección **Datos adjuntos** y luego adjunte el archivo de registro generado (normalmente, el archivo está en `%TEMP%\vslogs.zip`).
4. Haga clic en **Siguiente** para revisar el informe del problema y luego haga clic en **Enviar**.

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Paso 5: Ejecutar InstallCleanup.exe para quitar los archivos de instalación

Como último recurso, también puede [quitar Visual Studio](remove-visual-studio.md) para eliminar todos los archivos de instalación y la información de producto.

1. Siga las instrucciones de [Quitar Visual Studio](remove-visual-studio.md).
2. Vuelva a ejecutar el programa previo que se describe en [Paso 3: Eliminación del directorio del Instalador de Visual Studio para corregir problemas de actualización](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Intente instalar o actualizar de nuevo Visual Studio.

### <a name="step-6---contact-us-optional"></a>Paso 6: Póngase en contacto con nosotros (opcional)

Si no consigue instalar correctamente con ninguno de los otros pasos, puede ponerse en contacto con nosotros por chat para solicitar asistencia para la instalación (disponible solo en inglés). Para más información, vea la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

## <a name="how-to-troubleshoot-an-offline-installer"></a>Solución de problemas de un instalador sin conexión

Esta es una tabla de problemas conocidos y algunas soluciones que podrían servir de ayuda al realizar la instalación desde un diseño local.

| Problema       | Elemento                   | Soluciones |
| ----------- | ---------------------- | -------- |
| Los usuarios no tienen acceso a los archivos. | permisos (ACL) | Asegúrese de que ajusta los permisos (ACL) de manera que concedan acceso de lectura a otros usuarios *antes* de compartir la instalación sin conexión. |
| Las nuevas cargas de trabajo, componentes o idiomas no se instalarán.  | `--layout`  | Asegúrese de que tiene acceso a Internet si instala desde un diseño parcial y selecciona cargas de trabajo, componentes o idiomas que no estaban descargados previamente en ese diseño parcial. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Obtención de registros de instalación de Visual Studio

Los registros de instalación son necesarios para solucionar la mayoría de los problemas de instalación. Cuando se envía un problema mediante el uso de [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) del Instalador de Visual Studio, estos registros se incluyen automáticamente en el informe.

Si se pone en contacto con el Soporte técnico de Microsoft, puede que necesite proporcionar estos registros de instalación mediante la [herramienta de recopilación de registros de Microsoft Visual Studio y .NET Framework](https://aka.ms/vscollect). La herramienta de recopilación de registros recopila registros de instalación de todos los componentes instalados por Visual 2017 Studio, incluido .NET Framework, Windows SDK y SQL Server. También recopila información del equipo, un inventario de Windows Installer y la información de registro de eventos de Windows para el Instalador de Visual Studio, Windows Installer y Restaurar sistema.

Para recopilar los registros:

1. [Descargue la herramienta](https://aka.ms/vscollect).
2. Abra un símbolo del sistema administrativo.
3. Ejecute `Collect.exe` desde el directorio donde guardó la herramienta.
4. Busque el archivo `vslogs.zip` resultante en el directorio `%TEMP%`, por ejemplo, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> La herramienta debe ejecutarse en la misma cuenta de usuario en la que se ejecutó la instalación que dio error. Si ejecuta la herramienta desde una cuenta de usuario diferente, establezca la opción `–user:<name>` para especificar la cuenta de usuario en la que se ejecutó la instalación con errores. Ejecute `Collect.exe -?` desde un símbolo del sistema de administrador para obtener información adicional sobre las opciones y el uso.

## <a name="more-support-options"></a>Más opciones de soporte técnico

Si no consigue instalar correctamente con ninguno de los otros pasos, puede ponerse en contacto con nosotros por chat para solicitar asistencia para la instalación (disponible solo en inglés). Para más información, vea la [página de soporte técnico de Visual Studio](https://visualstudio.microsoft.com/vs/support/#talktous).

Aquí tiene algunas opciones más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esto requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Instalar Visual Studio detrás de un firewall o servidor proxy](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Quitar Visual Studio 2017](remove-visual-studio.md)
