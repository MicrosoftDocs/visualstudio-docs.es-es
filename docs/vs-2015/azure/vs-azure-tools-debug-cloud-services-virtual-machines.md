---
title: Depuración de una máquina virtual en Visual Studio o un servicio de nube de Azure | Microsoft Docs
description: Depurar un servicio en la nube o una máquina virtual en Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: b2c67ce81a42df4a17761fcee2dcd2f8a67c4941
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002945"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Depuración de una máquina virtual en Visual Studio o un servicio de nube de Azure

Visual Studio ofrece diferentes opciones para depurar Azure cloud services y máquinas virtuales.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Depurar el servicio en la nube en el equipo local

Puede ahorrar tiempo y dinero mediante el uso de Azure compute emulator para depurar el servicio en la nube en un equipo local. Al depurar un servicio localmente antes de implementarlo, puede mejorar la confiabilidad y rendimiento sin pagar por tiempo de proceso. Sin embargo, pueden producirse algunos errores solo al ejecutar un servicio en la nube de Azure propio. Puede depurar estos errores si habilita la depuración remota al publicar su servicio y, a continuación, asociar al depurador a una instancia de rol.

El emulador simula el servicio de Azure Compute y se ejecuta en su entorno local para que puede probar y depurar el servicio de nube antes de implementarla. El emulador administra el ciclo de vida de las instancias de rol y proporciona acceso a recursos simulados, tales como de almacenamiento local. Al depurar o ejecutar su servicio desde Visual Studio, el emulador se inicia automáticamente como una aplicación en segundo plano y, a continuación, implementa el servicio en el emulador. Puede usar el emulador para ver su servicio cuando se ejecuta en el entorno local. Puede ejecutar la versión completa o la versión express del emulador. (A partir de Azure 2.3, la versión express del emulador es el valor predeterminado). Consulte [utilizar Emulator Express para ejecutar y depurar un servicio en la nube localmente](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Para depurar el servicio en la nube en el equipo local

1. En la barra de menús, elija **depurar**, **Iniciar depuración** para ejecutar el proyecto de servicio de nube de Azure. Como alternativa, puede presionar F5. Verá un mensaje que se está iniciando el emulador de proceso. Cuando se inicia el emulador, el icono de bandeja del sistema lo confirma.

    ![Emulador de Azure en la bandeja del sistema](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Mostrar la interfaz de usuario del emulador de proceso, abra el menú contextual del icono de Azure en el área de notificación y, a continuación, seleccione **Mostrar IU del emulador de proceso**.

    El panel izquierdo de la interfaz de usuario muestra los servicios que están implementados actualmente en el emulador de proceso y las instancias de rol que cada servicio se está ejecutando. Puede elegir el servicio o los roles para mostrar el ciclo de vida, registro e información de diagnóstico en el panel derecho. Si coloca el foco en el margen superior de una ventana incluida, se expande para rellenar el recuadro derecho.

3. Paso a través de la aplicación mediante los comandos en el **depurar** menú y establecer puntos de interrupción en el código. Paso a paso a través de la aplicación en el depurador, los paneles se actualizan con el estado actual de la aplicación. Al detener la depuración, se elimina la implementación de aplicaciones. Si la aplicación incluye un rol web y ha establecido la propiedad acción de inicio para iniciar el explorador web, Visual Studio inicia la aplicación web en el explorador. Si cambia el número de instancias de un rol en la configuración del servicio, debe detener el servicio en la nube y, a continuación, reinicie la depuración para que pueda depurar estas nuevas instancias del rol.

    **Nota:** cuando se deja de ejecutar o depurar su servicio, no se detienen el emulador de proceso local y el emulador de almacenamiento. Debe detenerlos explícitamente desde el área de notificación.

## <a name="debug-a-cloud-service-in-azure"></a>Depuración de un servicio en la nube en Azure

Para depurar un servicio en la nube desde un equipo remoto, debe habilitar explícitamente esa funcionalidad al implementar su servicio en la nube para que los servicios (por ejemplo, msvsmon.exe) están instalados en las máquinas virtuales que se ejecutan las instancias de rol necesarios. Si no ha habilitado la depuración remota al publicar el servicio, deberá volver a publicar el servicio con la depuración remota habilitada.

Si habilita la depuración remota para un servicio en la nube, no mostrará un rendimiento inferior ni incurrirá en cargos adicionales. No use la depuración remota en un servicio de producción, ya que los clientes que usan el servicio podrían verse afectados negativamente.

> [!NOTE]
> Al publicar un servicio en la nube desde Visual Studio, puede habilitar **IntelliTrace** para cualquier rol en ese servicio que tienen como destino .NET Framework 4 o .NET Framework 4.5. Mediante el uso de **IntelliTrace**, puede examinar los eventos que se produjeron en una instancia de rol en el pasado y reproducen el contexto desde ese momento. Consulte [depurar un servicio en la nube publicado con IntelliTrace y Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016) y [con IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Para habilitar la depuración remota para un servicio en la nube

1. Abra el menú contextual del proyecto de Azure y, a continuación, seleccione **publicar**.

2. Seleccione el **ensayo** entorno y la **depurar** configuración.

    Esto es solo una referencia. Puede optar por ejecutar sus entornos de pruebas en un entorno de producción. Sin embargo, puede perjudicar a los usuarios si habilita la depuración remota en el entorno de producción. Puede elegir la configuración de lanzamiento, pero la configuración de depuración simplifica la depuración.

    ![Elija la configuración de depuración](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Siga los pasos habituales pero seleccione la **habilitar depurador remoto para todos los roles** casilla de verificación en la **configuración avanzada** ficha.

    ![Configuración de depuración](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Para asociar al depurador a un servicio en la nube en Azure

1. En el Explorador de servidores, expanda el nodo de servicio en la nube.

2. Abra el menú contextual del rol o instancia de rol al que desea asociar y, a continuación, seleccione **adjuntar depurador**.

    Si depura un rol, el depurador de Visual Studio se adjunta a cada instancia de ese rol. El depurador se interrumpirá en un punto de interrupción para la primera instancia de rol que se ejecuta esa línea de código y cumpla las condiciones de dicho punto de interrupción. Si depura una instancia, el depurador se adjunta al solo esa instancia y se interrumpe en un punto de interrupción solo cuando esa instancia específica ejecute esa línea de código y cumpla las condiciones del punto de interrupción.

    ![Asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Después de que el depurador se asocia a una instancia, la depuración como de costumbre. El depurador se asocia automáticamente al proceso de host adecuado para su rol. Dependiendo de cuál es el rol, el depurador se asocia a w3wp.exe, WaWorkerHost.exe o WaIISHost.exe. Para comprobar el proceso al que está asociado el depurador, expanda el nodo de instancia en el Explorador de servidores. Consulte [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) para obtener más información acerca de los procesos de Azure.

    ![Seleccione el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Para identificar los procesos al que está asociado el depurador, abra el cuadro de diálogo de procesos, en la barra de menús, elija Depurar, Windows, los procesos. (Teclado: Ctrl + Alt + Z) Para desasociar un proceso específico, abra el menú contextual y, a continuación, seleccione **desasociar proceso**. O bien, busque el nodo de instancia en el Explorador de servidores, busque el proceso, abra el menú contextual y, a continuación, seleccione **desasociar proceso**.

    ![Depurar procesos](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Evite detenciones prolongadas en los puntos de interrupción cuando la opción remota depuración. Azure trata un proceso que se ha detenido durante más de unos minutos como sin respuesta y deja de enviar tráfico a esa instancia. Si se detiene durante demasiado tiempo, msvsmon.exe se separará del proceso.

Para separar el depurador de todos los procesos de su instancia o rol, abra el menú contextual para el rol o la instancia que está depurando y, a continuación, seleccione **desasociar depurador**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Limitaciones de la depuración remota en Azure

Desde Azure SDK 2.3, la depuración remota presenta las siguientes limitaciones:

* Con la depuración remota habilitada, no se puede publicar un servicio en la nube en el que cualquier rol tiene más de 25 instancias.
* El depurador usa los puertos de 30400 a 30424, de 31400 a 31424 y de 32400 a 32424. Si intenta usar alguno de estos puertos, no podrá publicar su servicio y uno de los siguientes mensajes de error aparecerá en el registro de actividad de Azure:

  * Error al validar el archivo .cscfg con el archivo .csdef.
    El puerto reservado intervalo 'range' para el punto de conexión Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector del rol 'rol' se superpone con un intervalo o puerto ya definido.
  * Error de asignación. Vuelva a intentarlo más tarde, intente reducir el tamaño de máquina virtual o el número de instancias de rol o intente implementar en una región distinta.

## <a name="debugging-azure-virtual-machines"></a>Depuración de máquinas virtuales de Azure

Puede depurar programas que se ejecutan en máquinas virtuales de Azure mediante el Explorador de servidores en Visual Studio. Cuando se habilita la depuración remota en una máquina virtual de Azure, Azure instala la extensión de depuración remota en la máquina virtual. A continuación, puede asociar a procesos en la máquina virtual y depurar como lo haría normalmente.

> [!NOTE]
> Las máquinas virtuales creadas a través de la pila del Administrador de recursos de Azure se pueden depurar remotamente mediante Cloud Explorer en Visual Studio 2015. Para obtener más información, consulte [administración de recursos de Azure con Cloud Explorer](http://go.microsoft.com/fwlink/?LinkId=623031).

### <a name="to-debug-an-azure-virtual-machine"></a>Para depurar una máquina virtual de Azure

1. En el Explorador de servidores, expanda el nodo de las máquinas virtuales y seleccione el nodo de la máquina virtual que desea depurar.

2. Abra el menú contextual y seleccione **Habilitar depuración**. Cuando se le pregunte si está seguro de si desea habilitar la depuración en la máquina virtual, seleccione **Sí**.

    Azure instala la extensión de depuración remota en la máquina virtual para habilitar la depuración.

    ![Máquina virtual Habilitar comando de depuración](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Registro de actividad de Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Después de la extensión de depuración remota finalice la instalación, abra el menú contextual de la máquina virtual y seleccione **asociar depurador...**

    Azure Obtiene una lista de los procesos en la máquina virtual y los muestra en la asociación en el cuadro de diálogo procesar.

    ![Comando asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. En el **asociar al proceso** cuadro de diálogo, seleccione **seleccione** para limitar la lista de resultados para mostrar solo los tipos de código que desea depurar. Puede depurar código administrado de 32 bits o 64 bits, código nativo o ambos.

    ![Seleccione el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Seleccione los procesos que desea depurar en la máquina virtual y, a continuación, seleccione **adjuntar**. Por ejemplo, puede elegir el proceso w3wp.exe si desea depurar una aplicación web en la máquina virtual. Consulte [depurar uno o varios procesos en Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) y [Azure Role Architecture](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) para obtener más información.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Crear un proyecto web y una máquina virtual para la depuración

Antes de publicar su proyecto de Azure, le resultará útil para probarlo en un entorno contenido que admite la depuración y escenarios de pruebas, y donde puede instalar las pruebas y programas de supervisión. Una manera de ejecutar tales pruebas es depurar su aplicación en una máquina virtual de forma remota.

Proyectos de Visual Studio ASP.NET ofrecen una opción para crear una máquina virtual útil que puede usar para probar aplicaciones. La máquina virtual incluye extremos requeridos habitualmente como PowerShell, escritorio remoto y WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Para crear un proyecto web y una máquina virtual para la depuración

1. En Visual Studio, cree una nueva aplicación Web de ASP.NET.

2. En el cuadro de diálogo nuevo proyecto de ASP.NET, en la sección de Azure, elija **Máquina Virtual** en el cuadro de lista desplegable. Deje el **crear recursos remotos** casilla seleccionada. Seleccione **Aceptar** para continuar.

    El **crear máquina virtual en Azure** aparece el cuadro de diálogo.

    ![Crear el cuadro de diálogo de proyecto web ASP.NET](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **Nota:** le pedirá que inicie sesión en su cuenta de Azure si aún no ha iniciado sesión.

3. Seleccione las distintas configuraciones para la máquina virtual y, a continuación, seleccione **Aceptar**. Consulte [máquinas virtuales](http://go.microsoft.com/fwlink/?LinkId=623033) para obtener más información.

    El nombre especificado para el nombre DNS será el nombre de la máquina virtual.

    ![Crear máquina virtual en el cuadro de diálogo de Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure crea la máquina virtual y, a continuación, aprovisiona y configura los puntos de conexión, como escritorio remoto y Web Deploy

4. Cuando la máquina virtual esté completamente configurada, seleccione el nodo de la máquina virtual en el Explorador de servidores.

5. Abra el menú contextual y seleccione **Habilitar depuración**. Cuando se le pregunte si está seguro de si desea habilitar la depuración en la máquina virtual, seleccione **Sí**.

    Azure instala la extensión de depuración remota a la máquina virtual para habilitar la depuración.

    ![Máquina virtual Habilitar comando de depuración](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Registro de actividad de Azure](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Publicar el proyecto como se describe en [Cómo: implementar un proyecto utilizando un solo clic publicación Web en Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Dado que desea depurar en la máquina virtual, en el **configuración** página de la **publicación Web** asistente, seleccione **depurar** como la configuración. Esto garantiza que los símbolos de código están disponibles durante la depuración.

    ![Configuración de publicación](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. En el **File Publish Options**, seleccione **quitar archivos adicionales en destino** si el proyecto ya se ha implementado en un momento anterior.

8. Después de publicar el proyecto, en el menú contextual de la máquina virtual en el Explorador de servidores, seleccione **asociar depurador...**

    Azure Obtiene una lista de los procesos en la máquina virtual y los muestra en la asociación en el cuadro de diálogo procesar.

    ![Comando asociar depurador](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. En el **asociar al proceso** cuadro de diálogo, seleccione **seleccione** para limitar la lista de resultados para mostrar solo los tipos de código que desea depurar. Puede depurar código administrado de 32 bits o 64 bits, código nativo o ambos.

    ![Seleccione el cuadro de diálogo de tipo de código](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Seleccione los procesos que desea depurar en la máquina virtual y, a continuación, seleccione **adjuntar**. Por ejemplo, puede elegir el proceso w3wp.exe si desea depurar una aplicación web en la máquina virtual. Consulte [depurar uno o varios procesos en Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) para obtener más información.

## <a name="next-steps"></a>Pasos siguientes

* Use **Intellitrace** para recopilar un registro de llamadas y eventos de un servidor de la versión. Consulte [depurar un servicio en la nube publicado con IntelliTrace y Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016).

* Use **diagnósticos de Azure** para registrar información detallada del código que se ejecuta en roles, si los roles se ejecutan en el entorno de desarrollo o en Azure. Consulte [recopilar datos de registro mediante Diagnósticos de Azure](http://go.microsoft.com/fwlink/p/?LinkId=400450).
