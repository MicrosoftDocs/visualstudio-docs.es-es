---
title: "Áreas de trabajo en Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 4/27/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d610279c-d6c3-4084-939a-bf042f64d4dd
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7a873df77756e5a957d327049566c8e0db1f3a8a
ms.openlocfilehash: 8ac025a9da5c07cbc9efff416d07c93b91aa2c14
ms.contentlocale: es-es
ms.lasthandoff: 05/12/2017

---


## <a name="controlling-where-r-code-runs-with-workspaces"></a>Controlar dónde se ejecuta el código de R con áreas de trabajo

Un área de trabajo de Herramientas de R para Visual Studio (RTVS) le permite configurar dónde se ejecuta una sesión de R, que puede ocurrir en equipos locales y remotos. El objetivo es permitirle trabajar indistintamente con una experiencia de usuario comparable, lo que le ofrece la posibilidad de aprovechar las ventajas de equipos basados en la nube potencialmente más eficaces.

Para abrir la ventana **Áreas de trabajo**, use el comando **Herramientas de R > Ventanas > Áreas de trabajo** o presione Ctrl+9.

![Ventana Áreas de trabajo en Herramientas de R para Visual Studio (VS2017)](~/rtvs/media/workspaces-window.png)

En esta ventana, la marca de verificación verde indica el área de trabajo activa a la que está enlazado RTVS. Al seleccionar una flecha azul, se establece el área de trabajo activa. El icono de configuración (engranaje) a la derecha de cada área de trabajo le permite cambiar sus argumentos de línea de comandos, ubicación y nombre. La X roja quita un área de trabajo agregada manualmente.

En este tema:

- [Guardar y restablecer un área de trabajo](#saving-and-resetting-a-workspace)
- [Áreas de trabajo locales](#local-workspaces)
- [Áreas de trabajo remotas](#remote-workspaces)
- [Cambiar de área de trabajo](#switching-between-workspaces)
- [Directorios en equipos locales y remotos](#directories-on-local-and-remote-computers)
- [Copiar los archivos de proyecto en áreas de trabajo remotas](#copying-project-files-to-remote-workspaces)
- [Copiar archivos desde un área de trabajo remota](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Guardar y restablecer un área de trabajo

De forma predeterminada, RTVS no guarda el estado del área de trabajo al cerrar y volver a abrir un proyecto. En cambio, puede cambiar este comportamiento a través de las [opciones del área de trabajo](options.md#workspace).

El comando **Herramientas de R > Sesión > Restablecer** y el botón Restablecer de la barra de herramientas en la ventana interactiva restablecen también el estado del área de trabajo en cualquier momento. En el caso de las áreas de trabajo remotas, un restablecimiento tiene el efecto de eliminar el perfil de usuario creado al conectarse por primera vez al servidor remoto, lo que elimina en realidad los archivos que se hayan acumulado allí.

## <a name="local-workspaces"></a>Áreas de trabajo locales

La lista Áreas de trabajo locales muestra todos los intérpretes de R que se han instalado en el equipo. 

RTVS intenta detectar automáticamente todas las versiones de R que se han instalado al revisar la clave del Registro `HKEY_LOCAL_MACHINE\Software\R-Core\` cuando se inicia Visual Studio. Dado que esta comprobación se realiza en el inicio, tendrá que reiniciar Visual Studio si instala un nuevo intérprete de R.

RTVS podría no detectar un intérprete de R que se instale de forma no estándar (por ejemplo, al copiar simplemente archivos en una carpeta en lugar de ejecutar un instalador). En este caso, cree de forma manual un área de trabajo local de R de la siguiente forma:

1. Seleccione el botón **Agregar** en la ventana Áreas de trabajo.
1. Escriba un nombre para la nueva área de trabajo.
1. Escriba la ruta de acceso a la carpeta raíz de R, que es la que contiene la carpeta `bin` con el intérprete y los argumentos de línea de comandos opcionales para pasar al intérprete cuando se inicia RTVS.
1. Seleccione **Guardar** cuando haya terminado.

![Agregar una nueva área de trabajo](~/rtvs/media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Áreas de trabajo remotas

Las áreas de trabajo remotas le permiten conectarse a una sesión de R en un equipo remoto. (Consulte [Configuración de áreas de trabajo remotas](workspaces-remote-setup.md) para configurar un equipo para este propósito).

RTVS no detecta automáticamente las áreas de trabajo remotas, por lo que debe agregarlas manualmente mediante el botón **Agregar** en la ventana Áreas de trabajo como se describe en la sección anterior. En este caso, escriba el URI del equipo remoto en lugar de una ruta de acceso local.

> [!Important]
> Las áreas de trabajo remotas se identifican mediante un URI que *debe usar el protocolo HTTPS* para garantizar la privacidad y la integridad de la comunicación con el equipo remoto. RTVS no se conectará a un equipo remoto que no admita HTTPS.

> [!Note]
> Las áreas de trabajo remotas están en versión preliminar. Estamos trabajando en una mejor implementación del problema de sincronización de archivos para una futura versión y agradecemos sus ideas y comentarios sobre cómo mejorar la experiencia.


## <a name="switching-between-workspaces"></a>Cambiar de área de trabajo

RTVS está enlazado a una sola área de trabajo de cada vez, que se indica mediante una pequeña marca de verificación verde en esa área de trabajo en la ventana Áreas de trabajo. De forma predeterminada, RTVS se enlaza a la última área de trabajo local que tenía abierta en una sesión anterior.

Para cambiar el área de trabajo activa, seleccione la flecha azul situada al lado del área de trabajo que quiera. De este modo, se le pide que guarde la sesión, se finaliza el área de trabajo actual y después se cambia a la nueva.

> [!Tip]
> Para deshabilitar el aviso para guardar, seleccione el comando **Herramientas de R > Opciones** y establezca la opción **Mostrar el cuadro de diálogo de confirmación antes de cambiar de área de trabajo** en `No`. Consulte [Opciones del área de trabajo](options.md#workspace).

Si intenta cambiar a un área de trabajo local que se ha desinstalado o un área de trabajo remota que no está disponible, podría encontrarse con situaciones donde un proyecto de RTVS no está enlazado a ninguna área de trabajo. Como resultado, es posible que aparezca un error como el siguiente al escribir código en la ventana interactiva o, de lo contrario, intentar ejecutar código. Para corregir este problema, cambie simplemente a otra área de trabajo en la ventana Áreas de trabajo. Si no hay ninguna disponible, deberá instalar un intérprete de R. También puede intentar reiniciar Visual Studio si ha instalado un intérprete con Visual Studio en ejecución.

![Error cuando no hay ninguna área de trabajo enlazada a RTVS](~/rtvs/media/workspaces-disconnected-interactive-window.png)

### <a name="switching-to-a-remote-workspace"></a>Cambiar a un área de trabajo remota

RTVS le pide las credenciales al conectarse por primera vez a un área de trabajo remota y después almacena en caché esas credenciales (mediante la Caja de seguridad de credenciales segura de Windows) para sesiones posteriores. La comunicación con el servidor remoto se realiza después de forma segura sobre HTTPS (que es obligatorio).

Según la configuración del servidor, puede ver una advertencia de certificado al conectarse: "El certificado de seguridad presentado por los servicios remotos de R no nos permite comprobar que se está conectando de verdad a la máquina (nombre)".

![Advertencia de certificado autofirmado al conectarse a un área de trabajo remota](~/rtvs/media/workspaces-remote-self-signed-certificate-warning.png)

El certificado es un documento que presenta a RTVS la máquina a la que está intentando conectarse, que contiene un campo que identifica el URI de la máquina. La advertencia aparece cuando RTVS detecta una discrepancia entre el URI del certificado y el URI usado para conectarse a la máquina, lo que indica que es posible que se haya comprometido la seguridad del servidor.

En cambio, esta advertencia también aparecerá si se ha usado un *certificado autofirmado* para habilitar HTTPS en el equipo remoto en lugar de usar uno de un proveedor de confianza. Para obtener más información, consulte [Configuración de áreas de trabajo remotas](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Directorios en equipos locales y remotos

De forma predeterminada, al iniciar un nuevo intérprete de R en un área de trabajo local, el directorio de trabajo actual es `%userprofile%\Documents`. Puede cambiarlo en cualquier momento mediante los comandos **Herramientas de R > Directorio de trabajo**, o al hacer clic con el botón derecho en un proyecto en el Explorador de soluciones de Visual Studio y seleccionar comandos como **Establecer el directorio de trabajo aquí**.

En equipos remotos, RTVS crea automáticamente un perfil de usuario según sus credenciales cuando se conecta por primera vez a ese servidor, por lo que el directorio de trabajo es la carpeta `Documents` de ese perfil. Esto se usará para todas las sesiones remotas posteriores que usen las mismas credenciales. 

Como resultado, la ubicación exacta donde se ejecuta el código puede diferir entre áreas de trabajo locales y remotas. Por tanto, en el código, evite usar rutas de acceso absolutas a archivos de datos, porque lo más probable es que el código no se pueda intercambiar entre áreas de trabajo. Use en su lugar rutas de acceso relativas.

Tenga en cuenta también que con las áreas de trabajo remotas, todos los archivos del directorio de trabajo se mantienen en las sesiones del mismo perfil de usuario. Como se ha indicado anteriormente, puede eliminarlos mediante el comando **Herramientas de R > Sesión > Restablecer** (o el botón Restablecer en la ventana interactiva) al usar un área de trabajo remota. De nuevo, esto elimina el perfil de usuario del servidor, que se vuelve a crear al volver a conectarse.

## <a name="copying-project-files-to-remote-workspaces"></a>Copiar los archivos de proyecto en áreas de trabajo remotas

Al trabajar con proyectos de R en Visual Studio, el equipo local tiene siempre los últimos archivos del proyecto, incluso si usa un área de trabajo remota. Es decir, al abrir un proyecto en Visual Studio (que normalmente implica abrir una solución que contiene ese proyecto), RTVS supone que todo el contenido del proyecto reside en el equipo local. El área de trabajo remota es, de hecho, solo un host temporal para los archivos del proyecto y cualquier resultado del código. Esto significa que, por ejemplo, al cargar un archivo mediante `source` en la ventana interactiva, ese archivo ya debe estar en el equipo remoto en la ruta de acceso que proporcione o debe estar en el directorio de trabajo actual del intérprete de R remoto (establecido con la función `setwd()`).

Los archivos se copian en el servidor remoto de la siguiente forma:

- Para trabajar con archivos de forma remota a través de la ventana interactiva, primero debe copiarlos manualmente al hacer clic con el botón derecho en los archivos (o el proyecto) en el Explorador de soluciones y seleccionar **Archivos de origen seleccionados**. Los archivos individuales se copiarán en el directorio de trabajo en el servidor; al copiar un proyecto, RTVS creará una carpeta para el proyecto.

- También puede copiar archivos al seleccionarlos en el Explorador de soluciones y, después, seleccionar **Archivos de origen seleccionados**. De esta forma se cargan en la ventana interactiva y se ejecutan allí. Si la sesión está conectada a un equipo remoto, los archivos se copiarán allí en primer lugar.

- Si RTVS está enlazado a un área de trabajo remota y presiona F5, selecciona **Depurar > Iniciar depuración** o, de lo contrario, inicia la ejecución del código, de forma predeterminada, RTVS copiará el archivo del proyecto en el área de trabajo remota automáticamente (consulte a continuación cómo controlarlo).

- Se sobrescribirán todos los archivos que ya existan en el servidor.

> [!Note]
> Ya que RTVS no puede interceptar todas las llamadas de función de R de forma fiable, si se llama a funciones como `source()` o `runApp()` (para aplicaciones Shiny) desde la ventana interactiva, *no* se copiarán archivos al área de trabajo remota.

Si RTVS copia archivos cuando un proyecto está en ejecución (y exactamente qué archivos se copian) se controla a través de las [propiedades del proyecto](projects.md#project-properties). Para abrir esta página, seleccione el comando de menú **Proyecto > Propiedades de (nombre)** o haga clic con el botón derecho en el Explorador de soluciones y seleccione **Propiedades...**

![Pestaña Ejecutar de las propiedades del proyecto con configuración de transferencia de archivos](~/rtvs/media/workspaces-remote-file-transfer-filter-settings.png)

Aquí, **Transfer files on run** (Transferir archivos en ejecución) determina si RTVS copia automáticamente los archivos del proyecto. Después, el valor **Files to transfer** (Archivos que se transferirán) filtra exactamente qué archivos se transfieren. El valor predeterminado es copiar solo archivos `.R`, `.Rmd`, `.sql`, `.md` y `.cpp`. Esto se hace para evitar copiar de forma involuntaria grandes archivos de datos en el servidor con cada ejecución. 

## <a name="copying-files-from-a-remote-workspace"></a>Copiar archivos desde un área de trabajo remota

Si el script de R genera archivos en el servidor, puede volver a copiarlos en el cliente mediante la función `rtvs::fetch_file`. Esta función acepta, como mínimo, la ruta de acceso remoto al archivo que quiere copiar en el equipo y, opcionalmente, la ruta de acceso en el equipo donde quiere que se copie ese archivo. Si no especifica una ruta de acceso, el archivo se copiará en la carpeta `%userprofile%\Downloads`.

