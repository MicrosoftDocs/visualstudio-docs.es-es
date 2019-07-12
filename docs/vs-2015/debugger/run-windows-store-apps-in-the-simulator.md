---
title: Aplicaciones de la ejecución de Windows Store en el simulador | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 77de4fea82e05f539c89a75178d93f985e5a0fb3
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823855"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Ejecutar aplicaciones de la Tienda Windows en el simulador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El simulador de Visual Studio para aplicaciones de la Tienda Windows es una aplicación de escritorio que simula una aplicación de la Tienda Windows. Puede ejecutar aplicaciones y simular eventos táctiles y rotaciones comunes en su equipo de desarrollo. También puede elegir el tamaño físico de la pantalla y la resolución que quiera emular y simular las propiedades de conexión de red.  
  
 El simulador ofrece un entorno en el que puede diseñar, desarrollar, depurar y probar las aplicaciones de la Tienda Windows. Sin embargo, antes de publicar la aplicación en la Tienda Windows, debería probarla en un dispositivo real.  
  
 El simulador de Visual Studio para aplicaciones de la Tienda Windows no se ejecuta en un entorno aislado del equipo local. Por eso, los errores que aparecen en el simulador (como un error irrecuperable del sistema), también pueden afectar a todo el equipo.  
  
 Consulte [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) para obtener información de Windows Phone.  
  
> [!IMPORTANT]
> El simulador de Visual Studio 2015 no incluye el botón de geolocalización. Esto se debe a que el simulador de Windows 10 no incluye la simulación de geolocalización. Si necesita realizar este tipo de simulación, puede usar el simulador de Visual Studio 2013 en Windows 8.1 o en sistemas operativos anteriores.  
  
## <a name="BKMK_Set_the_simulator_as_the_target"></a> Establecer el simulador como destino  
 Para ejecutar la aplicación de la Tienda Windows en el simulador, selecciona **Simulador** en la lista desplegable que hay junto al botón **Iniciar depuración** en la barra de herramientas **Estándar** del depurador.  
  
 ![Que se ejecuta en el simulador](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="BKMK_Choose_an_interaction_mode"></a> Elegir el modo de interacción  
 Puede elegir los siguientes modos de interacción:  
  
- ![Botón de modo del mouse](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") modo del Mouse: establece el modo de interacción en los gestos del mouse. Los gestos del mouse son los clics, los doble clics y arrastrar.  
  
- ![Botón de inicio de emulación táctil](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") emulación táctil de inicio: establece el modo de interacción en gestos de un solo dedo toque con. Los eventos de un solo dedo son pulsar, arrastrar y deslizar rápidamente.  
  
     ![Destino de un solo dedo simulador](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") el icono de destino único indica la ubicación de los eventos en el simulador. Usa el mouse para colocar el puntero.  
  
     ![Destino de un solo dedo toque](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") presione el botón primario del mouse para activar el modo táctil. Por ejemplo, haz clic en el botón para simular una pulsación, o mantenlo presionado para arrastrar o deslizar rápidamente.  
  
## <a name="pinch-and-zoom"></a>Modo táctil de acercar y alejar  
 Establece el modo de interacción en gestos táctiles de acercar y alejar utilizando dos dedos.  
  
- ![Destino de simulador dos dedos](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - El icono de destino doble indica la ubicación de los dos dedos en la pantalla del dispositivo.  

  - Mueve el mouse para colocar los iconos sobre el objeto en la pantalla del dispositivo.  

  - Gira la rueda del mouse hacia atrás o hacia delante para cambiar la distancia simulada de los dos dedos antes de realizar la emulación táctil de acercar o alejar.  

- ![Alejar, acercar y girar destinos](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Presiona el botón primario y gira la rueda hacia atrás (hacia ti) para acercar (acercar los dedos).  

  - Presiona el botón primario y gira la rueda del mouse hacia delante (hacia el lado contrario a donde tú estás) para alejar (separar los dedos).  
  
## <a name="object-rotation"></a>Rotación de objetos  
 El botón **Emulación táctil, girar** establece el modo de interacción en los gestos de rotación de dos dedos.  
  
- Mueve el mouse para colocar los iconos sobre el objeto en la pantalla del dispositivo.  
  
  - Gira la rueda del mouse hacia atrás o hacia delante para cambiar la orientación simulada de los dos dedos antes de rotar el objeto.  

- Presiona el botón primario y gira la rueda hacia atrás (hacia ti) para rotar el objeto hacia la izquierda. Al girar la rueda del mouse, uno de los dos iconos de destino rota alrededor del otro para indicar el tamaño relativo de la rotación.  

  - Presiona el botón primario y gira la rueda del mouse hacia delante (hacia el lado contrario a donde te encuentras) para rotar el objeto en el sentido de las agujas del reloj.  

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Habilitar o deshabilitar el modo Siempre visible  
 Puedes establecer la ventana del simulador para que siempre esté encima de las demás. El botón **Alternar la ventana de nivel superior** habilita o deshabilita el modo **Siempre visible** de la ventana del simulador.  
  
## <a name="BKMK_Change_the_device_orientation"></a> Cambiar la orientación del dispositivo  
 Puedes cambiar la orientación del dispositivo entre vertical y horizontal rotándolo 90 grados en cualquier dirección.  
  
> [!NOTE]
> El simulador no respeta la propiedad [DisplayProperties.AutoRotationPreferences](http://go.microsoft.com/fwlink/?LinkId=249460) de un proyecto. Por ejemplo, si el proyecto establece la orientación en `Landscape`y, después, tú rotes el simulador para situarlo en orientación vertical, la imagen de la pantalla del simulador también se rotará y cambiará de tamaño. Debes probar la configuración en un dispositivo real.  
  
> [!NOTE]
> Si rotas el simulador de modo que su borde sea mayor que la pantalla en que aparece, su tamaño cambia para ajustarse automáticamente a la pantalla. Si lo vuelves a rotar, no recupera su tamaño original.  
  
## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Cambiar el tamaño y la resolución de pantalla simulados  
 Para cambiar el tamaño y la resolución de pantalla simulados, seleccione el botón **Cambiar resolución** en la paleta y seleccione otro tamaño y resolución en la lista.  
  
 El tamaño y la resolución de la pantalla aparecen como *Pulgadas de ancho de pantalla, ancho de píxel X alto de píxel*. Ten en cuenta que tanto el tamaño como la resolución de pantalla son simulados. Las coordenadas de ubicación del simulador se convierten a las coordenadas del tamaño y la resolución seleccionados del dispositivo.  
  
> [!NOTE]
> Puedes guardar versiones a escala de las imágenes de mapa de bits en tu aplicación. Windows cargará la imagen correcta para la escala actual. Para más información, vea [Diseño dinámico 101](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Sin embargo, si cambias la resolución del simulador de modo que Windows elija otra imagen para ajustarla a la resolución, deberás detener y reiniciar la sesión de depuración para ver la nueva imagen.  
  
## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Realizar una captura de pantalla de la aplicación para enviarla a la Tienda Windows  
 Al enviar una aplicación a la tienda de aplicaciones de Windows, debe incluir capturas de pantalla de la aplicación.  
  
> [!NOTE]
> La captura de pantalla se guarda con la resolución actual del simulador. Para cambiar la resolución, elige el botón **Cambiar resolución** .  
  
- Para crear capturas de pantalla de la aplicación en el simulador, elige el botón **Capturar pantalla en el Portapapeles** .  
  
- Para configurar la ubicación donde se encuentran las capturas de pantalla, seleccione el botón **Configuración de captura de pantalla** y elija la ubicación en el menú contextual.  
  
     ![Menú de contexto de configuración de captura de pantalla](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="BKMK_Simulate_network_connection_properties"></a> Simular propiedades de conexión de red  
 Puedes ayudar a los usuarios de la aplicación a administrar los costos de las conexiones de red de uso medido haciendo que tengan conocimiento de ellos o de los cambios de estado del plan de datos, y habilitando la aplicación para utilizar esta información y evitar incurrir así en gastos adicionales por uso en roaming o por superar un límite de transferencia de datos determinado. Las API de [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) le permiten responder a los eventos [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) y [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) que firman. Consulte [Quickstart: Administrar las restricciones de costo de red de uso medido](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Para depurar o probar el código con reconocimiento de costos de red, el simulador puede imitar las propiedades de una red que se exponen a través del objeto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) devuelto por [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx).  
  
 Para simular propiedades de red:  
  
1. En la barra de herramientas del simulador, elija el botón **Cambiar las propiedades de red** .  
  
2. En el cuadro de diálogo **Establecer propiedades de red** , seleccione **Usar propiedades de red simuladas**.  
  
    Desactiva la casilla para quitar la simulación y vuelve a las propiedades de red de la interfaz conectada actualmente.  
  
3. Escribe un **Nombre de perfil** para la red simulada. Recomendamos usar un nombre único que puede usar para identificar la simulación en la propiedad [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) del objeto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) .  
  
4. Seleccione el valor [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) para el perfil de la lista **Tipo de costo de red** .  
  
5. En la lista **Marca de estado del límite de datos** , puede establecer la propiedad [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) o [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)en true, o puede elegir **Por debajo del límite de datos** para establecer ambos valores en false.  
  
6. En la lista **Estado de movilidad** , establezca la propiedad [Movilidad](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Elija **Configurar propiedades** para simular las propiedades de red desencadenando un evento [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) en primer plano y [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) en segundo plano de tipo **NetworkStateChange**.  
  
   **Más información sobre la administración de conexiones de red**  
  
   [Inicio rápido: Administración de las restricciones de costo de red de uso medido](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Ejemplo de información de red](http://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analizar el uso de energía](../profiling/analyze-energy-use-in-store-apps.md)  
  
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Cómo responder a eventos del sistema con tareas en segundo plano](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Desencadenar eventos de suspensión, reanudación y en segundo plano en aplicaciones de la Tienda Windows](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Navegar por el simulador con el teclado  
 Para navegar por la barra de herramientas del simulador presione **Ctrl+Alt+flecha arriba** para cambiar el foco de la ventana del simulador a la barra de herramientas del simulador. Usa las teclas **Flecha arriba** y **Flecha abajo** para desplazarte entre los botones de la barra de herramientas.  
  
 Para apagar el simulador presione **CTRL+ALT+F4**.  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar aplicaciones desde Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
