---
title: Depuración de una máquina virtual o un servicio en la nube de Azure
description: Depurar un servicio en la nube o una máquina virtual en Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: 2185641d5e3f9facf416e6ea999a1e8dcec0b37b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294200"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Depuración de una máquina virtual o un servicio en la nube de Azure en Visual Studio

Visual Studio proporciona distintas opciones para la depuración de servicios en la nube y máquinas virtuales de Azure.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Depuración del servicio en la nube en el equipo local

Puede ahorrar tiempo y dinero si utiliza el emulador de proceso de Azure para depurar su servicio en la nube en un equipo local. La depuración de un servicio localmente antes de su implementación puede mejorar la fiabilidad y el rendimiento sin pagar por tiempo de proceso. No obstante, pueden producirse algunos errores solo al ejecutar un servicio en la nube en el propio Azure. Puede depurar estos errores si habilita la depuración remota al publicar el servicio y luego adjuntar el depurador a una instancia de rol.

El emulador simula el servicio Azure Compute y se ejecuta en el entorno local para que pueda probar y depurar el servicio en la nube antes de implementarlo. El emulador administra el ciclo de vida de sus instancias de rol y proporciona acceso a recursos simulados, tales como el almacenamiento local. Al depurar o ejecutar el servicio desde Visual Studio, este entorno inicia automáticamente el emulador como una aplicación en segundo plano y después implementa el servicio en el emulador. Puede utilizar el emulador para ver su servicio cuando se ejecuta en el entorno local. Puede ejecutar la versión completa o la versión Express del emulador. (Starting with Azure 2.3, the express version of the emulator is the default.) See [Using Emulator Express to Run and Debug a Cloud Service Locally](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Para depurar el servicio en la nube en el equipo local

1. En la barra de menús, elija **Depurar**, **Iniciar depuración** para ejecutar el proyecto de servicio en la nube de Azure. Como alternativa, puede presionar F5. Verá un mensaje que indica que el emulador de proceso se está iniciando. Cuando se inicia el emulador, el icono de bandeja del sistema lo confirma.

    ![Emulador de Azure en la bandeja del sistema](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Visualice la interfaz de usuario del emulador de proceso; para ello, abra el menú contextual del icono de Azure en el área de notificación y haga clic en **Show Compute Emulator UI**(Mostrar la UI del emulador de proceso).

    El panel izquierdo de la interfaz de usuario muestra los servicios implementados actualmente en el emulador de proceso y las instancias de rol que cada servicio ejecuta. Puede elegir el servicio o los roles para mostrar información sobre el ciclo de vida, el registro y el diagnóstico en el panel derecho. Si coloca el foco en el margen superior de una ventana incluida, se expande para rellenar el recuadro derecho.

3. Recorra la aplicación: seleccione los comandos del menú **Depurar** y establezca puntos de interrupción en el código. A medida que recorre la aplicación en el depurador, los paneles se actualizan con el estado actual de la aplicación. Cuando se detiene la depuración, se elimina la implementación de aplicaciones. Si la aplicación incluye un rol web y ha establecido la propiedad acción de inicio para iniciar el explorador web, Visual Studio inicia la aplicación web en el explorador. Si cambia el número de instancias de un rol en la configuración del servicio, debe detener el servicio en la nube y, luego, reinicie la depuración para que pueda depurar estas nuevas instancias del rol.

    > [!NOTE]
    > cuando se deja de ejecutar o depurar el servicio, el emulador de proceso y el emulador de almacenamiento locales no se detienen. Debe detenerlos explícitamente en el área de notificación.

## <a name="debug-a-cloud-service-in-azure"></a>Depuración de un servicio en la nube en Azure

Para depurar un servicio en la nube desde un equipo remoto, debe habilitar esta funcionalidad de forma explícita cuando implemente su servicio en la nube para que los servicios requeridos (como msvsmon.exe) se instalen en las máquinas virtuales que ejecutan sus instancias de rol. Si no habilitó la depuración remota al publicar el servicio, deberá volver a publicar el servicio con la depuración remota habilitada.

Si habilita la depuración remota para un servicio en la nube, este no mostrará un rendimiento inferior ni incurrirá en cargos adicionales. No use la depuración remota en un servicio de producción, porque podría perjudicar a los clientes que usan el servicio.

> [!NOTE]
> Al publicar un servicio en la nube en Visual Studio, puede habilitar **IntelliTrace** para los roles de ese servicio cuyo destino sea .NET Framework 4 o .NET Framework 4.5. Con **IntelliTrace**, puede examinar eventos que se produjeron en una instancia de rol en el pasado y reproducir el contexto a partir de ese momento. Consulte [Depuración con IntelliTrace y Visual Studio de un servicio en la nube publicado](https://go.microsoft.com/fwlink/?LinkID=623016) y [Uso de IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Para habilitar la depuración remota para un servicio en la nube

1. Abra el menú contextual del proyecto de Azure y seleccione **Publicar**.

2. Seleccione el entorno de **ensayo** y la configuración de **depuración**.

    Esto es solo de referencia. Puede optar por ejecutar sus entornos de prueba en un entorno de producción. No obstante, puede perjudicar a los usuarios si habilita la depuración remota en el entorno de producción. Puede seleccionar la configuración Liberar, pero la configuración Depurar simplifica la depuración.

    ![Elegir la configuración Depurar](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Siga los pasos habituales pero active la casilla **Habilitar depurador remoto para todos los roles** de la pestaña **Configuración avanzada**.

    ![Configuración de depuración](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Para asociar el depurador a un servicio en la nube en Azure

1. En el Explorador de servidores, expanda el nodo del servicio en la nube.

2. Abra el menú contextual del rol o la instancia de rol a los que quiera asociarlo y luego seleccione **Asociar depurador**.

    Si depura un rol, el depurador de Visual Studio se asociará a cada instancia de dicho rol. El depurador se interrumpirá en un punto de interrupción para la primera instancia de rol que ejecute esta línea de código y cumpla las condiciones de dicho punto de interrupción. Si depura una instancia, el depurador solo se asociará a dicha instancia y se interrumpirá en un punto de interrupción solamente cuando esa instancia específica ejecute esa línea de código y cumpla las condiciones del punto de interrupción.

    ![Asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Después de que el depurador se asocie a una instancia, realice la depuración de la forma habitual. El depurador se asocia automáticamente al proceso de host adecuado del rol. En función del tipo de rol, el depurador se asocia a w3wp.exe, WaWorkerHost.exe o WaIISHost.exe. Para comprobar el proceso al que se ha asociado el depurador, expanda el nodo de la instancia en el Explorador de servidores. Consulte [Arquitectura de roles de Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) para más información sobre los procesos de Azure.

    ![Seleccionar el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Para identificar los procesos a los que se ha adjuntado el depurador, abra el cuadro de diálogo Procesos. Para ello, en la barra de menús, seleccione Depurar, Windows, Procesos. (Keyboard: Ctrl+Alt+Z) To detach a specific process, open its shortcut menu, and then select **Detach Process**. También puede localizar el nodo de la instancia en el Explorador de servidores, buscar el proceso, abrir su menú contextual y seleccione **Desasociar proceso**.

    ![Depurar procesos](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Evite detenciones prolongadas en los puntos de interrupción durante la depuración remota. Azure trata un proceso que se detiene durante algo más que unos minutos como si hubiese dejado de responder y detiene el envío de tráfico a dicha instancia. Si efectúa una detención demasiado prolongada, msvsmon.exe se separará del proceso.

Para separar el depurador de todos los procesos de su instancia o rol, abra el menú contextual del rol o la instancia que está depurando y seleccione **Desasociar depurador**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitaciones de la depuración remota en Azure

Desde Azure SDK 2.3, la depuración remota presenta las siguientes limitaciones:

* Con la depuración remota habilitada, no puede publicar un servicio en la nube que presente algún rol con más de 25 instancias.
* El depurador usa los puertos de 30400 a 30424, de 31400 a 31424 y de 32400 a 32424. Si intenta usar alguno de estos puertos, no podrá publicar su servicio y aparecerá uno de los siguientes mensajes de error en el registro de actividad de Azure:

  * Error al validar el archivo .cscfg con el archivo .csdef.
    El intervalo de puertos reservado 'intervalo de puertos' para el extremo Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector del rol 'rol' se superpone con un intervalo o puerto ya definido.
  * Error en la asignación. Vuelva a intentarlo más tarde, intente reducir el tamaño de VM o el número de instancias de rol, o intente implementar en una región distinta.

## <a name="debugging-azure-virtual-machines"></a>Depuración de máquinas virtuales de Azure

Puede depurar programas que se ejecuten en máquinas virtuales de Azure usando el Explorador de servidores en Visual Studio. Si habilita la depuración remota en una máquina virtual de Azure, Azure instalará la extensión de depuración remota en la máquina virtual. A continuación, podrá asociarla a procesos en la máquina virtual y realizar la depuración como lo haría normalmente.

> [!NOTE]
> Las máquinas virtuales creadas a través de la pila del Administrador de recursos de Azure se pueden depurar remotamente mediante Cloud Explorer en Visual Studio de 2015. Para obtener más información, consulte [Administración de recursos de Azure con Cloud Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Para depurar una máquina virtual de Azure

1. En el Explorador de servidores, expanda el nodo Máquinas virtuales y seleccione el nodo de la máquina virtual que desea depurar.

2. Abra el menú contextual y seleccione **Habilitar depuración**. Cuando se le pida que confirme si quiere habilitar la depuración en la máquina virtual, seleccione **Sí**.

    Azure instala la extensión de depuración remota en la máquina virtual para habilitar la depuración.

    ![Comando para habilitar la depuración en máquina virtual](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Registro de actividades de Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Cuando la extensión de depuración remota finalice la instalación, abra el menú contextual de la máquina virtual y seleccione **Asociar depurador...**

    Azure obtiene una lista de los procesos presentes en la máquina virtual y los muestra en el cuadro de diálogo Asociar al proceso.

    ![Comando Asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. En el cuadro de diálogo **Asociar al proceso**, elija **Seleccionar** para limitar la lista de resultados de forma que solo se muestren los tipos de código que quiere depurar. Puede depurar código administrado de 32 o 64 bits, código nativo o ambos.

    ![Seleccionar el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Haga clic en los procesos que quiere depurar en la máquina virtual y después seleccione **Asociar**. Por ejemplo, puede seleccionar el proceso w3wp.exe si desea depurar una aplicación web en la máquina virtual. Consulte [Depuración de uno o varios procesos en Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) y [Arquitectura de roles de Azure](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) para más información.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Creación de un proyecto web y una máquina virtual para la depuración

Antes de publicar el proyecto de Azure, es posible que le resulte útil probarlo en un entorno contenido que sea compatible con los entornos de depuración y pruebas, y en el que pueda instalar programas de pruebas y supervisión. Una manera de ejecutar tales pruebas es depurar su aplicación de forma remota en una máquina virtual.

Los proyectos ASP.NET de Visual Studio ofrecen una opción para crear una práctica máquina virtual que se puede usar para probar aplicaciones. La máquina virtual incluye los puntos de conexión requeridos habitualmente, como PowerShell, Escritorio remoto y Web Deploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Para crear de un proyecto web y una máquina virtual para la depuración

1. En Visual Studio, cree una nueva aplicación web ASP.NET.

2. En el cuadro de diálogo Nuevo proyecto ASP.NET, en la sección Azure, elija **Máquina virtual** del cuadro de lista desplegable. Deje la casilla **Crear recursos remotos** activada. Seleccione **Aceptar** para continuar.

    Aparecerá el cuadro de diálogo **Crear máquina virtual en Azure** .

    ![Cuadro de diálogo Crear nuevo proyecto ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > se le pedirá que inicie sesión en la cuenta de Azure si todavía no lo ha hecho.

3. Seleccione los distintos valores de configuración de la máquina virtual y después seleccione **Aceptar**. Consulte [Máquinas virtuales](https://go.microsoft.com/fwlink/?LinkId=623033) para obtener más información.

    El nombre que escriba como nombre DNS será el nombre de la máquina virtual.

    ![Cuadro de diálogo Crear máquina virtual en Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crea la máquina virtual y, a continuación, aprovisiona y configura los extremos, como Escritorio remoto y Web Deploy.

4. Cuando la máquina virtual esté completamente configurada, seleccione el nodo de la máquina virtual en el Explorador de servidores.

5. Abra el menú contextual y seleccione **Habilitar depuración**. Cuando se le pida que confirme si quiere habilitar la depuración en la máquina virtual, seleccione **Sí**.

    Azure instala la extensión de depuración remota en la máquina virtual para habilitar la depuración.

    ![Comando para habilitar la depuración en máquina virtual](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Registro de actividades de Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publish your project as outlined in [How to: Deploy a Web Project Using One-Click Publish in Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Dado que desea realizar la depuración en la máquina virtual, en la página **Configuración** del asistente para **Publicación web**, seleccione **Depurar** como configuración. Esto garantiza la disponibilidad de los símbolos de código durante la depuración.

    ![Configuración Publicar](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. En **Opciones de publicación de archivos**, seleccione **Quitar archivos adicionales en destino** si el proyecto ya se implementó anteriormente.

8. Después de publicar el proyecto, en el menú contextual de la máquina virtual en el Explorador de servidores, seleccione **Asociar depurador...**

    Azure obtiene una lista de los procesos presentes en la máquina virtual y los muestra en el cuadro de diálogo Asociar al proceso.

    ![Comando Asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. En el cuadro de diálogo **Asociar al proceso**, elija **Seleccionar** para limitar la lista de resultados de forma que solo se muestren los tipos de código que quiere depurar. Puede depurar código administrado de 32 o 64 bits, código nativo o ambos.

    ![Seleccionar el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Haga clic en los procesos que quiere depurar en la máquina virtual y después seleccione **Asociar**. Por ejemplo, puede seleccionar el proceso w3wp.exe si desea depurar una aplicación web en la máquina virtual. Consulte [Depuración de uno o varios procesos en Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) para obtener más información.

## <a name="next-steps"></a>Pasos siguientes

* Use **IntelliTrace** para recopilar un registro de llamadas y eventos de un servidor de versión. Consulte [Depuración con IntelliTrace y Visual Studio de un servicio en la nube publicado](https://go.microsoft.com/fwlink/?LinkID=623016).

* Use **Diagnósticos de Azure** para registrar información detallada del código que se ejecuta en los roles, bien sea en el entorno de desarrollo o en Azure. Consulte [Recopilación de datos de registro mediante Diagnósticos de Azure](https://go.microsoft.com/fwlink/p/?LinkId=400450).
