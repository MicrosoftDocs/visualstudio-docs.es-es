---
title: Solución de problemas y problemas conocidos (Visual Studio Tools para Unity) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 1c69c78e9a081680c6ee5279ddce1816bf500672
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027294"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Solución de problemas y problemas conocidos (Visual Studio Tools para Unity)

En esta sección encontrará soluciones a problemas comunes con Visual Studio Tools para Unity y descripciones de problemas conocidos. Asimismo descubrirá cómo puede ayudar a mejorar Visual Studio Tools para Unity mediante la notificación de errores.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Solución de problemas de conexión entre Unity y Visual Studio

### <a name="confirm-editor-attaching-is-enabled"></a>Confirmar que Editor Attaching está habilitado

En el menú de Unity, seleccione **Edit > Preferences** (Edit > Preferencias) y luego seleccione la pestaña **External Tools** (Herramientas externas). Confirme que la casilla **Editor Attaching** esté habilitada. Para más información, consulte la [documentación sobre las preferencias de Unity](https://docs.unity3d.com/Manual/Preferences.html).

### <a name="unable-to-attach"></a>Imposibilidad de efectuar la asociación

- Intente deshabilitar temporalmente el antivirus o cree reglas de exclusión para VS y Unity.
- Intente deshabilitar temporalmente el firewall o cree reglas que permitan redes TCP/UDP entre VS y Unity.
- Algunos programas como TeamViewer, pueden interferir con la detección de procesos. Puede intentar detener temporalmente cualquier software adicional para ver si cambia algo.
- No cambie el nombre del archivo ejecutable principal de Unity, ya que VSTU solo supervisa procesos con el nombre "Unity.exe".

## <a name="visual-studio-crashes"></a>Bloqueo de Visual Studio

Este problema puede deberse a que la caché de MEF de Visual Studio está dañada.

Intente quitar la carpeta siguiente para restablecer la caché de MEF (cierre Visual Studio antes de hacerlo):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Esto debería resolver el problema. En caso de que siga experimentando el problema, ejecute un símbolo del sistema para desarrolladores de Visual Studio como administrador y use el comando siguiente:

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio deja de responder

Varios complementos de Unity, por ejemplo, Parse, FMOD, UMP (Universal Media Player), ZFBrowser o Embedded Browser usan subprocesos nativos. Resulta problemático cuando un complemento acaba de asociar un subproceso nativo al runtime, que luego realiza llamadas de bloqueo al sistema operativo. Esto significa que Unity no puede interrumpir ese subproceso del depurador (o recarga del dominio) y deja de responder.

En el caso de FMOD hay una solución alternativa, puede pasar la [marca](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) de inicialización `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` para deshabilitar el procesamiento asincrónico y realizar todo el procesamiento en el subproceso principal.

## <a name="incompatible-project-in-visual-studio"></a>Proyecto no compatible en Visual Studio

En primer lugar, compruebe que Visual Studio está establecido como editor de scripts externo en Unity (Editar/Preferencias/Herramientas externas). Después, compruebe que el complemento de Visual Studio está instalado en Unity ("Ayuda/Acerca de" debe mostrar en la parte inferior un mensaje como Microsoft Visual Studio Tools para Unity está habilitado). Después, compruebe que la extensión está instalada correctamente en Visual Studio (Ayuda/Acerca de).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Recargas adicionales o pérdida de todas las ventanas abiertas de Visual Studio

No toque nunca los archivos de proyecto directamente desde un procesador de recursos o cualquier otra herramienta. Si realmente necesita manipular el archivo de proyecto, hay una API para hacerlo. Consulte la [sección Problemas de referencias de ensamblado](#Assembly-reference-issues).

Si se producen recargas adicionales o si Visual Studio pierde todas las ventanas abiertas al realizar una recarga, asegúrese de que dispone de los paquetes de compatibilidad de .NET apropiados. Consulte la sección siguiente sobre marcos de trabajo para más información.

## <a name="the-debugger-does-not-break-on-exceptions"></a>El depurador no provoca una interrupción ante excepciones

Cuando se utiliza el runtime heredado de Unity (equivalente a .NET 3.5), el depurador siempre provocará una interrupción cuando una excepción no esté controlada (= fuera de un bloque try/catch). Si se controla la excepción, el depurador se basará en la ventana de configuración de excepciones para determinar si es necesaria una interrupción.

Con el nuevo runtime (equivalente a .NET 4.6), Unity introdujo una manera nueva de administrar las excepciones de usuario y, como resultado, todas las excepciones se consideran "controladas por el usuario" aunque estén fuera de un bloque try/catch. Por eso ahora hay que marcarlas explícitamente en la ventana de configuración de excepciones si se quiere que el depurador provoque una interrupción.

En la ventana Configuración de excepciones (Depurar > Ventanas > Configuración de excepciones), expanda el nodo de una categoría de excepciones (por ejemplo, Excepciones de Common Language Runtime, es decir, las excepciones. NET) y active la casilla de una excepción concreta que quiera capturar en esa categoría (por ejemplo System.NullReferenceException). También puede seleccionar una categoría de excepciones completa.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>En Windows, Visual Studio le pide que descargue la plataforma de destino Unity

Visual Studio Tools para Unity requiere .NET Framework 3.5, que no está instalado de forma predeterminada en Windows 8 ni 10. Para corregir este problema, siga las instrucciones para descargar e instalar .NET Framework 3.5.

Cuando se utiliza el nuevo runtime de Unity, también son necesarios los paquetes de compatibilidad de .NET en sus versiones 4.6 y 4.7.1. Es posible usar el programa de instalación de VS2017 para instalarlos rápidamente (modifique la instalación de VS2017, busque los componentes individuales, categoría. NET, y seleccione todos los paquetes de compatibilidad 4.x).

## <a name="assembly-reference-issues"></a>Problemas de referencias de ensamblado

Si el proyecto incluye referencias complejas o si se quiere controlar mejor este paso de generación, se puede usar nuestra [API](../cross-platform/customize-project-files-created-by-vstu.md) para manipular el contenido de la solución o el proyecto que se genera. También puede usar [archivos de respuesta](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) en el proyecto de Unity y los procesaremos.

## <a name="breakpoints-with-a-warning"></a>Puntos de interrupción con advertencia

Si Visual Studio no encuentra una ubicación de origen para un punto de interrupción concreto, aparecerá una advertencia en el punto de interrupción. Compruebe que el script que usa está cargado y se emplea correctamente en la escena actual de Unity.

## <a name="breakpoints-not-hit"></a>Puntos de interrupción no ejecutados

Compruebe que el script que usa está cargado y se emplea correctamente en la escena actual de Unity. Salga de Visual Studio y Unity y elimine todos los archivos generados (\*.csproj, \*.sln) y la carpeta Library completa.

## <a name="unable-to-debug-android-players"></a>Imposibilidad de depurar reproductores de Android

La multidifusión se usa para la detección de reproductores (que es el mecanismo predeterminado que usa Unity), pero después se usa una conexión TCP normal para asociar el depurador. La fase de detección es el principal problema con dispositivos Android.

Wi-Fi es versátil, pero no ofrece la misma velocidad en comparación con USB debido a la latencia. Hemos visto una falta de compatibilidad de multidifusión adecuada en algunos enrutadores o dispositivos (por ejemplo, el caso de las series de Nexus).

Con USB se agiliza mucho la depuración, y Visual Studio Tools para Unity es ahora capaz de detectar dispositivos USB y comunicarse con el servidor adb para reenviar correctamente los puertos en la depuración.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Problemas de Visual Studio 2015 e IntelliSense, o de colores de código

Intente actualizar Visual Studio 2015 a Update 3.

## <a name="known-issues"></a>Problemas conocidos

 Existen problemas conocidos en Visual Studio Tools para Unity que se deben a cómo interactúa el depurador con la antigua versión de Unity del compilador de C#. Estamos trabajando para ayudar a solucionar estos problemas, pero mientras tanto podría experimentar los siguientes problemas:

- A veces, al depurar, Unity se bloquea.

- A veces, al depurar, Unity se inmoviliza.

- Al entrar y salir de métodos a veces se produce un comportamiento incorrecto, especialmente en iteradores o dentro de instrucciones switch.

## <a name="report-errors"></a>Errores de informes

 Ayúdenos a mejorar la calidad de Visual Studio Tools para Unity mediante el envío de informes de errores cuando experimente bloqueos, inmovilizaciones u otro tipo de errores. Esto nos ayudará a investigar y solucionar problemas en Visual Studio Tools para Unity. ¡Gracias!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Cómo informar de un error cuando Visual Studio se inmoviliza

 Hay informes que indican que a veces Visual Studio se inmoviliza al depurar con Visual Studio Tools para Unity, pero necesitamos más datos para comprender este problema. Puede ayudarnos a investigarlo siguiendo los pasos indicados a continuación.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Para informar de que Visual Studio se inmoviliza durante la depuración con Visual Studio Tools para Unity

*En Windows:*

1. Abra una nueva instancia de Visual Studio.

1. Abra el diálogo Asociar al proceso. En la nueva instancia de Visual Studio, en el menú principal, elija **Depurar**, **Asociar al proceso**.

1. Asocie el depurador a la instancia inmovilizada de Visual Studio. En el diálogo **Asociar al proceso** , seleccione la instancia inmovilizada de Visual Studio en la tabla **Procesos disponibles** y, a continuación, elija el botón **Asociar** .

1. Pause el Depurador. En el menú principal de la nueva instancia de Visual Studio, elija **Depurar**, **Interrumpir todo** o simplemente presione **Ctrl+Alt+Interrumpir**.

1. Cree un volcado del subproceso. En la ventana Comandos, escriba el siguiente comando y presione **Entrar**:

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
