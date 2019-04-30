---
title: Iniciar una sesión de depuración para aplicaciones de Store (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 630b2896e7446cf62982dd62ed12f9f7b7ca4aa9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427299"
---
# <a name="start-a-debugging-session-for-store-apps-in-visual-studio-javascript"></a>Iniciar una sesión de depuración para aplicaciones de la Tienda en Visual Studio (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se aplica a Windows y Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 En este tema se describe cómo iniciar una sesión de depuración para las aplicaciones de la Tienda Windows compiladas en JavaScript y HTML5. Puede iniciar la depuración presionando una sola tecla o configurar la sesión de depuración para situaciones concretas y, a continuación, elegir el modo de iniciar la aplicación.

> [!NOTE]
> Para las aplicaciones escritas en XAML y Visual C#, Visual C++ o Visual Basic, vea [iniciar una sesión de depuración (VB, C#, C++ y XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="BKMK_In_this_topic"></a> En este tema
 [En este tema](#BKMK_In_this_topic)

 [Iniciar la depuración de manera sencilla](#BKMK_The_easy_way_to_start_debugging)

 [Configurar la sesión de depuración](#BKMK_Configure_the_debugging_session)

- [Abrir la página de propiedades de depuración del proyecto](#BKMK_Open_the_debugging_property_page_for_the_project)

- [Elegir las opciones de configuración de compilación](#BKMK_Choose_the_build_configuration_options)

- [Elegir el destino de implementación](#BKMK_Choose_the_deployment_target)

- [Elegir el depurador utilizado](#BKMK_Choose_the_debugger_to_use)

- [(Opcional) Retrasar el inicio de la aplicación en la sesión de depuración](#BKMK__Optional__Delay_starting_app_in_the_debug_session)

- [(Opcional) Deshabilitar bucles invertidos de red](#BKMK__Optional__Disable_network_loopbacks)

  [Iniciar la sesión de depuración](#BKMK_Start_the_debugging_session)

- [Iniciar la depuración (F5)](#BKMK_Start_debugging__F5_)

- [Iniciar la depuración (F5) pero retrasar el inicio de la aplicación](#BKMK_Start_debugging__F5__but_delay_the_app_start)

  [Iniciar una aplicación instalada en el depurador](#BKMK_Start_an_installed_app_in_the_debugger)

  [Asociar el depurador a una aplicación en ejecución](#BKMK_Attach_the_debugger_to_a_running_app_)

- [Configurar la aplicación para que se ejecute en modo de depuración](#BKMK_Set_the_app_to_run_in_debug_mode)

- [Asociar el depurador](#BKMK_Attach_the_debugger)

## <a name="BKMK_The_easy_way_to_start_debugging"></a> Iniciar la depuración de manera sencilla
 ![Solo se aplica a Windows](../debugger/media/windows-only-content.png "windows_only_content")

1. Abre la solución de aplicación en Visual Studio.

2. Si la solución contiene proyectos para las aplicaciones de la Tienda Windows y de la Tienda de Windows Phone, asegúrese de que el proyecto que quiera depurar sea el proyecto de inicio. En el Explorador de soluciones, seleccione el proyecto y, a continuación, elija **establecer como proyecto de inicio** en el menú contextual.

3. Presione F5.

   ![Solo se aplica a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

   Visual Studio compila e inicia la aplicación con el depurador asociado. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza. Para obtener más información, vea [Inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md).

## <a name="BKMK_Configure_the_debugging_session"></a> Configurar la sesión de depuración
 Dado que no se compila el script, no se aplicará la configuración de la compilación y de la plataforma. Si está depurando un componente administrado o C++, establezca el **configuración** a **depurar** y elija la plataforma de destino desde el **configuración** cuadro de diálogo.

### <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a> Abrir la página de propiedades de depuración del proyecto

1. En el Explorador de soluciones, seleccione el proyecto. Elige **Propiedades**en el menú contextual.

2. Expanda el **propiedades de configuración** nodo y, a continuación, elija **depuración**

### <a name="BKMK_Choose_the_build_configuration_options"></a> Elegir las opciones de configuración de compilación

1. En la lista **Configuración** , elige **Debug** o **(Active) Debug**.

2. En la lista **Plataforma** elige la plataforma de destino para la que se va a compilar. En la mayoría de los casos, **cualquier CPU** es la mejor opción.

### <a name="BKMK_Choose_the_deployment_target"></a> Elegir el destino de implementación
 Puede implementar y depurar una aplicación en el equipo de Visual Studio, en el simulador de Visual Studio del equipo local o en un equipo remoto. Seleccione el destino de la **depurador para iniciar** lista el **depuración** página de propiedades del proyecto.

 ![Solo se aplica a Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Para una aplicación de Windows Store, elija una de estas opciones desde el **dispositivo de destino** lista:

|||
|-|-|
|**Equipo local**|Depura la aplicación en la sesión actual en el equipo local. Consulte [ejecución Windows Store apps en el equipo local](../debugger/run-windows-store-apps-on-the-local-machine.md).|
|**Simulador**|Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo (por ejemplo, gestos táctiles y de rotación de dispositivos) que no está disponible en el equipo local. Consulte [ejecución Windows Store apps en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|
|**Equipo remoto**|Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las Herramientas remotas de Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Consulte [ejecución Windows Store apps en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|

 Si eliges **Equipo remoto**, especifica el nombre o la dirección IP del equipo remoto de una de estas maneras:

- Escriba el nombre o dirección IP del equipo remoto en el **nombre de la máquina** cuadro.

- Elija la flecha hacia abajo en la **nombre de la máquina** y elija  **\<buscar... >**. A continuación, elija el equipo remoto desde **Seleccionar conexión del depurador remoto** cuadro de diálogo.

   ![Seleccionar conexión del depurador remoto](../debugger/media/vsrun-pro-selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")

  > [!NOTE]
  > El cuadro de diálogo Seleccionar conexión del depurador remoto muestra los equipos que están en la subred local y los que están conectados directamente con el equipo de Visual Studio mediante un cable Ethernet. Para especificar otro equipo, escribe su nombre en el cuadro **Nombre de equipo** .

  ![Solo se aplica a Windows Phone](../debugger/media/phone-only-content.png "phone_only_content")

  Para una aplicación de teléfono de Windows Store, elija **dispositivo** o uno de los emuladores de la **dispositivo de destino** lista.

### <a name="BKMK_Choose_the_debugger_to_use"></a> Elegir el depurador utilizado
 El depurador va asociado al código JavaScript de la aplicación de forma predeterminada. Puede depurar el código administrado y de C++ nativo de los componentes de la aplicación en lugar del código JavaScript. El código que se debe depurar se especifica en la lista **Tipo de depurador** de la página de propiedades de **Depuración** del proyecto de aplicación.

 Elija uno de estos depuradores en la **tipo de depurador** lista:

|||
|-|-|
|**Solo script**|Depura el código JavaScript de la aplicación. Se omiten el código administrado y el nativo.|
|**Solo nativo**|Depura el código C/C++ nativo de la aplicación. Se omiten el código administrado y el de JavaScript.|
|**Código nativo con script**|Depure el código de C++ nativo y el código JavaScript de la aplicación.|
|**Solo administrado**|Depura el código administrado de la aplicación. Se omiten el código de JavaScript y el de C/C++ nativo.|
|**Mixto (administrado y nativo)**|Depura el código de C/C++ nativo y el código administrado de la aplicación. Se omite el código de JavaScript.|

### <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a> (Opcional) Retrasar el inicio de la aplicación en la sesión de depuración
 De forma predeterminada, Visual Studio inicia inmediatamente la aplicación cuando se iniciar la depuración. También puedes iniciar una sesión de depuración pero retrasar el inicio de la aplicación. La aplicación se inicia en el depurador cuando se inicia desde la pantalla Inicio o mediante un contrato de activación, o bien cuando la inicia otro proceso o método. También puede usar el inicio retrasado para depurar los eventos en segundo plano de la aplicación que quiera que se produzcan cuando la aplicación no se esté ejecutando.

 Especifique si desea retrasar el inicio de la aplicación en el **Iniciar aplicación** lista el **depuración** página de propiedades del proyecto de aplicación. Elige una de estas opciones:

- Elija **No** para retrasar el inicio de la aplicación.

- Elija **Sí** para iniciar la aplicación inmediatamente.

### <a name="BKMK__Optional__Disable_network_loopbacks"></a> (Opcional) Deshabilitar bucles invertidos de red
 ![Solo se aplica a Windows](../debugger/media/windows-only-content.png "windows_only_content")

 Por razones de seguridad, a las aplicaciones de la Tienda Windows instaladas de la manera estándar en un dispositivo no se les permite realizar llamadas de red a ese dispositivo. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar tu aplicación a la Tienda Windows, debes probarla sin la exención.

 Para quitar la exención de bucle invertido de red, elija **No** desde el **permitir bucle invertido de red** lista el **depuración** página de propiedades.

## <a name="BKMK_Start_the_debugging_session"></a> Iniciar la sesión de depuración

### <a name="BKMK_Start_debugging__F5_"></a> Iniciar la depuración (F5)
 Cuando se elige **Iniciar depuración** en el **depurar** menú (teclado: F5), Visual Studio inicia la aplicación con el depurador adjunto. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

### <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a> Iniciar la depuración (F5) pero retrasar el inicio de la aplicación
 Puede establecer que la aplicación se ejecute en modo de depuración, pero dejar que se inicie mediante un método que no sea el depurador. Por ejemplo, puedes depurar el inicio de tu aplicación desde el menú Inicio o depurar un proceso en segundo plano de la aplicación sin iniciarla. Si deseas retrasar el inicio de la aplicación, realiza lo siguiente:

1. En el **depurar** página de la aplicación de las propiedades del proyecto, elija **No** desde el **Iniciar aplicación** lista.

2. Elija **Iniciar depuración** en el **depurar** menú (teclado: F5).

3. Inicia la aplicación desde el menú Inicio, un contrato de ejecución o mediante otro procedimiento.

   La aplicación se inicia en modo de depuración. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

   . Para obtener más información sobre la depuración de tareas en segundo plano, vea [desencadenador suspender, reanudar y en segundo plano de eventos para Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

## <a name="BKMK_Start_an_installed_app_in_the_debugger"></a> Iniciar una aplicación instalada en el depurador
 Si inicias la depuración utilizando F5, Visual Studio compila e implementa la aplicación, establece que la aplicación se ejecute en modo de depuración y, a continuación, la inicia. Para iniciar una aplicación que ya está instalada en un dispositivo, utiliza el cuadro de diálogo Depurar paquete de aplicaciones instalado. Este procedimiento es útil si necesitas depurar una aplicación instalada desde la Tienda Windows o si tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.

 La aplicación puede estar instalada en el dispositivo local o en un dispositivo remoto.  Puedes iniciar la aplicación inmediatamente o establecer que se ejecute en el depurador cuando se inicie mediante otro proceso o método, por ejemplo desde el menú Inicio o mediante un contrato de activación. También puedes establecer que la aplicación se ejecute en modo de depuración cuando desees depurar un proceso en segundo plano sin iniciar la aplicación. Para obtener más información, consulte [desencadenador suspender, reanudar y en segundo plano de eventos para Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).

 Para establecer que una aplicación instalada se ejecute en modo de depuración, realiza lo siguiente:

> [!NOTE]
> La aplicación no debe estar ejecutándose al iniciar este procedimiento.

1. En el menú **Depurar** , elige **Depurar paquete de aplicaciones instalado**

2. Elige una de las opciones siguientes de la lista:

   |                    |                                                                                                                                                                                                                                                                                                                                                                                                           |
   |--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **Equipo local**  |                                                                                                                Depura la aplicación en la sesión actual en el equipo local. Consulte [ejecución Windows Store apps en el equipo local](../debugger/run-windows-store-apps-on-the-local-machine.md).                                                                                                                 |
   |   **Simulador**    | Depura la aplicación en el simulador de Visual Studio para aplicaciones de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] . El simulador es una ventana del escritorio que te permite depurar la funcionalidad del dispositivo (por ejemplo, gestos táctiles y de rotación de dispositivos) que no está disponible en el equipo local. Consulte [ejecución Windows Store apps en el simulador](../debugger/run-windows-store-apps-in-the-simulator.md). |
   | **Equipo remoto** |                          Depura la aplicación en un dispositivo que esté conectado al equipo local a través de la intranet o directamente mediante un cable Ethernet. Para depurar remotamente, las Herramientas remotas de Visual Studio deben estar instaladas y ejecutándose en el dispositivo remoto. Consulte [ejecución Windows Store apps en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).                           |

3. Elige la aplicación en la lista **Paquetes de aplicaciones instalados** .

4. Elige el motor de depuración que deseas usar en la lista **Depurar este tipo de código** .

5. (Opcional). Elige **No iniciar, pero depurar mi código al empezar** para depurar la aplicación cuando se inicie mediante otro método o para depurar un proceso en segundo plano.

   Cuando hagas clic en **Inicio**, la aplicación se iniciará o se establecerá que se ejecute en modo de depuración.

## <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a> Asociar el depurador a una aplicación en ejecución
 Si quieres asociar el depurador a una aplicación de la [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] , debes utilizar el Administrador de paquetes depurables para establecer la aplicación de modo que se ejecute en modo de depuración. El Administrador de paquetes depurables se instala con las Herramientas remotas de Visual Studio.

 Asociar el depurador a una aplicación resulta útil si tiene que depurar una aplicación ya instalada, por ejemplo, que se haya instalado desde la Tienda Windows. Es necesario asociarlo cuando tienes los archivos de origen de la aplicación pero no tienes un proyecto de Visual Studio para ella. Por ejemplo, puede que tengas un sistema de compilación personalizado que no utilice proyectos o soluciones de Visual Studio.

 Para asociar el depurador a una aplicación:

1. Establece la aplicación para que se ejecute en modo de depuración. Se tiene que hacer cuando la aplicación no se está ejecutando.

2. Inicia la aplicación. Puede iniciar la aplicación desde la pantalla Inicio, un contrato de ejecución o algún otro método.

3. Asocia el depurador a la aplicación en ejecución.

### <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a> Configurar la aplicación para que se ejecute en modo de depuración

1. Instala las Herramientas remotas de Visual Studio en el dispositivo donde esté instalada la aplicación. Consulte [instalar las herramientas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).

2. En la pantalla Inicio, busque `Debuggable Package Manager`. Inícielo.

     Se abre una ventana de PowerShell configurada correctamente para cmdlet AppxDebug.

3. Para habilitar la depuración de una aplicación, debes especificar el identificador PackageFullName de la aplicación. Para ver una lista de todas las aplicaciones que incluyen PackageFullName, escribe `Get-AppxPackage` en el símbolo del sistema de PowerShell.

4. En el símbolo del sistema de PowerShell, especifique `Enable-AppxDebug` *PackageFullName* , donde *PackageFullName* es el identificador PackageFullName de la aplicación.

### <a name="BKMK_Attach_the_debugger"></a> Asociar el depurador

> [!TIP]
> Las aplicaciones de JavaScript se ejecutan en una instancia del proceso wwahost.exe. Si hay otras aplicaciones de JavaScript ejecutándose durante la asociación, debe conocer el identificador numérico del proceso (PID) del proceso wwahost.exe en el que se ejecuta la aplicación.
>
> El modo más fácil de solucionarlo es cerrar las demás aplicaciones de JavaScript. De lo contrario, puede abrir el Administrador de tareas de Windows antes de iniciar la aplicación y apuntar los identificadores de los procesos wwahost.exe. Al especificar el proceso de asociación en el **procesos disponibles** cuadro de diálogo, wwahost.exe de la aplicación tendrá un identificador que es diferente de los que haya anotado.

 Para asociar el depurador:

1. En el menú **Depurar** , elija **Asociar al proceso**.

    Aparecerá el cuadro de diálogo **Asociar al proceso** .

2. Para asociarlo a una aplicación de un dispositivo remoto, especifícalo en el cuadro **Calificador** . Puede realizar lo siguiente:

   - Escribir el nombre en el cuadro **Calificador** .

   - Elija la flecha hacia abajo en la **calificador** cuadro y elegir el dispositivo en una lista de dispositivos asociados a antes.

   - Elija **buscar** para elegir el dispositivo en una lista de dispositivos de la subred local.

3. Especifica el tipo de código que deseas depurar en el cuadro **Asociar a** .

    Elige **Seleccionar** y realiza una de las siguientes operaciones:

   - Elige **Determinar automáticamente el tipo de código para depurar**.

   - Elige **Depurar estos tipos de código** y seleccionar uno o más tipos de la lista.

4. En el **procesos disponibles** lista, elija el **wwahost.exe** proceso. Use la **título** columna para identificar la aplicación.

5. Elija **Asociar**.

   Visual Studio asocia el depurador al proceso. La ejecución continúa hasta que se alcanza un punto de interrupción, se suspende manualmente la ejecución, se produce una excepción no controlada o la aplicación finaliza.

## <a name="see-also"></a>Vea también
 [Controlar la ejecución en una sesión de depuración (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md) [inicio rápido: Depurar HTML y CSS](../debugger/quickstart-debug-html-and-css.md) [desencadenador suspender, reanudar y en segundo plano de eventos para Windows Store)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md) [depurar aplicaciones en Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)
