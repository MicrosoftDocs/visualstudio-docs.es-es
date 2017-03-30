---
title: "Creación de un instalador sin conexión para Visual Studio 2017 | Microsoft Docs"
description: "Obtenga información sobre cómo crear un instalador sin conexión de Visual Studio."
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
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
translationtype: Human Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 563c78a49eb55886b1ddbd4f437951c99c6568e5
ms.lasthandoff: 03/22/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Creación de un instalador sin conexión para Visual Studio 2017
Sabemos que muchos clientes desean disponer de un instalador sin conexión para [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067). A pesar de no ofrecemos una imagen ISO, es fácil crear una carpeta que puede usar para una instalación sin conexión.

Esta es la manera de hacerlo.

## <a name="download-the-setup-file-you-want"></a>Descargue el archivo de configuración que desee.
**[Descargue](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** la edición de Visual Studio que desee. Asegúrese de hacer clic en **Guardar** y, a continuación, haga clic en **Abrir carpeta**.

El archivo de instalación&mdash;o para ser más específico, un archivo de programa previo&mdash;coincidirá con uno de los siguientes.

|Edición | Archivo|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Comunidad de Visual Studio |**vs_community.exe**|

Otros programas previos admitidos incluyen vs_buildtools.exe, vs_feedbackclient.exe, vs_teamexplorer.exe, vs_testagent.exe, vs_testcontroller.exe y vs_testprofessional.exe.

## <a name="create-an-offline-installation-folder"></a>Creación de una carpeta de instalación sin conexión
Para crear una instalación sin conexión con todos los lenguajes y todas las características, utilice uno de los comandos de los ejemplos siguientes.

(Asegúrese de ejecutar el comando desde el directorio de descarga. Normalmente, es `C:\Users\<username>\Downloads` en un equipo que ejecuta Windows 10).

- Para Visual Studio Enterprise, ejecute: <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Para Visual Studio Professional, ejecute: <br> ```vs_professional.exe --layout c:\vs2017offline```
- Para Visual Studio Community, ejecute: <br> ```vs_community.exe --layout c:\vs2017offline```

Para obtener más ejemplos, vea la sección [Personalización del instalador sin conexión](#how-to-customize-your-offline- installer) de esta página.

## <a name="install-from-the-offline-installation-folder"></a>Instalación desde la carpeta de instalación sin conexión
Ejecute la instalación sin conexión ahora o más tarde; la decisión le corresponde a usted. Sin embargo, cuando lo haga, siga estos pasos.

  1. Instale los certificados (están en la carpeta de certificados, que se encuentra en la carpeta de diseño. Basta con hacer clic derecho en cada una de ellos para instalarlos).

  2. Ejecute el archivo de instalación. Por ejemplo, ejecute: <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Sugerencias adicionales para instaladores sin conexión
Es fácil personalizar o actualizar su instalador sin conexión; le mostraremos cómo hacerlo. Y si algo va mal con el instalador sin conexión, tenemos a su disposición información de solución de problemas y soporte técnico.

### <a name="how-to-customize-your-offline-installer"></a>Personalización del instalador sin conexión
Hay muchas opciones que puede utilizar para personalizar el instalador sin conexión. Estos son algunos ejemplos de cómo se personaliza por [configuración regional de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Para descargar todas las cargas de trabajo y los componentes para un solo idioma, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Para descargar todas las cargas de trabajo y los componentes para varios idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Para descargar una carga de trabajo para todos los idiomas, ejecute: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - Para descargar dos cargas de trabajo y un componente opcional para tres idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` Para obtener más información acerca de las opciones que puede utilizar para personalizar la instalación, consulte nuestra página [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Actualización de un instalador sin conexión
Quizá prefiera actualizar el instalador sin conexión en un momento posterior. Esta es la manera de hacerlo.
* Para actualizar una instancia de Visual Studio que ha instalado desde una carpeta de instalación sin conexión, ejecute el instalador de Visual Studio y, a continuación, haga clic en **Actualizar**.
* Para actualizar la carpeta de instalación sin conexión para que incluya las actualizaciones más recientes, ejecute el comando ```--layout``` de nuevo. Asegúrese de que señale a la misma carpeta que utilizó anteriormente; de este modo, solo se descargarán los componentes que se hayan actualizado desde la última ejecución de ```--layout```.


### <a name="how-to-troubleshoot-an-offline-installer"></a>Solución de problemas de un instalador sin conexión
En ocasiones, algo no sale según lo previsto. Aquí presentamos una tabla de problemas conocidos y algunas soluciones que le pueden ayudar.

| Problema       | Elemento                   | Solución |
| ----------- | ---------------------- | -------- |
| Recibe un mensaje de advertencia acerca de que no se pueden instalar algunos componentes y paquetes.  | Programa de instalación de Android SDK (nivel de API) | Si desea incluir paquetes de Android SDK (nivel de API), debe tener una conexión a Internet cuando se crea el instalador sin conexión. Si está en una red restringida, debe permitir el acceso a las siguientes direcciones URL: <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Para obtener información sobre cómo resolver posibles problemas con la configuración de proxy, vea la publicación del blog [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errores de instalación de Visual Studio [Instalación de Android SDK] detrás de un proxy).  |  
| Los usuarios no tienen acceso a los archivos. | permisos (ACL) | Asegúrese de que ajusta los permisos (ACL) de manera que concedan acceso de lectura a otros usuarios *antes* de compartir la instalación sin conexión. |
| Las nuevas cargas de trabajo, componentes o idiomas no se instalarán.  | `--layout`  | Asegúrese de que tiene acceso a Internet si instala desde un diseño parcial y selecciona cargas de trabajo, componentes o idiomas que no están disponibles en el diseño anterior. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión
Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es utilizar la herramienta [Notificar un problema	](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

Tenemos también otras opciones de soporte técnico disponibles. Para ver un listado, consulte la página [Hable con nosotros](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)

