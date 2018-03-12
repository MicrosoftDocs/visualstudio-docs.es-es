---
title: "Solución de problemas y problemas conocidos (Visual Studio Tools para Unity) | Microsoft Docs"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 95d1724561886e1bcfa9a870bdf3bdadb787f9e8
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Solución de problemas y problemas conocidos (Visual Studio Tools para Unity)
En esta sección encontrará soluciones a problemas comunes con Visual Studio Tools para Unity y descripciones de problemas conocidos. Asimismo descubrirá cómo puede ayudar a mejorar Visual Studio Tools para Unity mediante la notificación de errores.

## <a name="troubleshooting"></a>Solución de problemas
Para resolver algunos problemas comunes que se producen al trabajar con Visual Studio Tools para Unity, consulte las secciones siguientes.

### <a name="visual-studio-crashes"></a>Bloqueo de Visual Studio
Esto puede deberse a que la memoria caché de MEF de Visual Studio está dañada.

Debe quitar la carpeta siguiente para restablecer la caché de MEF (cierre Visual Studio antes de hacerlo):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Esto debería resolver el problema. En caso de que siga experimentando el problema, ejecute un símbolo del sistema para desarrolladores de Visual Studio como administrador y use el comando siguiente:

```batch
 devenv /setup
```

### <a name="issues-with-vs2015-and-intellisense-or-code-coloration"></a>Problemas de VS2015 e IntelliSense, o de colores de código.
Debe intentar actualizar el proyecto de Visual Studio 2015 a Update 3.

### <a name="visual-studio-hangs"></a>Visual Studio deja de responder
Varios complementos de Unity, como, por ejemplo, Parse, FMOD, UMP (Universal Media Player), ZFBrowser o Embedded Browser usan subprocesos nativos. Resulta problemático cuando un complemento acaba de asociar un subproceso nativo al runtime, que luego realiza llamadas de bloqueo al sistema operativo. Esto significa que Unity no puede interrumpir ese subproceso del depurador (o recarga del dominio) y deja de responder.

En el caso de FMOD hay una solución alternativa, puede pasar la [marca](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) de inicialización FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE para deshabilitar el procesamiento asincrónico y realizar todo el procesamiento en el subproceso principal.

### <a name="incompatible-project-in-visual-studio"></a>Proyecto no compatible en Visual Studio
En primer lugar, compruebe que Visual Studio está establecido como editor de scripts externo en Unity (Editar/Preferencias/Herramientas externas). Después, compruebe que el complemento de Visual Studio está instalado en Unity ("Ayuda/Acerca de" debe mostrar en la parte inferior un mensaje como Microsoft Visual Studio Tools para Unity está habilitado). Después, compruebe que la extensión está instalada correctamente en Visual Studio (Ayuda/Acerca de).

### <a name="assembly-reference-issues"></a>Problemas de referencias de ensamblado
Si el proyecto incluye referencias complejas o si se quiere controlar mejor este paso de generación, se puede usar nuestra [API](../cross-platform/customize-project-files-created-by-vstu.md) para manipular el contenido de la solución o el proyecto que se genera. También puede usar [archivos de respuesta](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) en el proyecto de Unity y los procesaremos.

### <a name="breakpoints-with-a-warning"></a>Puntos de interrupción con advertencia
Si Visual Studio no encuentra una ubicación de origen para un punto de interrupción concreto, aparecerá una advertencia en el punto de interrupción. Compruebe que el comportamiento que usa está cargado y se emplea correctamente en la escena actual de Unity.

### <a name="breakpoints-not-hit"></a>Puntos de interrupción no ejecutados
 Compruebe que el comportamiento que usa está cargado y se emplea correctamente en la escena actual de Unity. Salga de Visual Studio y Unity y, luego, elimine todos los archivos generados (*.csproj, *.sln) y la carpeta de biblioteca completa.

### <a name="unable-to-attach"></a>Imposibilidad de efectuar la asociación
-   Intente deshabilitar temporalmente el antivirus o cree reglas de exclusión para VS y Unity.
-   Intente deshabilitar temporalmente el firewall o cree reglas que permitan redes TCP/UDP entre VS y Unity.
-   Hemos identificado que programas como TeamViewer interfieren en la detección de procesos. Puede intentar detener temporalmente cualquier software adicional para ver si cambia algo.
-   No cambie el nombre del archivo ejecutable principal de Unity, ya que VSTU solo supervisa procesos con el nombre "Unity.exe".

### <a name="unable-to-debug-android-players"></a>Imposibilidad de depurar reproductores de Android
La multidifusión se usa para la detección de reproductores (que es el mecanismo predeterminado que usa Unity), pero después se usa una conexión TCP normal para asociar el depurador. La fase de detección es el principal problema con dispositivos Android.

USB es muy rápido para la depuración, pero no es compatible con el mecanismo de detección de reproductores de Unity.
Wi-Fi es más versátil, pero no ofrece la misma velocidad en comparación con USB debido a la latencia. Hemos visto una falta de compatibilidad de multidifusión adecuada en algunos enrutadores o dispositivos (por ejemplo, el caso de las series de Nexus).

Puede probar lo siguiente mediante USB para ver los puertos abiertos en el dispositivo conectado (con el reproductor en ejecución para que pueda comprobar el puerto de depuración, siempre en el formato 56xxx):

```shell
adb shell netstat
```

Reenvíe el puerto al equipo local:

```shell
adb forward tcp:56xxx tcp:56xxx
```

Después, conecte VSTU mediante el puerto reenviado 127.0.0.1:56xxx.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrar de UnityVS a Visual Studio Tools para Unity
 Si está migrando de UnityVS a Visual Studio Tools para Unity, debe generar nuevas soluciones de Visual Studio para los proyectos de Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Migrar un proyecto Unity de UnityVS 1.8 a Visual Studio Tools para Unity 1.9

1.  Elimine los antiguos archivos de solución y proyecto del proyecto de Unity. En el directorio raíz del proyecto Unity, busque los archivos .sln y .*proj de Visual Studio y elimínelos todos.

2.  Importe el paquete de Visual Studio Tools para Unity en su proyecto de Unity. Para obtener información sobre cómo importar el paquete de VSTU, vea Configurar Visual Studio Tools para Unity en la página [Introducción](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .

3.  Genere los nuevos archivos de solución y proyecto. Si quiere generarlos ahora, en el menú principal del Editor de Unity, elija **Visual Studio Tools**, **Generar archivos de proyecto**. De lo contrario, puede omitir este paso si lo desea; Visual Studio Tools para Unity generará los nuevos archivos automáticamente al elegir **Visual Studio Tools**, **Abrir en Visual Studio**.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>En Windows, Visual Studio le pide que descargue la plataforma de destino Unity
 Visual Studio Tools para Unity requiere .NET Framework 3.5, que no está instalado de forma predeterminada en Windows 8 ni 10. Para corregir este problema, siga las instrucciones para descargar e instalar .NET Framework 3.5.

## <a name="known-issues"></a>Problemas conocidos
 Existen problemas conocidos en Visual Studio Tools para Unity que se deben a cómo interactúa el depurador con la antigua versión de Unity del compilador de C#. Estamos trabajando para ayudar a solucionar estos problemas, pero mientras tanto podría experimentar los siguientes problemas:

-   A veces, al depurar, Unity se bloquea.

-   A veces, al depurar, Unity se inmoviliza.

-   Al entrar y salir de métodos a veces se produce un comportamiento incorrecto, especialmente en iteradores o dentro de instrucciones switch.

## <a name="reporting-errors"></a>Notificar errores
 Ayúdenos a mejorar la calidad de Visual Studio Tools para Unity mediante el envío de informes de errores cuando experimente bloqueos, inmovilizaciones u otro tipo de errores. Esto nos ayudará a investigar y solucionar problemas en Visual Studio Tools para Unity. ¡Gracias!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Cómo informar de un error cuando Visual Studio se inmoviliza
 Hay informes que indican que a veces Visual Studio se inmoviliza al depurar con Visual Studio Tools para Unity, pero necesitamos más datos para comprender este problema. Puede ayudarnos a investigarlo siguiendo los pasos indicados a continuación.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Para informar de que Visual Studio se inmoviliza durante la depuración con Visual Studio Tools para Unity

*En Windows:*

1.  Abra una nueva instancia de Visual Studio.

2.  Abra el diálogo Asociar al proceso. En la nueva instancia de Visual Studio, en el menú principal, elija **Depurar**, **Asociar al proceso**.

3.  Asocie el depurador a la instancia inmovilizada de Visual Studio. En el diálogo **Asociar al proceso** , seleccione la instancia inmovilizada de Visual Studio en la tabla **Procesos disponibles** y, a continuación, elija el botón **Asociar** .

4.  Pause el Depurador. En el menú principal de la nueva instancia de Visual Studio, elija **Depurar**, **Interrumpir todo** o simplemente presione **Ctrl+Alt+Interrumpir**.

5.  Cree un volcado del subproceso. En la ventana Comandos, escriba el siguiente comando y presione **Entrar**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Puede que primero tenga que hacer visible la ventana **Comando** . En el menú principal de Visual Studio elija **Vista**, **Otras ventanas**, **Ventana Comandos**.

*En Mac:*

1. Abra un terminal y obtenga el PID de Visual Studio para Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Inicie el depurador LLDB:

    ```shell
    lldb
    ```

1. Asócielo a la instancia de Visual Studio para Mac con el PID:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Recupere el archivo stacktrace de todos los subprocesos:

    ```shell
    bt all
    ```

Por último, envíe el volcado del subproceso a [vstusp@microsoft.com](mailto:vstusp@microsoft.com), junto con una descripción de lo que estaba haciendo cuando Visual Studio se quedó inmovilizado.
