---
title: "Solución de problemas de instalación | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: d8125873ab5a92d9af26c556cb2f953a606c28d9
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-failures"></a>Solución de problemas de instalación de Visual Studio 2017 y errores de actualización

## <a name="symptoms"></a>Síntomas
Cuando intenta instalar o actualizar Microsoft Visual Studio 2017, la operación da error.

## <a name="workaround"></a>Solución
Para solucionar este problema, siga estos pasos:

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Paso 1: Comprobación de si este problema es un problema conocido
Existen algunos problemas conocidos con el instalador de Visual Studio en los que está trabajando Microsoft para intentar resolverlos. Compruebe la [sección de problemas conocidos de nuestras notas de versión](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall) para ver si hay una solución para su problema.

### <a name="step-2---check-with-the-developer-community"></a>Paso 2: Consulta con la comunidad de desarrolladores
Busque su mensaje de error en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html. Puede que otros miembros de la comunidad hayan documentado una solución para su problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Paso 3: Eliminación del directorio del instalador de Visual Studio para corregir problemas de actualización
El programa previo del instalador de Visual Studio es un ejecutable mínimo de poco peso que instala el resto del instalador de Visual Studio. Puede que con la eliminación de los archivos del instalador de Visual Studio y la ejecución repetida del programa previo se resuelvan algunos errores de actualización. Para ello, siga estos pasos:

1. Cierre el instalador de Visual Studio.
2. Elimine el directorio del instalador de Visual Studio. Normalmente, el directorio es C:\Archivos de programa (x86)\Microsoft Visual Studio\Installer.
3. Ejecute al programa previo del instalador de Visual Studio. Puede encontrar el programa previo en su carpeta de descargas con un nombre de archivo que sigue un patrón ```vs_[Visual Studio edition]__*.exe```. Si no encuentra esa aplicación, puede descargar el programa previo; para ello, vaya a la página de [descargas de Visual Studio](https://www.visualstudio.com/downloads/) y haga clic en **Descargar** en su edición de Visual Studio. Ejecute este ejecutable para restablecer sus metadatos de instalación.
4. Intente instalar o actualizar de nuevo Visual Studio. Si el programa de instalación sigue dando error, vaya inmediatamente al paso 4 a continuación.
<br/>**Nota:** Este paso reinstala los archivos de Visual Studio y restablece los metadatos de instalación. 

### <a name="step-4---report-a-problem"></a>Paso 4: Notificación de un problema
En algunas situaciones, como las relacionadas con los archivos dañados, los problemas se pueden examinar caso por caso:

1. Descargue la [herramienta de recopilación de registros de Microsoft Visual Studio y .NET Framework](https://www.microsoft.com/en-us/download/details.aspx?id=12493) y ejecútela. Esta herramienta recopila y compila los registros de instalación disponibles para las instalaciones de Visual Studio, .NET Framework y SQL Server.
2. Abra el instalador de Visual Studio y luego haga clic en **Notificar un problema** para abrir la herramienta de comentarios de Visual Studio.
![Puede desplazarse con la tecla de tabulación hasta el botón Proporcionar comentarios para abrir la herramienta de comentarios](media/report-a-problem.png).
3. Asigne un título a su informe de problema y proporcione los detalles pertinentes. Haga clic en **Siguiente** para ir a la sección **Datos adjuntos** y luego adjunte el archivo de registro generado (normalmente, el archivo está en % TEMP%\vslogs.zip).
![Desplácese con la tecla de tabulación hasta el botón Informar de un problema nuevo y siga los pasos](media/problem-report-details.png).
4. Haga clic en **Siguiente** para revisar el informe del problema y luego haga clic en **Enviar**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Paso 5: Ejecución de InstallCleanup.exe para limpiar los archivos de instalación
Como último recurso, puede ejecutar InstallCleanup.exe. InstallCleanup.exe es una utilidad que se incluye con el instalador de Visual Studio, que limpia los archivos de instalación. No es una reinstalación completa. Esta utilidad elimina los datos de instancia y de caché en Visual Studio de 2017.

1. Cierre el instalador de Visual Studio.
2. Abra un símbolo del sistema de administrador. Para ello, siga estos pasos:
   * En el menú **Inicio**, haga clic en **Ejecutar** (Inicio + R).
   * Escriba **cmd**.
   * Haga clic con el botón derecho en **Símbolo del sistema** y luego elija **Ejecutar como administrador**.
3. Escriba la ruta de acceso completa de la utilidad InstallCleanup.exe y pase el siguiente modificador de línea de comandos: -f. De forma predeterminada, la ruta de acceso de la utilidad es la siguiente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Vuelva a ejecutar al programa previo que se describe en el paso 3.
5. Intente instalar o actualizar de nuevo Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Solución de problemas de un instalador sin conexión
Esta es una tabla de problemas conocidos y algunas soluciones que podrían servir de ayuda al realizar la instalación desde un diseño local.

| Problema       | Elemento                   | Solución |
| ----------- | ---------------------- | -------- |
| Los usuarios no tienen acceso a los archivos. | permisos (ACL) | Asegúrese de que ajusta los permisos (ACL) de manera que concedan acceso de lectura a otros usuarios *antes* de compartir la instalación sin conexión. |
| Las nuevas cargas de trabajo, componentes o idiomas no se instalarán.  | `--layout`  | Asegúrese de que tiene acceso a Internet si instala desde un diseño parcial y selecciona cargas de trabajo, componentes o idiomas que no están disponibles en el diseño anterior. |



