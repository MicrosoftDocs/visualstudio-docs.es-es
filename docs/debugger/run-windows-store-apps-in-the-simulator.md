---
title: Ejecutar aplicaciones para UWP en el simulador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f8d1ae730947a70cac253866d0257aa4e0216626
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882774"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Ejecutar aplicaciones para UWP en el simulador
El simulador de Visual Studio para aplicaciones UWP es una aplicación de escritorio que simula una aplicación para UWP. Normalmente, desea depurar en el equipo local, un dispositivo conectado o un equipo remoto. Sin embargo, en algunos escenarios, es posible que desee usar el simulador de Visual Studio para emular un tamaño de pantalla física diferente y la resolución. También puede simular eventos comunes táctiles y rotaciones y simular las propiedades de conexión de red.
  
 El simulador proporciona un entorno en el que puede diseñar, desarrollar, depurar y probar aplicaciones para UWP. Sin embargo, antes de publicar la aplicación en Microsoft Store, debe probar la aplicación en un dispositivo real.  
  
 El simulador de Visual Studio para aplicaciones UWP no se ejecuta en un entorno aislado en el equipo local. Por eso, los errores que aparecen en el simulador (como un error irrecuperable del sistema), también pueden afectar a todo el equipo.  
  
> [!IMPORTANT]
>  El simulador de Visual Studio 2015 no incluye el botón de geolocalización. Esto se debe a que el simulador de Windows 10 no incluye la simulación de geolocalización.
  
##  <a name="BKMK_Set_the_simulator_as_the_target"></a> Establecer el simulador como destino  
 Para ejecutar la aplicación para UWP en el simulador, seleccione **simulador** en la lista desplegable lista junto a la **Iniciar depuración** botón en el depurador **estándar** barra de herramientas. Esta opción solo está disponible si la aplicación **mínima de la plataforma de destino. Versión** es menor o igual que el sistema operativo en el equipo de desarrollo. 
  
 ![Que se ejecuta en el simulador](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")  
  
##  <a name="BKMK_Choose_an_interaction_mode"></a> Elegir el modo de interacción  
 Puede elegir los siguientes modos de interacción:  
  
-   ![Botón de modo del mouse](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") modo del Mouse: establece el modo de interacción en los gestos del mouse. Los gestos del mouse son los clics, los doble clics y arrastrar.  
  
-   ![Botón de inicio de emulación táctil](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") emulación táctil de inicio: establece el modo de interacción en gestos de un solo dedo toque con. Los eventos de un solo dedo son pulsar, arrastrar y deslizar rápidamente.  
  
     ![Destino de un solo dedo simulador](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger") el icono de destino único indica la ubicación de los eventos en el simulador. Usa el mouse para colocar el puntero.  
  
     ![Destino de un solo dedo toque](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged") presione el botón primario del mouse para activar el modo táctil. Por ejemplo, haz clic en el botón para simular una pulsación, o mantenlo presionado para arrastrar o deslizar rápidamente.  
  
## <a name="pinch-and-zoom"></a>Modo táctil de acercar y alejar  
 Establece el modo de interacción en gestos táctiles de acercar y alejar utilizando dos dedos.  
  
-   ![Destino del dedo Siimulator dos](../debugger/media/simulator_twofinger.png "SIMULATOR_TwoFinger")  
  
     El icono de destino doble indica la ubicación de los dos dedos en la pantalla del dispositivo.  
  
    -   Mueve el mouse para colocar los iconos sobre el objeto en la pantalla del dispositivo.  
  
    -   Gira la rueda del mouse hacia atrás o hacia delante para cambiar la distancia simulada de los dos dedos antes de realizar la emulación táctil de acercar o alejar.  
  
-   -   ![Alejar, acercar y girar destinos](../debugger/media/simulator_twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  
  
         Presiona el botón primario y gira la rueda hacia atrás (hacia ti) para acercar (acercar los dedos).  
  
    -   Presiona el botón primario y gira la rueda del mouse hacia delante (hacia el lado contrario a donde tú estás) para alejar (separar los dedos).  
  
## <a name="object-rotation"></a>Rotación de objetos  
 El botón **Emulación táctil, girar** establece el modo de interacción en los gestos de rotación de dos dedos.  
  
-   -   Mueve el mouse para colocar los iconos sobre el objeto en la pantalla del dispositivo.  
  
    -   Gira la rueda del mouse hacia atrás o hacia delante para cambiar la orientación simulada de los dos dedos antes de rotar el objeto.  
  
-   -   Presiona el botón primario y gira la rueda hacia atrás (hacia ti) para rotar el objeto hacia la izquierda. Al girar la rueda del mouse, uno de los dos iconos de destino rota alrededor del otro para indicar el tamaño relativo de la rotación.  
  
    -   Presiona el botón primario y gira la rueda del mouse hacia delante (hacia el lado contrario a donde te encuentras) para rotar el objeto en el sentido de las agujas del reloj.  
  
##  <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Habilitar o deshabilitar el modo Siempre visible  
 Puedes establecer la ventana del simulador para que siempre esté encima de las demás. El botón **Alternar la ventana de nivel superior** habilita o deshabilita el modo **Siempre visible** de la ventana del simulador.  
  
##  <a name="BKMK_Change_the_device_orientation"></a> Cambiar la orientación del dispositivo  
 Puedes cambiar la orientación del dispositivo entre vertical y horizontal rotándolo 90 grados en cualquier dirección.  
  
> [!NOTE]
>  El simulador no respeta la propiedad [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) de un proyecto. Por ejemplo, si el proyecto establece la orientación en `Landscape`y, después, tú rotes el simulador para situarlo en orientación vertical, la imagen de la pantalla del simulador también se rotará y cambiará de tamaño. Debes probar la configuración en un dispositivo real.  
  
> [!NOTE]
>  Si rotas el simulador de modo que su borde sea mayor que la pantalla en que aparece, su tamaño cambia para ajustarse automáticamente a la pantalla. Si lo vuelves a rotar, no recupera su tamaño original.  
  
##  <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Cambiar el tamaño y la resolución de pantalla simulados  
 Para cambiar el tamaño y la resolución de pantalla simulados, seleccione el botón **Cambiar resolución** en la paleta y seleccione otro tamaño y resolución en la lista.  
  
 El tamaño y la resolución de la pantalla aparecen como *Pulgadas de ancho de pantalla, ancho de píxel X alto de píxel*. Ten en cuenta que tanto el tamaño como la resolución de pantalla son simulados. Las coordenadas de ubicación del simulador se convierten a las coordenadas del tamaño y la resolución seleccionados del dispositivo.  
  
> [!NOTE]
>  Puedes guardar versiones a escala de las imágenes de mapa de bits en tu aplicación. Windows cargará la imagen correcta para la escala actual. Para obtener más información, consulte [introducción de diseño y la interfaz de usuario](/windows/uwp/layout/design-and-ui-intro). Sin embargo, si cambias la resolución del simulador de modo que Windows elija otra imagen para ajustarla a la resolución, deberás detener y reiniciar la sesión de depuración para ver la nueva imagen.  
  
##  <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Realizar una captura de pantalla de la aplicación para enviarla a Microsoft Store  
 Al enviar una aplicación a Microsoft Store, debe incluir capturas de pantalla de la aplicación.  
  
> [!NOTE]
>  La captura de pantalla se guarda con la resolución actual del simulador. Para cambiar la resolución, elige el botón **Cambiar resolución** .  
  
-   Para crear capturas de pantalla de la aplicación en el simulador, elige el botón **Capturar pantalla en el Portapapeles** .  
  
-   Para configurar la ubicación donde se encuentran las capturas de pantalla, seleccione el botón **Configuración de captura de pantalla** y elija la ubicación en el menú contextual.  
  
     ![Menú de contexto de configuración de captura de pantalla](../debugger/media/simulator_screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
##  <a name="BKMK_Simulate_network_connection_properties"></a> Simular propiedades de conexión de red  
 Puede ayudar a los usuarios de la aplicación administrar el costo de las conexiones de red de uso medido manteniendo el reconocimiento de red conexión costo o datos plan cambios de estado y habilitando la aplicación para usar esta información para evitar incurrir en costes adicionales para la itinerancia o superar un límite de transferencia de datos especificado. Las API de [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) le permiten responder a los eventos [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) y [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) que firman. Vea [Inicio rápido: administrar los límites de costos de red de uso medido](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Para depurar o probar el código con reconocimiento de costos de red, el simulador puede imitar las propiedades de una red que se exponen a través de la [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) objeto devuelto por [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).
  
 Para simular propiedades de red:  
  
1. En la barra de herramientas del simulador, elija el botón **Cambiar las propiedades de red** .  
  
2. En el cuadro de diálogo **Establecer propiedades de red** , seleccione **Usar propiedades de red simuladas**.  
  
    Desactiva la casilla para quitar la simulación y vuelve a las propiedades de red de la interfaz conectada actualmente.  
  
3. Escribe un **Nombre de perfil** para la red simulada. Recomendamos usar un nombre único que puede usar para identificar la simulación en la propiedad [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) del objeto [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) .  
  
4. Seleccione el valor [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) para el perfil de la lista **Tipo de costo de red** .  
  
5. Desde el **indicador de estado del límite de datos** lista, puede establecer el [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) propiedad o el [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) en true, o bien puede  **En el límite de datos** para establecer ambos valores en false.  
  
6. En la lista **Estado de movilidad** , establezca la propiedad [Movilidad](/uwp/api/windows.networking.connectivity.connectioncost) .  
  
7. Elija **Configurar propiedades** para simular las propiedades de red desencadenando un evento [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) en primer plano y [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) en segundo plano de tipo **NetworkStateChange**.  
  
   **Más información sobre la administración de conexiones de red**  
  
   [Inicio rápido: administrar los límites de costos de red de uso medido](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ejemplo de información de red](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analizar el uso de energía](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)  
  
   [Cómo responder a eventos del sistema con tareas en segundo plano](/previous-versions/windows/apps/hh977058(v=win.10))  
  
   [Desencadenación de eventos de suspensión, reanudación y en segundo plano en aplicaciones para UWP](/visualstudio/debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio)  
  
##  <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navegar por el simulador con el teclado  
 Puede navegar por la barra de herramientas del simulador presione **CTRL + ALT + flecha arriba** para cambiar el foco de la ventana del simulador a la barra de herramientas del simulador. Usa las teclas **Flecha arriba** y **Flecha abajo** para desplazarte entre los botones de la barra de herramientas.  
  
 Puede apagar el simulador presionando **CTRL + ALT + F4**.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar aplicaciones desde Visual Studio](../debugger/run-store-apps-from-visual-studio.md)