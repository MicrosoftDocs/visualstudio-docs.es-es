---
title: Análisis del uso de energía en las aplicaciones de la Tienda | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82f5e6401ba65a0dfaffc268890ece0166432c08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532956"
---
# <a name="analyze-energy-use-in-store-apps"></a>Analizar el uso de energía en las aplicaciones de la Tienda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El generador de perfiles **Consumo de energía** de Visual Studio le ayuda a analizar el consumo de potencia y energía de las aplicaciones de la Tienda Windows en dispositivos de tableta de bajo consumo que funcionan al menos parte del tiempo con baterías. En un dispositivo que funciona con baterías, una aplicación que usa demasiada energía puede producir tanta insatisfacción en el cliente que este puede decidir incluso desinstalarla. La optimización del uso de energía puede incrementar la adopción y el uso de la aplicación por parte de los clientes.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a><a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a>Qué es el generador de perfiles consumo de energía, cómo funciona y qué mide  
 El generador de perfiles Consumo de energía captura las actividades de la pantalla, la CPU y las conexiones de red de un dispositivo durante una sesión de generación de perfiles. Después genera estimaciones de la potencia usada para esas actividades y de la cantidad total de energía para la sesión de generación de perfiles.  
  
> [!NOTE]
> El generador de perfiles de energía calcula el uso de potencia y energía mediante un modelo de hardware de dispositivo de referencia estándar representativo de los dispositivos de tableta de bajo consumo en los que se puede ejecutar la aplicación. Para proporcionar las mejores estimaciones, recomendamos recopilar los datos del perfil en un dispositivo de tableta de bajo consumo.  
>   
> Aunque el modelo proporciona buenas estimaciones para diversos dispositivos de bajo consumo, los valores reales del dispositivo para el que se genera el perfil probablemente serán diferentes. Use los valores para buscar las actividades de pantalla, la CPU y de red con un consumo elevado de los recursos en relación con otros usos de estos y que, por tanto, puedan ser buenas candidatas para la optimización.  
  
 El generador de perfiles Consumo de energía usa estas definiciones de *potencia* y *energía*:  
  
- *Potencia* mide la velocidad a la que se usa la fuerza para realizar un trabajo que se lleva a cabo en un período de tiempo. En electricidad, la unidad de potencia estándar es un *vatio*, que se define como la velocidad a la que se realiza un trabajo cuando una corriente de un amperio fluye a través de una diferencia de potencial eléctrico de un voltio. En el gráfico **Uso de potencia** , las unidades se muestran en milivatios **mW** , que son la milésima parte de un vatio.  
  
   Tenga en cuenta que, dado que la potencia es una tasa, tiene una dirección (el trabajo puede aumentar o disminuir en un período de tiempo) y una velocidad (la cantidad en la que aumenta o disminuye el trabajo).  
  
- *Energía* mide la cantidad total de potencia, bien como capacidad o como potencial, como en la capacidad de potencia de una batería, o como el total de potencia gastada en un período de tiempo. La unidad de energía es un vatio-hora, la cantidad de potencia de un vatio aplicada constantemente durante una hora. En el **Resumen de uso de energía**, las unidades se muestran en milivatios-hora **mW-h**.  
  
  ![Capacidad energética, potencia usada, energía total usada](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Por ejemplo, una batería totalmente cargada en una tableta gráfica tiene cierta cantidad de energía almacenada. Dado que la energía se usa para realizar tareas, como comunicarse a través de una red, calcular valores o mostrar gráficos, la potencia de la batería se disipa a distintas tasas. En cualquier período de tiempo, el total de potencia consumido también se mide por energía.  
  
## <a name="identify-scenarios-with-user-marks"></a><a name="BKMK_Identify_scenarios_with_user_marks"></a>Identificar escenarios con marcas de usuario  
 Puedes agregar *marcas de usuario* a los datos de generación de perfiles para ayudar a identificar áreas en la regla de escala de tiempo.  
  
 ![Marcas de usuario en la escala de tiempo](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 La marca aparece como un triángulo naranja en la escala de tiempo en el momento de la ejecución del método. El mensaje y el tiempo se muestran como información sobre herramientas al mantener el mouse sobre la marca. Si dos o más marcas de usuario están muy próximas, se combinan dichas marcas y los datos sobre herramientas. Puedes acercar la escala de tiempo para separar las marcas.  
  
 **Agregar marcas a código de C#, Visual Basic y C++**  
  
 Para agregar una marca de usuario a código de C#, Visual Basic y C++, cree primero un objeto [Windows.Foundation.Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) . Después, inserte llamadas a métodos [LoggingChannel.LogMessage](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) en los puntos del código que quiera marcar. Use [LoggingLevel.Information](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) en las llamadas.  
  
 Al ejecutarse el método, se agrega una marca de usuario a los datos de generación de perfiles junto con un mensaje.  
  
> [!NOTE]
> - Windows.Foundation.Diagnostics LoggingChannel implementa la interfaz [Windows.Foundation.IClosable](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) (proyectada como [System.IDisposable](https://msdn.microsoft.com/library/System.IDisposable.aspx) en C# y VB). Para evitar la pérdida de recursos de sistema operativo, llame a [LoggingChannel.Close](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx)() (Windows.Foundation.Diagnostics.LoggingChannel.Dispose() en C# y VB) cuando haya finalizado con un canal de registro.  
>   - Cada canal de registro abierto debe tener un nombre único. Al intentar crear un nuevo canal de registro con el mismo nombre que un canal no desechado, se produce una excepción.  
  
 **Agregar marcas a código de JavaScript**  
  
 Para agregar marcas de usuario, agrega el código siguiente en los puntos del código que desees marcar:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* es una cadena que contiene el mensaje que se va a mostrar en la información sobre herramientas de la marca de usuario.  
  
## <a name="configure-your-environment-for-profiling"></a><a name="BKMK_Configure_your_environment_for_profiling"></a>Configurar el entorno para la generación de perfiles  
 Para obtener buenas estimaciones, deberá generar un perfil de uso de energía para la aplicación en un dispositivo de bajo consumo que esté funcionando con baterías. Dado que Visual Studio no se ejecuta en la mayoría de estos dispositivos, deberá conectar su equipo de Visual Studio al dispositivo usando las Herramientas remotas para Visual Studio. Para conectarte con un dispositivo remoto, debes configurar tanto el proyecto de Visual Studio como el dispositivo remoto. Consulte [Ejecutar aplicaciones de la Tienda Windows en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md) para obtener más información.  
  
> [!TIP]
> - No te recomendamos la generación de perfiles de energía en el simulador de la Tienda Windows ni en el equipo de Visual Studio. La generación de perfiles en el dispositivo real proporciona datos mucho más realistas.  
>   - Genere el perfil en el dispositivo de destino mientras esté funcionando con baterías.  
>   - Cierre otras aplicaciones que puedan usar los mismos recursos (red, CPU o pantalla).  
  
## <a name="collect-energy-profile-data-for-your-app"></a><a name="BKMK_Collect_energy_profile_data_for_your_app"></a>Recopilación de datos de Perfil de energía para la aplicación  
  
1. En el menú **Depurar** , elija **Iniciar diagnóstico sin depurar**.  
  
     ![Elección de Consumo de energía en el concentrador de diagnósticos](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. Elija **Consumo de energía** y, a continuación, **Iniciar**.  
  
    > [!NOTE]
    > Al iniciar el generador de perfiles **consumo de energía** , es posible que vea una ventana control de **cuentas de usuario** que solicite su permiso para ejecutar VsEtwCollector.exe. Elija **Sí**.  
  
3. Ejecute la aplicación para recopilar datos.  
  
4. Para detener la generación de perfiles, vuelve a Visual Studio (Alt + Tab) y elige **Detener colección** en la página del concentrador de diagnósticos.  
  
     ![Detección de la recopilación de datos](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Visual Studio analiza los datos recopilados y muestra los resultados.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a><a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a>Recopilación de datos de Perfil de energía para una aplicación instalada  
 La herramienta Consumo de energía solo puede ejecutarse en aplicaciones de la Tienda en Windows 8.1 que se inicien desde una solución de Visual Studio o se instalen desde la Tienda Windows. Cuando una solución se abre en Visual Studio, el destino predeterminado es el **Proyecto de inicio**. Para establecer el destino de una aplicación instalada:  
  
1. Elija **Cambiar destino** y, a continuación, **Aplicación instalada**.  
  
2. En la lista **Seleccionar paquete de aplicaciones instalado** , elija el destino.  
  
3. Elija **Consumo de energía** en la página del concentrador de diagnósticos.  
  
4. Elija **Iniciar** para dar comienzo a la generación de perfiles.  
  
   Para detener la generación de perfiles, vuelve a Visual Studio (Alt + Tab) y elige **Detener colección** en la página del concentrador de diagnósticos.  
  
## <a name="analyze-energy-profile-data"></a><a name="BKMK_Analyze_energy_profile_data"></a>Analizar datos de Perfil de energía  
 Los datos de perfil de energía se muestran en la ventana de documento de Visual Studio:  
  
 ![Página de informe del generador de perfiles de energía](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|Imagen|Descripción|  
|-|-|  
|![Paso 1](../profiling/media/procguid-1.png "ProcGuid_1")|El archivo de informe se denomina Report*YYYYMMDD-HHMM*.diagsession. Puedes cambiar el nombre si decides guardarlo.|  
|![Paso 2](../profiling/media/procguid-2.png "ProcGuid_2")|La escala de tiempo muestra la longitud de la sesión de generación de perfiles, los eventos de activación del ciclo de vida de la aplicación y las marcas de usuario.|  
|![Paso 3](../profiling/media/procguid-3.png "ProcGuid_3")|Puedes restringir el informe a una parte de la escala de tiempo arrastrando las barras azules para seleccionar una región de esta.|  
|![Paso 4](../profiling/media/procguid-4.png "ProcGuid_4")|El gráfico **Uso de potencia** es un gráfico de varias líneas que muestra los cambios producidos en la potencia de salida por un recurso de dispositivo durante una sesión de generación de perfiles. El generador de perfiles Consumo de energía hace un seguimiento de la potencia utilizada por la CPU, la actividad de red y la presentación en pantalla.|  
|![Paso 5](../profiling/media/procguid-6.png "ProcGuid_6")|El gráfico **Recursos (activados/desactivados)**  proporciona detalles sobre los costos energéticos de red. La barra **Red** representa el tiempo que estuvo abierta la conexión de red. La barra secundaria **Transferencia de datos** es el tiempo que la aplicación estuvo recibiendo o enviando datos a través de la red.|  
|![Paso 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|El **Resumen de uso de energía** muestra la cantidad proporcional de la energía total utilizada en la escala de tiempo seleccionada por la CPU, la actividad de red y la presentación en pantalla.|  
  
 **Para analizar los datos de perfil de energía**  
  
 Busca un área donde la potencia del recurso presente un pico de actividad. Establezca una relación entre el área del pico con la funcionalidad de la aplicación. A continuación, use las barras de control de la escala de tiempo para acercarse a dicha área. Si deseas centrarte en el uso de la red, expande el nodo **Red** del gráfico **Recursos (activados/desactivados)**  para comparar el tiempo que estuvo abierta la conexión de red con el tiempo que la aplicación estuvo recibiendo o transfiriendo datos en la conexión. Reducir el tiempo que la red está abierta innecesariamente es un método de optimización muy eficaz.  
  
## <a name="optimize-energy-use"></a><a name="BKMK_Optimize_energy_use"></a>Optimizar el uso de energía  
 Además de transmitir datos, las conexiones de red incurren en ciertos costos de energía para inicializar, mantener y cerrar la conexión. Algunas redes mantienen la conexión durante un período de tiempo después de que los datos se hayan enviado o recibido para permitir que se transmitan más datos en una única conexión. Puedes utilizar el panel **Recursos (activados/desactivados)** para examinar la manera en que la aplicación interactúa con la conexión.  
  
 ![Panel Recursos &#40;On&#47;Off&#41;](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 Si las barras **Red** y **Transferencia de datos** muestran que la conexión está abierta durante largos períodos para transmitir intermitentemente una serie de pequeños paquetes de datos, puedes procesar por lotes los datos para enviarlos en una transmisión, reduciendo así el tiempo que la red está abierta y los costos energéticos.  
  
 ![Panel de resumen del consumo de energía](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Sin embargo, tienes menos control sobre los costos de energía de la pantalla. La mayoría de las pantallas requieren más energía para mostrar colores claros que colores más oscuros, por lo que usar un fondo oscuro es una manera de reducir costos.  
  
## <a name="other-resources"></a><a name="BKMK_Other_resources"></a>Otros recursos  
  
- Las secciones de **estado de la conexión y administración de los costos** para [C#/VB/C++ y XAML](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) y [JavaScript y HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) en el Centro de desarrollo de Windows describen las API de Windows que proporcionan información sobre la conectividad de red que puede usar su aplicación para minimizar el costo del tráfico de red.  
  
     El simulador de Visual Studio para la Tienda Windows te permite simular las propiedades de la conexión de datos de las API de información de red. Consulta [Run Windows Store apps in the simulator](../debugger/run-windows-store-apps-in-the-simulator.md).  
  
- Las herramientas **Control de tiempo de función de JavaScript** y **Uso de CPU** pueden ayudarle a reducir la carga de la CPU siempre que esté causada por funciones ineficaces Consulte [analizar el uso](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md)de la CPU.
