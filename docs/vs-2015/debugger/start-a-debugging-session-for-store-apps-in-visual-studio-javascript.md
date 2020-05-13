---
title: Iniciar una sesión de depuración para aplicaciones de la Tienda (JavaScript) Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b4e861c8985ee37a8c2d9b7f9286d6284bb4f91
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301384"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Iniciar una sesión de depuración para aplicaciones de la Tienda en Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone](.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 En este tema se describe cómo iniciar una sesión de depuración para las aplicaciones de la Tienda Windows compiladas en JavaScript y HTML5. Puede iniciar la depuración presionando una sola tecla o configurar la sesión de depuración para situaciones concretas y, a continuación, elegir el modo de iniciar la aplicación.

> [!NOTE]
> Para las aplicaciones que se escriben en XAML y Visual C, Visual C++ o Visual Basic, vea Iniciar una sesión de [depuración (VB, C, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a>En este tema
 [En este tema](#BKMK_In_this_topic)

 [Iniciar la depuración de manera sencilla](#BKMK_The_easy_way_to_start_debugging)

 [Configurar la sesión de depuración](#BKMK_Configure_the_debugging_session)

- [Abra la página de propiedades de depuración para el proyecto](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Elija las opciones de configuración de compilación](#BKMK_Choose_the_build_configuration_options)

- [Elija el destino de implementación](#BKMK_Choose_the_deployment_target)

- [Elegir el depurador utilizado](#BKMK_Choose_the_debugger_to_use)

- [(Opcional) Retrase el inicio de la aplicación en la sesión de depuración](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Opcional) Deshabilitar bucles de red](#BKMK__Optional__Disable_network_loopbacks)

  [Inicie la sesión de depuración](#BKMK_Start_the_debugging_session)

- [Iniciar la depuración (F5)](#BKMK_Start_debugging__F5_)

- [Iniciar la depuración (F5) pero retrasar el inicio de la aplicación](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Iniciar una aplicación instalada en el depurador](#BKMK_Start_an_installed_app_in_the_debugger)

  [Asocie el depurador a una aplicación en ejecución](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Establezca la aplicación para que se ejecute en modo de depuración](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Asociar el depurador](#BKMK_Attach_the_debugger)

## <a name="the-easy-way-to-start-debugging"></a><a name="BKMK_The_easy_way_to_start_debugging"></a>La manera fácil de iniciar la depuración
 ![Válido únicamente para Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Abre la solución de aplicación en Visual Studio.

2. Si la solución contiene proyectos para las aplicaciones de la Tienda Windows y de la Tienda de Windows Phone, asegúrese de que el proyecto que quiera depurar sea el proyecto de inicio. En Exploración de soluciones, seleccione el proyecto y, a continuación, elija **Establecer como proyecto de inicio** en el menú contextual.

3. Presione F5.

   ![Válido únicamente para Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio compila e inicia la aplicación con el depurador asociado. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza. Para obtener más información, consulte [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="configure-the-debugging-session"></a><a name="BKMK_Configure_the_debugging_session"></a>Configurar la sesión de depuración
 Dado que no se compila el script, no se aplicará la configuración de la compilación y de la plataforma. Si está depurando un Componente administrado o C++ , establezca **Configuración** en **Depurar** y elija la plataforma de destino en el cuadro de diálogo **Configuración.**

### <a name="open-the-debugging-property-page-for-the-project"></a><a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Abrir la página de propiedades de depuración del proyecto

1. En el Explorador de soluciones, seleccione el proyecto. Elige **Propiedades**en el menú contextual.

2. Expanda el nodo Propiedades de **configuración** y, a continuación, elija **Depuración**

### <a name="choose-the-build-configuration-options"></a><a name="BKMK_Choose_the_build_configuration_options"></a> Elegir las opciones de configuración de compilación

1. En la lista **Configuración** , elige **Debug** o **(Active) Debug**.

2. En la lista **Plataforma** elige la plataforma de destino para la que se va a compilar. En la mayoría de los casos, **cualquier CPU** es la mejor opción.

### <a name="choose-the-deployment-target"></a><a name="BKMK_Choose_the_deployment_target"></a> Elegir el destino de implementación
 Puede implementar y depurar una aplicación en el equipo de Visual Studio, en el simulador de Visual Studio del equipo local o en un equipo remoto. Elija el destino de la lista **Depurador para iniciar** en la página de propiedades **Depuración** del proyecto.

 ![Válido únicamente para Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Para una aplicación de la Tienda Windows, elige una de estas opciones en la lista Dispositivo de **destino:**

|||
|-|-|
|**Máquina local**|Depura la aplicación en la sesión actual en el equipo local. Consulte Ejecutar aplicaciones de [la Tienda Windows en el equipo local.](../debugger/run-windows-store-apps-on-the-local-machine.md)|
|**Simulador**|Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo (por ejemplo, gestos táctiles y de rotación de dispositivos) que no está disponible en el equipo local. Consulte Ejecutar aplicaciones de [la Tienda Windows en el simulador.](../debugger/run-windows-store-apps-in-the-simulator.md)|
|**Máquina remota**|Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las Herramientas remotas de Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Consulte Ejecutar aplicaciones de la [Tienda Windows en un equipo remoto.](../debugger/run-windows-store-apps-on-a-remote-machine.md)|

 Si eliges **Equipo remoto**, especifica el nombre o la dirección IP del equipo remoto de una de estas maneras:

- Escriba el nombre o la dirección IP de la máquina remota en el cuadro Nombre de **máquina.**

- Elija la flecha hacia abajo en el cuadro **Nombre** de máquina y elija ** \<Localizar...>**. A continuación, elija el equipo remoto en el cuadro de diálogo **Seleccionar conexión de depurador remoto.**

   ![Seleccionar conexión del depurador remoto](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > El cuadro de diálogo Seleccionar conexión del depurador remoto muestra los equipos que están en la subred local y los que están conectados directamente con el equipo de Visual Studio mediante un cable Ethernet. Para especificar otro equipo, escribe su nombre en el cuadro **Nombre de equipo** .

  ![Válido únicamente para Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Para una aplicación de Windows Store Phone, elija **Dispositivo** o uno de los emuladores en la lista Dispositivo de **destino.**

### <a name="choose-the-debugger-to-use"></a><a name="BKMK_Choose_the_debugger_to_use"></a>Elija el depurador que desea utilizar
 El depurador va asociado al código JavaScript de la aplicación de forma predeterminada. Puede depurar el código administrado y de C++ nativo de los componentes de la aplicación en lugar del código JavaScript. El código que se debe depurar se especifica en la lista **Tipo de depurador** de la página de propiedades de **Depuración** del proyecto de aplicación.

 Elija uno de estos depuradores de la lista Tipo de **depurador:**

|||
|-|-|
|**Solo script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|
|**Solo para nativos**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|
|**Código nativo con script**|Depure el código de C++ nativo y el código JavaScript de la aplicación.|
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript.|

### <a name="optional-delay-starting-the-app-in-the-debug-session"></a><a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Opcional) Retrasar el inicio de la aplicación en la sesión de depuración
 De forma predeterminada, Visual Studio inicia inmediatamente la aplicación cuando se iniciar la depuración. También puedes iniciar una sesión de depuración pero retrasar el inicio de la aplicación. La aplicación se inicia en el depurador cuando se inicia desde la pantalla Inicio o mediante un contrato de activación, o bien cuando la inicia otro proceso o método. También puede usar el inicio retrasado para depurar los eventos en segundo plano de la aplicación que quiera que se produzcan cuando la aplicación no se esté ejecutando.

 Especifique si desea retrasar el inicio de la aplicación en la lista **Iniciar aplicación** de la página de propiedades **Depuración** del proyecto de aplicación. Elija una de estas opciones:

- Elija **No** para retrasar el inicio de la aplicación.

- Elija **Sí** para iniciar la aplicación inmediatamente.

### <a name="optional-disable-network-loopbacks"></a><a name="BKMK__Optional__Disable_network_loopbacks"></a> (Opcional) Deshabilitar bucles invertidos de red
 ![Válido únicamente para Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Por razones de seguridad, a las aplicaciones de la Tienda Windows instaladas de la manera estándar en un dispositivo no se les permite realizar llamadas de red a ese dispositivo. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar tu aplicación a la Tienda Windows, debes probarla sin la exención.

 Para quitar la exención de bucle de reacción de red, elija **No** en la lista **Permitir bucle de recuperación** de red en la página de propiedades **Depuración.**

## <a name="start-the-debugging-session"></a><a name="BKMK_Start_the_debugging_session"></a> Iniciar la sesión de depuración

### <a name="start-debugging-f5"></a><a name="BKMK_Start_debugging__F5_"></a>Iniciar depuración (F5)
 Al elegir **Iniciar depuración** en el menú **Depurar** (teclado: F5), Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="start-debugging-f5-but-delay-the-app-start"></a><a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Inicie la depuración (F5) pero retrase el inicio de la aplicación
 Puede establecer que la aplicación se ejecute en modo de depuración, pero dejar que se inicie mediante un método que no sea el depurador. Por ejemplo, puedes depurar el inicio de tu aplicación desde el menú Inicio o depurar un proceso en segundo plano de la aplicación sin iniciarla. Si deseas retrasar el inicio de la aplicación, realiza lo siguiente:

1. En la página **Depurar** de las propiedades del proyecto de aplicación, elija **No** en la lista **Iniciar aplicación.**

2. Elija **Iniciar depuración** en el menú **Depurar** (Teclado: F5).

3. Inicia la aplicación desde el menú Inicio, un contrato de ejecución o mediante otro procedimiento.

   La aplicación se inicia en modo de depuración. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

   . Para obtener más información acerca de la depuración de tareas en segundo plano, vea desencadenar eventos de [suspensión, reanudación y en segundo plano para](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)la Tienda Windows).

## <a name="start-an-installed-app-in-the-debugger"></a><a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar una aplicación instalada en el depurador
 Si inicias la depuración utilizando F5, Visual Studio compila e implementa la aplicación, establece que la aplicación se ejecute en modo de depuración y, a continuación, la inicia. Para iniciar una aplicación que ya está instalada en un dispositivo, utiliza el cuadro de diálogo Depurar paquete de aplicaciones instalado. Este procedimiento es útil si necesitas depurar una aplicación instalada desde la Tienda Windows o si tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.

 La aplicación puede estar instalada en el dispositivo local o en un dispositivo remoto.  Puedes iniciar la aplicación inmediatamente o establecer que se ejecute en el depurador cuando se inicie mediante otro proceso o método, por ejemplo desde el menú Inicio o mediante un contrato de activación. También puedes establecer que la aplicación se ejecute en modo de depuración cuando desees depurar un proceso en segundo plano sin iniciar la aplicación. Para obtener más información, consulta [Desencadenar eventos de suspensión, reanudación y fondo para](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)la Tienda Windows).

 Para establecer que una aplicación instalada se ejecute en modo de depuración, realiza lo siguiente:

> [!NOTE]
> La aplicación no debe estar ejecutándose al iniciar este procedimiento.

1. En el menú **Depurar** , elige **Depurar paquete de aplicaciones instalado**

2. Elige una de las opciones siguientes de la lista:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Máquina local**  |                                                                                                                Depura la aplicación en la sesión actual en el equipo local. Consulte Ejecutar aplicaciones de [la Tienda Windows en el equipo local.](../debugger/run-windows-store-apps-on-the-local-machine.md)                                                                                                                 |
   |   **Simulador**    | Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo (por ejemplo, gestos táctiles y de rotación de dispositivos) que no está disponible en el equipo local. Consulte Ejecutar aplicaciones de [la Tienda Windows en el simulador.](../debugger/run-windows-store-apps-in-the-simulator.md) |
   | **Máquina remota** |                          Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las Herramientas remotas de Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Consulte Ejecutar aplicaciones de la [Tienda Windows en un equipo remoto.](../debugger/run-windows-store-apps-on-a-remote-machine.md)                           |

3. Elige la aplicación en la lista **Paquetes de aplicaciones instalados** .

4. Elige el motor de depuración que deseas usar en la lista **Depurar este tipo de código** .

5. (Opcional). Elige **No iniciar, pero depurar mi código al empezar** para depurar la aplicación cuando se inicie mediante otro método o para depurar un proceso en segundo plano.

   Cuando hagas clic en **Inicio**, la aplicación se iniciará o se establecerá que se ejecute en modo de depuración.

## <a name="attach-the-debugger-to-a-running-app"></a><a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar el depurador a una aplicación en ejecución
 Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las Herramientas remotas de Visual Studio.

 Asociar el depurador a una aplicación resulta útil si tiene que depurar una aplicación ya instalada, por ejemplo, que se haya instalado desde la Tienda Windows. Es necesario asociarlo cuando tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.

 Para asociar el depurador a una aplicación:

1. Establece la aplicación para que se ejecute en modo de depuración. Se tiene que hacer cuando la aplicación no se está ejecutando.

2. Inicie la aplicación. Puede iniciar la aplicación desde la pantalla Inicio, un contrato de ejecución o algún otro método.

3. Asocia el depurador a la aplicación en ejecución.

### <a name="set-the-app-to-run-in-debug-mode"></a><a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurar la aplicación para que se ejecute en modo de depuración

1. Instala las Herramientas remotas de Visual Studio en el dispositivo donde esté instalada la aplicación. Consulte [Instalación de las herramientas remotas](https://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. En la pantalla Inicio, busque `Debuggable Package Manager`. Inícielo.

     Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.

3. Para habilitar la depuración de una aplicación, debes especificar el identificador PackageFullName de la aplicación. Para ver una lista de todas las aplicaciones que incluyen PackageFullName, escribe `Get-AppxPackage` en el símbolo del sistema de PowerShell.

4. En el símbolo del sistema de PowerShell, especifique `Enable-AppxDebug` *PackageFullName* , donde *PackageFullName* es el identificador PackageFullName de la aplicación.

### <a name="attach-the-debugger"></a><a name="BKMK_Attach_the_debugger"></a>Adjuntar el depurador

> [!TIP]
> Las aplicaciones de JavaScript se ejecutan en una instancia del proceso wwahost.exe. Si hay otras aplicaciones de JavaScript ejecutándose durante la asociación, debe conocer el identificador numérico del proceso (PID) del proceso wwahost.exe en el que se ejecuta la aplicación.
>
> El modo más fácil de solucionarlo es cerrar las demás aplicaciones de JavaScript. De lo contrario, puede abrir el Administrador de tareas de Windows antes de iniciar la aplicación y apuntar los identificadores de los procesos wwahost.exe. Al especificar el proceso al que se va a adjuntar en el cuadro de diálogo **Procesos disponibles,** wwahost.exe de la aplicación tendrá un identificador que es diferente de los que ha observado.

 Para asociar el depurador:

1. En el menú **Depurar** , elija **Asociar al proceso**.

    Aparecerá el cuadro de diálogo **Asociar al proceso** .

2. Para asociarlo a una aplicación de un dispositivo remoto, especifícalo en el cuadro **Calificador** . Puede:

   - Escribir el nombre en el cuadro **Calificador** .

   - Elija la flecha abajo en el cuadro **Calificador** y elija el dispositivo de una lista de dispositivos a los que se ha conectado antes.

   - Elija **Buscar** para elegir el dispositivo de una lista de dispositivos de la subred local.

3. Especifica el tipo de código que deseas depurar en el cuadro **Asociar a** .

    Elige **Seleccionar** y realiza una de las siguientes operaciones:

   - Elige **Determinar automáticamente el tipo de código para depurar**.

   - Elige **Depurar estos tipos de código** y seleccionar uno o más tipos de la lista.

4. En la lista **Procesos disponibles,** elija el proceso **wwahost.exe** adecuado. Use la columna **Título** para identificar la aplicación.

5. Elija **Asociar**.

   Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

## <a name="see-also"></a>Consulte también
 Controlar la ejecución en una sesión de [depuración (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md) Trigger suspender, reanudar y eventos en segundo plano para la Tienda [Windows)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [Depurar aplicaciones de depuración en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
