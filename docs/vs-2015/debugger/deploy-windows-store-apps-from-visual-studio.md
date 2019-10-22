---
title: Implementar aplicaciones de Windows Store
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177474"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Implementar aplicaciones de la Tienda Windows desde Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")

 La funcionalidad de implementación de Visual Studio crea y registra aplicaciones de la Tienda Windows creadas con Visual Studio en un dispositivo de destino. El modo en que se registra la aplicación depende de si el dispositivo de destino es local o remoto.

- Cuando el destino es un equipo local de Visual Studio, Visual Studio registra la aplicación desde su carpeta de compilación.

- Cuando el destino es un dispositivo remoto, Visual Studio copia los archivos necesarios en el equipo remoto y registra la aplicación en ese dispositivo.

  Implementación es automática cuando se depura la aplicación desde Visual Studio mediante el uso de la **Iniciar depuración** opción (teclado: F5) o el **iniciar sin depurar** opción (teclado: CTRL + F5). También puede implementar la aplicación manualmente. La implementación manual es útil en los siguientes casos:

- Pruebas ad hoc en un equipo local o remoto.

- Implementación de una aplicación que iniciará otra aplicación que querrá depurar.

- Implementación de una aplicación que se depurará cuando la inicie otra aplicación u otro método.

## <a name="BKMK_In_this_topic"></a> En este tema
 En este tema, puede aprender lo siguiente:

 [Cómo implementar una aplicación de la Tienda Windows](#BKMK_How_to_deploy_a_Windows_Store_app)

 [Cómo especificar un dispositivo remoto](#BKMK_How_to_specify_a_remote_device)

 [Opciones de implementación](#BKMK_Deployment_options)

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Cómo implementar una aplicación de la Tienda Windows
 La implementación manual de una aplicación es un proceso simple:

1. Si implementa a un dispositivo remoto, especifique el nombre o la dirección IP del dispositivo en la página de proyecto de la propiedad del proyecto de inicio de la aplicación. Los pasos necesarios se mencionan más adelante dentro de este tema.

2. En la barra de herramientas de Visual Studio del depurador, seleccione el destino de la implementación en la lista desplegable que hay junto al botón **Iniciar depuración** .

     ![Ejecutar en el equipo Local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. En el menú **Compilar** , elija **Implementar**

## <a name="BKMK_How_to_specify_a_remote_device"></a> Cómo especificar un dispositivo remoto
 **Requisitos previos**

 Para implementar una aplicación en un dispositivo remoto:

- Debe haber una licencia de desarrollador instalada en el dispositivo remoto.

- La aplicación Herramientas remotas de Visual Studio debe estar instalada en el dispositivo remoto, y el Monitor de depuración remota debe estar en ejecución.

     En la implementación se usa el canal de la red del depurador remoto para enviar los archivos de aplicación al dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Para especificar un dispositivo remoto

1. En la página de propiedades de depuración del proyecto de inicio, especifique el nombre o la dirección IP de un dispositivo de implementación remoto.

2. Para abrir la página de propiedades de depuración, elija el proyecto en el Explorador de soluciones y, luego, seleccione **Propiedades** en el menú contextual.

3. A continuación, elija el nodo **Depurar** en la ventana de las páginas de propiedad.

4. Puede escribir el nombre o la dirección IP del dispositivo remoto, o bien seleccionarlo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .

    ![Cuadro de diálogo Seleccionar conexión del depurador remoto](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    El cuadro de diálogo **Seleccionar conexión del depurador remoto** muestra los equipos que están en la subred local y los que están conectados directamente con el equipo de Visual Studio mediante un cable Ethernet.

   **Cómo especificar el dispositivo remoto en una página de proyecto de JavaScript o Visual C++**

   ![C&#43; &#43; propiedades para la depuración remota del proyecto](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. Elige **Depurador remoto** en la lista **Depurador para iniciar** .

6. Especifique el nombre de la red del dispositivo remoto en el cuadro **Nombre de equipo** . O bien puede seleccionar la flecha abajo del cuadro para seleccionar el dispositivo desde el cuadro de diálogo Seleccionar conexión del depurador remoto.

   **Cómo especificar el dispositivo remoto en una página de proyecto de Visual C# y Visual Basic**

   ![Administra las propiedades del proyecto para la depuración remota](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. Elige **Equipo remoto** en la lista **Dispositivo de destino** .

8. Escribe el nombre de red del dispositivo remoto en el cuadro **Equipo remoto** o haz clic en **Buscar** para elegir el dispositivo en el cuadro de diálogo **Seleccionar conexión del depurador remoto** .

## <a name="BKMK_Deployment_options"></a> Opciones de implementación
 Puede establecer las siguientes opciones de implementación en la página de propiedades de depuración del proyecto de inicio.

 **Permitir bucle invertido de red** por motivos de seguridad, un [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] no se permite realizar llamadas de red en el dispositivo está instalado en aplicación que está instalada en la manera estándar. De forma predeterminada, la implementación de Visual Studio crea una exención respecto a esta regla para la aplicación implementada. Esta exención te permite probar procedimientos de comunicación en un mismo equipo. Antes de enviar su aplicación a la [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)], debe probarla sin la exención.

 Para quitar la exención de bucle invertido de red en la aplicación:

- En C# y en la página de propiedades de depuración de VB, desactive la casilla **Permitir bucle invertido de red** .

- En JavaScript y en la página de propiedades de depuración, establezca el valor de **Permitir bucle invertido de red** en **No**.

  **No iniciar, pero depurar mi código al empezar (C# y VB) o iniciar aplicación (JavaScript y C++)** para configurar la implementación para iniciar automáticamente una sesión de depuración cuando se inicia la aplicación:

- En C# y en la página de depuración de VB, active la casilla **No iniciar, pero depurar mi código al empezar** .

- En JavaScript y en la página de propiedades de depuración, establezca el valor de **Iniciar aplicación** en **Sí**.

## <a name="see-also"></a>Vea también
 [Ejecutar aplicaciones desde Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
