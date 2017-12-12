---
title: "Áreas de trabajo en Herramientas de R para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 06/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 15928f639465f6d8abbaa3735fee40e59ae5045c
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2017
---
# <a name="controlling-where-r-code-runs-with-workspaces"></a>Controlar dónde se ejecuta el código de R con áreas de trabajo

Un área de trabajo de Herramientas de R para Visual Studio (RTVS) le permite configurar dónde se ejecuta una sesión de R, que puede ocurrir en equipos locales y remotos. El objetivo es permitirle trabajar indistintamente con una experiencia de usuario comparable, lo que le ofrece la posibilidad de aprovechar las ventajas de equipos basados en la nube potencialmente más eficaces.

Para abrir la ventana **Áreas de trabajo**, use el comando **Herramientas de R > Ventanas > Áreas de trabajo** o presione Ctrl+9.

![Ventana Áreas de trabajo en Herramientas de R para Visual Studio (VS2017)](media/workspaces-window.png)

En esta ventana, la marca de verificación verde indica el área de trabajo activa a la que está enlazado RTVS. Al seleccionar una flecha azul, se establece el área de trabajo activa. El icono de configuración (engranaje) a la derecha de cada área de trabajo le permite cambiar sus argumentos de línea de comandos, ubicación y nombre. La X roja quita un área de trabajo agregada manualmente.

En este tema:

- [Guardar y restablecer un área de trabajo](#saving-and-resetting-a-workspace)
- [Áreas de trabajo locales](#local-workspaces)
- [Áreas de trabajo remotas](#remote-workspaces)
- [Inicio de sesión en el área de trabajo remota](#remote-workspace-logon)
- [Cambiar de área de trabajo](#switching-between-workspaces)
- [Directorios en equipos locales y remotos](#directories-on-local-and-remote-computers)
- [Copiar los archivos de proyecto en áreas de trabajo remotas](#copying-project-files-to-remote-workspaces)
- [Copiar archivos desde un área de trabajo remota](#copying-files-from-a-remote-workspace)

## <a name="saving-and-resetting-a-workspace"></a>Guardar y restablecer un área de trabajo

De forma predeterminada, RTVS no guarda el estado del área de trabajo al cerrar y volver a abrir un proyecto. En cambio, puede cambiar este comportamiento a través de las [opciones del área de trabajo](options.md#workspace).

El comando **Herramientas de R > Sesión > Restablecer** y el botón Restablecer de la barra de herramientas en la ventana interactiva restablecen también el estado del área de trabajo en cualquier momento. Con las áreas de trabajo remotas, al restablecer se elimina el perfil de usuario creado al conectarse por primera vez al servidor remoto, lo que elimina en realidad los archivos que se hayan acumulado allí.

## <a name="local-workspaces"></a>Áreas de trabajo locales

La lista Áreas de trabajo locales muestra todos los intérpretes de R que se han instalado en el equipo. 

Cuando se inicia Visual Studio, este intenta detectar automáticamente todas las versiones de R que se han instalado al revisar la clave del Registro `HKEY_LOCAL_MACHINE\Software\R-Core\`. Dado que esta comprobación se realiza en el inicio, necesita reiniciar Visual Studio si instala un nuevo intérprete de R.

RTVS podría no detectar un intérprete de R que se instale de forma no estándar (por ejemplo, al copiar simplemente archivos en una carpeta en lugar de ejecutar un instalador). En este caso, cree de forma manual un área de trabajo local de R de la siguiente forma:

1. Seleccione el botón **Agregar** en la ventana Áreas de trabajo.
1. Escriba un nombre para la nueva área de trabajo.
1. Escriba la ruta de acceso a la carpeta raíz de R, que es la que contiene la carpeta `bin` con el intérprete junto con cualquier argumento de línea de comandos opcional para pasar al intérprete cuando se inicia RTVS.
1. Seleccione **Guardar** cuando haya terminado.

![Agregar una nueva área de trabajo](media/workspaces-add-new.png)

## <a name="remote-workspaces"></a>Áreas de trabajo remotas

Las áreas de trabajo remotas le permiten conectarse a una sesión de R en un equipo remoto. (Consulte [Configuración de áreas de trabajo remotas](workspaces-remote-setup.md) para configurar un equipo para este propósito).

Visual Studio no detecta automáticamente las áreas de trabajo remotas, por lo que debe agregarlas manualmente con el botón **Agregar** de la ventana Áreas de trabajo, tal como se describe en la sección anterior. En este caso, escriba el URI del equipo remoto en lugar de una ruta de acceso local.

> [!Important]
> Las áreas de trabajo remotas se identifican mediante un URI que *debe usar el protocolo HTTPS* para garantizar la privacidad y la integridad de la comunicación con el equipo remoto. Visual Studio no puede conectarse a un equipo remoto que no admita HTTPS.

> [!Note]
> Las áreas de trabajo remotas están en versión preliminar. Estamos trabajando en una mejor implementación del problema de sincronización de archivos para una futura versión y agradecemos sus ideas y comentarios.

## <a name="remote-workspace-logon"></a>Inicio de sesión en el área de trabajo remota

Debe usar un nombre de usuario y una contraseña para iniciar sesión en el área de trabajo remota.

### <a name="logon-to-windows-workspace"></a>Inicio de sesión en el área de trabajo de Windows

Si la máquina remota está configurada para usar la cuenta de dominio, puede usar el inicio de sesión de dominio para acceder a un área de trabajo remota. Si no es así, tiene que usar el formato `machine-name\username` para iniciar sesión con una cuenta de equipo en la máquina remota.

### <a name="logon-to-linux-workspace"></a>Inicio de sesión en el área de trabajo de Linux

Para iniciar sesión en una cuenta de Linux, use el formato `<<unix>>\username`. Por ejemplo, si tiene una cuenta con el nombre `ruser`, debe escribir en el nombre de usuario como `<<unix>>\ruser`.

## <a name="switching-between-workspaces"></a>Cambiar de área de trabajo

RTVS está enlazado solo a un área de trabajo a la vez. El área de trabajo enlazada se indica mediante una pequeña marca verde en la ventana Áreas de trabajo. De manera predeterminada, RTVS se enlaza a la última área de trabajo local abierta en una sesión anterior.

Para cambiar el área de trabajo activa, seleccione la flecha azul situada al lado del área de trabajo que quiera. De este modo, se le pide que guarde la sesión, se finaliza el área de trabajo actual y después se cambia a la nueva.

> [!Tip]
> Para deshabilitar el aviso para guardar, seleccione el comando **Herramientas de R > Opciones** y establezca la opción **Mostrar el cuadro de diálogo de confirmación antes de cambiar de área de trabajo** en `No`. Consulte [Opciones del área de trabajo](options.md#workspace).

Si intenta cambiar a un área de trabajo local que se ha desinstalado o a un área de trabajo remota que no está disponible, RTVS podría no estar enlazado a ninguna área de trabajo. Como resultado, es posible que vea un error al escribir código en la ventana interactiva o al intentar ejecutar código de otra forma:

![Error cuando no hay ninguna área de trabajo enlazada a RTVS](media/workspaces-disconnected-interactive-window.png)

Para corregir este problema, cambie a otra área de trabajo en la ventana Áreas de trabajo. Si no hay ningún área de trabajo disponible, necesita instalar un intérprete de R. También puede intentar reiniciar Visual Studio si ha instalado un intérprete con Visual Studio en ejecución.

### <a name="switching-to-a-remote-workspace"></a>Cambiar a un área de trabajo remota

RTVS le pide las credenciales al conectarse por primera vez a un área de trabajo remota y después almacena en caché esas credenciales (mediante la Caja de seguridad de credenciales segura de Windows) para sesiones posteriores. La comunicación con el servidor remoto se realiza después de forma segura sobre HTTPS (que es obligatorio).

En función de la configuración del servidor, puede ver una advertencia de certificado al conectarse que dice: "El certificado de seguridad presentado por los servicios remotos de R no nos permite comprobar que se está conectando de verdad a la máquina (nombre)".

![Advertencia de certificado autofirmado al conectarse a un área de trabajo remota](media/workspaces-remote-self-signed-certificate-warning.png)

El certificado es un documento que el equipo al que está intentando conectarse le presenta a RTVS. El certificado contiene un campo que identifica el URI de ese equipo. La advertencia aparece cuando RTVS detecta una discrepancia entre el URI del certificado y el URI usado para conectarse al equipo, lo que indica que es posible que se haya comprometido la seguridad del servidor.

En cambio, esta advertencia también aparece si se ha usado un *certificado autofirmado* para habilitar HTTPS en el equipo remoto en lugar de usar uno de un proveedor de confianza. Para obtener más información, vea [Configuración de áreas de trabajo remotas](workspaces-remote-setup.md).

## <a name="directories-on-local-and-remote-computers"></a>Directorios en equipos locales y remotos

De forma predeterminada, al iniciar un nuevo intérprete de R en un área de trabajo local, el directorio de trabajo actual es `%userprofile%\Documents`. Si en algún momento quiere cambiar el directorio, use los comandos **Herramientas de R > Directorio de trabajo**, o haga clic con el botón derecho en un proyecto en el Explorador de soluciones de Visual Studio y seleccione comandos como **Establecer el directorio de trabajo aquí**.

Cuando se conecta por primera vez a un equipo remoto, RTVS crea automáticamente un perfil de usuario según sus credenciales, que establece el directorio de trabajo en la carpeta `Documents` de ese perfil. Esta carpeta se usa para todas las sesiones remotas posteriores que usen las mismas credenciales. 

Como resultado, la ubicación exacta donde se ejecuta el código puede diferir entre áreas de trabajo locales y remotas. Por tanto, en su código use siempre rutas de acceso relativas a los archivos de datos, de manera que su código pueda moverse entre áreas de trabajo.

Tenga en cuenta también que con las áreas de trabajo remotas, todos los archivos del directorio de trabajo se mantienen en las sesiones del mismo perfil de usuario. Como se ha indicado anteriormente, puede eliminar estos archivos mediante el comando **Herramientas de R > Sesión > Restablecer** (o el botón Restablecer en la ventana interactiva) al usar un área de trabajo remota. De nuevo, este comando elimina el perfil de usuario del servidor, que se vuelve a crear al volver a conectarse.

## <a name="copying-project-files-to-remote-workspaces"></a>Copiar los archivos de proyecto en áreas de trabajo remotas

Al trabajar con proyectos de R en Visual Studio, el equipo local tiene siempre los últimos archivos del proyecto, incluso si usa un área de trabajo remota. Es decir, al abrir un proyecto en Visual Studio (que normalmente implica abrir una solución que contiene ese proyecto), RTVS supone que todo el contenido del proyecto reside en el equipo local. El área de trabajo remota es, de hecho, solo un host temporal para los archivos del proyecto y cualquier resultado del código. Esto significa que, por ejemplo, al cargar un archivo mediante `source` en la ventana interactiva, ese archivo ya debe estar en el equipo remoto en la ruta de acceso que proporcione o debe estar en el directorio de trabajo actual del intérprete de R remoto (establecido con la función `setwd()`).

Los archivos se copian en el servidor remoto de la siguiente forma:

- Para trabajar con archivos de forma remota a través de la ventana interactiva, primero debe copiarlos manualmente al hacer clic con el botón derecho en los archivos (o el proyecto) en el Explorador de soluciones y seleccionar **Archivos de origen seleccionados**. Los archivos individuales se copian en el directorio de trabajo en el servidor; al copiar un proyecto, RTVS crea una carpeta para el proyecto.

- También puede copiar archivos al seleccionarlos en el Explorador de soluciones y, después, seleccionar **Archivos de origen seleccionados**. Esta acción los carga en la ventana interactiva y se ejecutan allí. Si la sesión está conectada a un equipo remoto, los archivos se copiarán allí en primer lugar.

- Si RTVS está enlazado a un área de trabajo remota y presiona F5, selecciona **Depurar > Iniciar depuración** o inicia la ejecución del código de alguna otra forma, de manera predeterminada RTVS copia el archivo del proyecto en el área de trabajo remota automáticamente (vea a continuación cómo controlar este comportamiento).

- Se sobrescriben todos los archivos que ya existen en el servidor.

> [!Note]
> Ya que RTVS no puede interceptar todas las llamadas de función de R de manera fiable, si se llama a funciones como `source()` o `runApp()` (para aplicaciones Shiny) desde la ventana interactiva, *no* se copian archivos al área de trabajo remota.

Las [Propiedades del proyecto](projects.md#project-properties) controlan si RTVS copia archivos cuando un proyecto está en ejecución y exactamente qué archivos se copian. Para abrir esta página, seleccione el comando de menú **Proyecto > Propiedades de (nombre)** o haga clic con el botón derecho en el Explorador de soluciones y seleccione **Propiedades...**

![Pestaña Ejecutar de las propiedades del proyecto con configuración de transferencia de archivos](media/workspaces-remote-file-transfer-filter-settings.png)

Aquí, la propiedad **Transfer files on run** (Transferir archivos en ejecución) determina si RTVS copia automáticamente los archivos del proyecto. Después, el valor **Files to transfer** (Archivos que se transferirán) filtra exactamente qué archivos se transfieren. El valor predeterminado es copiar solo archivos `.R`, `.Rmd`, `.sql`, `.md` y `.cpp`. Este comportamiento evita copiar de manera involuntaria grandes archivos de datos en el servidor con cada ejecución. 

## <a name="copying-files-from-a-remote-workspace"></a>Copiar archivos desde un área de trabajo remota

Si el script de R genera archivos en el servidor, puede volver a copiarlos en el cliente mediante la función `rtvs::fetch_file`. Esta función acepta, como mínimo, la ruta de acceso remoto al archivo que quiere copiar en el equipo y, opcionalmente, la ruta de acceso de destino en su equipo. Si no especifica una ruta de acceso, el archivo se copia en la carpeta `%userprofile%\Downloads`.
