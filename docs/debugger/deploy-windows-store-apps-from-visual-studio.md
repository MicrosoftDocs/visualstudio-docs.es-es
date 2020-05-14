---
title: Implementación de aplicaciones para UWP | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 4c58dbb32ef0a476ac7e22a840e27e389c710f97
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188283"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Implementar aplicaciones para UWP desde Visual Studio

La funcionalidad de implementación de Visual Studio compila y registra aplicaciones para UWP creadas con Visual Studio en un dispositivo de destino. El modo en que se registra la aplicación depende de si el dispositivo de destino es local o remoto.

- Cuando el destino es un equipo local de Visual Studio, Visual Studio registra la aplicación desde su carpeta de compilación.

- Cuando el destino es un dispositivo remoto, Visual Studio copia los archivos necesarios en el equipo remoto y registra la aplicación en ese dispositivo.

La implementación es automática cuando se depura la aplicación desde Visual Studio mediante la opción **Iniciar depuración** (teclado: F5) o la opción **Iniciar sin depurar** (teclado: CTRL + F5). También puede implementar la aplicación manualmente. La implementación manual es útil en los siguientes casos:

- Pruebas ad hoc en un equipo local o remoto.

- Implementación de una aplicación que iniciará otra aplicación que querrá depurar.

- Implementación de una aplicación que se depurará cuando la inicie otra aplicación u otro método.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Implementación de una aplicación para UWP
 La implementación manual de una aplicación es un proceso simple:

1. Si implementa a un dispositivo remoto, especifique el nombre o la dirección IP del dispositivo en la página de proyecto de la propiedad del proyecto de inicio de la aplicación. Los pasos necesarios se mencionan más adelante dentro de este tema.

2. En la barra de herramientas de Visual Studio del depurador, seleccione el destino de la implementación en la lista desplegable que hay junto al botón **Iniciar depuración** .

     ![Ejecución en la máquina local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. En el menú **Compilar** , elija **Implementar**

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Cómo especificar un dispositivo remoto

**Requisitos previos**

En un dispositivo remoto de Windows 10, debe habilitar el [modo de desarrollador](/windows/uwp/get-started/enable-your-device-for-development). En los dispositivos de Windows 10 que ejecutan la actualización del creador o una versión posterior, las herramientas remotas se instalan automáticamente cuando se implementa la aplicación. Para más información, consulte [Depuración de un paquete de aplicaciones instalado](../debugger/debug-installed-app-package.md).

> [!NOTE]
> En las versiones de Windows 10 anteriores a la actualización del creador, las Herramientas remotas para Visual Studio se deben instalar en el dispositivo remoto y el depurador remoto debe estar en ejecución.

En la implementación se usa el canal de la red del depurador remoto para enviar los archivos de aplicación al dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Para especificar un dispositivo remoto

1. En la página de propiedades de depuración del proyecto de inicio, especifique el nombre o la dirección IP de un dispositivo de implementación remoto.

2. Para abrir la página de propiedades de depuración, elija el proyecto en el Explorador de soluciones y, luego, seleccione **Propiedades** en el menú contextual.

3. A continuación, elija el nodo **Depurar** en la ventana de las páginas de propiedad.

4. En **Dispositivo de destino**, seleccione **Máquina remota**.

5. En **Máquina remota**, haga clic en **Buscar**.

6. Puede escribir el nombre o la dirección IP del dispositivo remoto, o bien seleccionarlo en el cuadro de diálogo **Conexión remota**.

    ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    El cuadro de diálogo **Conexión remota** muestra los dispositivos que están en la subred local y los que están conectados directamente a la máquina de Visual Studio mediante un cable Ethernet.

   **Especificación del dispositivo remoto en una página del proyecto de C++**

   ![Propiedades del proyecto de C++ para la depuración remota](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Elige **Depurador remoto** en la lista **Depurador para iniciar** .

8. Especifique el nombre de la red del dispositivo remoto en el cuadro **Nombre de equipo** . O bien puede seleccionar la flecha abajo del cuadro para seleccionar el dispositivo desde el cuadro de diálogo Seleccionar conexión del depurador remoto.

   **Cómo especificar el dispositivo remoto en una página de proyecto de Visual C# y Visual Basic**

   ![Propiedades de proyectos administrados para la depuración remota](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Elige **Equipo remoto** en la lista **Dispositivo de destino** .

10. Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o haz clic en **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opciones de implementación

Puede establecer las siguientes opciones de implementación en la página de propiedades de depuración del proyecto de inicio.

**Permitir bucle invertido de red**

Por razones de seguridad, una aplicación para UWP o de [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] instalada de forma estándar, no puede realizar llamadas de red al dispositivo en el que está instalada. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar su aplicación a la [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], debe probarla sin la exención.

Para quitar la exención de bucle invertido de red en la aplicación:

- En la página de propiedades de depuración de C# y de Visual Basic, desactive la casilla **Permitir bucle invertido de red**.

- En la página de propiedades de depuración de C++, establezca el valor **Permitir bucle invertido de red** en **No**.

**No iniciar, pero depurar mi código al empezar (C# y Visual Basic) / Iniciar aplicación (C++)**

Para configurar el inicio automático de una sesión de depuración en la implementación cuando se inicie la aplicación:

- En la página de propiedades de depuración de C# y Visual Basic, active la casilla **No iniciar, pero depurar mi código al empezar**.

- En la página de propiedades de depuración de C++, establezca el valor **Iniciar aplicación** en **Sí**.

## <a name="see-also"></a>Vea también

- [Opciones avanzadas de implementación remota](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Depuración de un paquete de aplicaciones instalado](../debugger/debug-installed-app-package.md)
- [Ejecutar aplicaciones desde Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
