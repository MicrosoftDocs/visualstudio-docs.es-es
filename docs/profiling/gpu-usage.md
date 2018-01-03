---
title: Uso de GPU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 957fed3c-4ded-4e05-87c6-ccc33de65349
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3a79d924e8f20079040f29a85854555e214e4281
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-usage"></a>Uso de GPU
La herramienta Uso de GPU del concentrador de rendimiento y diagnóstico de Visual Studio permite comprender mejor el uso de hardware de alto nivel con la aplicación Direct3D. Con ella puede determinar si el rendimiento de la aplicación está enlazado a la CPU o a la GPU, y obtener más información sobre cómo usar el hardware de la plataforma con mayor eficacia. La herramienta Uso de GPU es compatible con aplicaciones que usan Direct3D 12, Direct3D 11 y Direct3D 10. No es compatible con otras API de gráficos, como Direct2D u OpenGL.  
  
 Esta es la ventana del **informe de Uso de GPU**:  
  
 ![El informe de uso de la GPU, con las escalas de tiempo de CPU y GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Requisitos  
 Además de los requisitos de diagnóstico de gráficos, para usar la herramienta Uso de GPU deben cumplirse los requisitos siguientes:  
  
-   Una GPU y un controlador compatibles con la instrumentación de intervalos necesaria.  
  
    > [!NOTE]
    >  Para obtener más información sobre el hardware y los controladores compatibles, vea [Compatibilidad de hardware y controladores](#hwsupport) al final de este documento.  
  
 Para obtener más información sobre los requisitos de diagnóstico de gráficos, vea este tema de [introducción](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Cómo usar la herramienta Uso de GPU  
 Cuando se ejecuta una aplicación con la herramienta Uso de GPU, Visual Studio crea una sesión de diagnóstico que representa gráficamente la información de alto nivel sobre el uso de la GPU en tiempo real y el rendimiento de representación de la aplicación.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Para iniciar la herramienta Uso de GPU:  
  
1.  En el menú principal, seleccione **Depurar** y **Rendimiento y diagnósticos** (teclado: presione Alt+F2).  
  
2.  En el concentrador de rendimiento y diagnóstico, active la casilla junto a **Uso de GPU**. Si lo prefiere, active las casillas situadas junto a otras herramientas que le interesen. Puede ejecutar varias herramientas de rendimiento y diagnóstico de manera simultánea para obtener una imagen más completa del rendimiento de la aplicación.  
  
     ![Elija las herramientas de diagnóstico que quiere usar.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")  
  
    > [!NOTE]
    >  No todas las herramientas de rendimiento y diagnóstico pueden usarse al mismo tiempo.  
  
3.  Seleccione el botón **Iniciar** azul de la parte inferior del concentrador de rendimiento y diagnóstico para ejecutar la aplicación con las herramientas que ha seleccionado.  
  
 La información de alto nivel que se muestra en tiempo real describe los intervalos y la velocidad de fotogramas, y el uso de la GPU. Aunque todos estos fragmentos de información se representan de forma independiente, usan una escala de tiempo común y pueden relacionarse fácilmente entre sí.  
  
 Los gráficos **Tiempo entre fotogramas (ms)** y **Fotogramas por segundo (FPS)** contienen dos líneas rojas horizontales que representan los destinos de rendimiento de 60 y 30 fotogramas por segundo. En el gráfico **Tiempo entre fotogramas**, la aplicación excede el destino de rendimiento cuando el gráfico está por debajo de la línea. Cuando el gráfico está por encima de la línea, significa que no alcanza este destino. En el gráfico Fotogramas por segundo, ocurre lo contrario: la aplicación excede el destino de rendimiento cuando el gráfico está por encima de la línea. Cuando el gráfico está por debajo de la línea, significa que no alcanza este destino. Estos gráficos se usan fundamentalmente para obtener información de alto nivel sobre el rendimiento de una aplicación e identificar las ralentizaciones que posiblemente deban investigarse (por ejemplo, la disminución repentina de la velocidad de fotogramas o el aumento del uso de la GPU).  
  
 Mientras la aplicación se ejecuta con la herramienta Uso de GPU, la sesión de diagnóstico también recopila información detallada sobre los eventos de gráficos que se han ejecutado en la GPU. Esta información sirve para generar un informe más pormenorizado del uso que la aplicación realiza del hardware. Este informe tarda cierto tiempo en generarse a partir de la información recopilada, por lo que solo se encuentra disponible una vez que la sesión de diagnóstico ha recopilado toda la información.  
  
 Si desea examinar un problema de uso o rendimiento con mayor detalle, detenga la recopilación de información de rendimiento para que se genere el informe.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Para generar y ver el informe de uso de la GPU:  
  
1.  Seleccione el vínculo **Detener colección** en la parte inferior de la ventana de sesión de diagnóstico, o presione **Detener** en la esquina superior izquierda.  
  
     ![Recopile información de tiempo de la GPU y la CPU.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")  
  
2.  En la parte superior del informe, seleccione una sección en uno de los gráficos en los que se muestra el problema que desea investigar. Puede realizar una selección de tres segundos como máximo. Las secciones más largas se truncan al principio.  
  
     ![Después de la recopilación, seleccione un intervalo para ver los detalles](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")  
  
3.  Si quiere ver una escala de tiempo detallada de la selección, seleccione el vínculo **ver detalles** en el mensaje **…click here to view details of GPU usage for that range** (…haga clic aquí para ver detalles de uso de la GPU del intervalo), en la parte inferior del informe.  
  
     ![Después de la recopilación, con el intervalo seleccionado](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")  
  
 Se abrirá un nuevo documento con fichas que contiene el informe. El informe de uso de la GPU permite ver cuándo se inicia un evento de gráficos en la CPU, cuando este llega a la GPU y cuánto tiempo precisa la GPU para ejecutarlo. Esta información puede ayudarle a identificar los cuellos de botella y las oportunidades para incrementar el paralelismo del código.  

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exportar a GPUView o a Windows Performance Analyzer
A partir de Visual Studio 2017, estos datos se pueden abrir con [GPUView](/windows-hardware/drivers/display/using-gpuview) y [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Para ello, haga clic en el vínculo **Abrir en GpuView** o **Abrir en WPA**, situado en la esquina inferior derecha de la sesión de diagnóstico.

![Abrir en…](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Cómo usar el informe de uso de la GPU  
 La parte superior del informe de uso de la GPU muestra las escalas de tiempo de las actividades de procesamiento de la CPU y la representación y copia de la GPU. Estas escalas de tiempo se dividen mediante barras verticales de color gris claro que representan el valor de vsync de la pantalla. La frecuencia de estas barras coincide con la frecuencia de actualización de una de las pantallas (que se ha seleccionado en el menú desplegable **Mostrar**), de la que se han recopilado los datos de uso de la GPU. Es posible que la pantalla tenga una frecuencia de actualización mayor que el destino de rendimiento de la aplicación. Por ello, no puede haber una relación de 1 a 1 entre el valor de vsync y la velocidad de fotogramas que debe alcanzar la aplicación. Para cumplir su destino de rendimiento, la aplicación debe completar todo el procesamiento, generar la representación y realizar una llamada a Present(), con la velocidad de fotogramas de destino. Sin embargo, no se mostrarán los fotogramas representados hasta la vsync siguiente a Present().  
  
 En la parte inferior se muestra una lista de los eventos de gráficos que se han producido durante el período de tiempo del informe.  
  
 Esta es la ventana de **informe de Uso de GPU**:  
  
 ![El informe de uso de la GPU, con las escalas de tiempo de CPU y GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
 Si se selecciona uno de los eventos de la parte inferior del informe, se situará un marcador en los eventos correspondientes de las escalas de tiempo relevantes (por lo general, un evento en un subproceso de CPU que representa la llamada API, y otro evento en una de las escalas de tiempo de GPU que representa el momento en que la GPU ha completado la tarea). Del mismo modo, si se selecciona uno de los eventos en una escala de tiempo, se resaltará el evento correspondiente en la parte inferior del informe. En la medida en que se vaya alejando de las escalas de tiempo de la parte superior del informe, solo permanecerán visibles los eventos que precisen más tiempo. Para ver los eventos de menor duración, acérquese a las escalas de tiempo con Ctrl + rueda (del dispositivo señalador), o con el control de escalado de la esquina inferior izquierda del panel superior. También puede arrastrar el contenido del panel de la escala de tiempo para desplazarse por los eventos registrados.  
  
 Para encontrar los elementos que busca con mayor facilidad, puede filtrar el informe de uso de la GPU por nombre de proceso, identificador de subproceso y nombre de evento. Además, puede elegir la frecuencia de actualización de la pantalla que determinará las líneas de vysnc y ordenar los eventos jerárquicamente si la aplicación usa la interfaz de ID3DUserDefinedAnnotation para comandos de representación de grupos.  
  
 Más información:  
  
|Control de filtro|Description|  
|--------------------|-----------------|  
|**Process**|El nombre del proceso que le interesa. Este menú desplegable contiene todos los procesos que usan la GPU durante la sesión de diagnóstico. El color asocia con el proceso en este menú es el color de la actividad del subproceso en las escalas de tiempo que aparecen más abajo.|  
|**Subproceso**|El identificador de subproceso que le interesa. En una aplicación multiproceso, este elemento puede ayudarle a aislar los subprocesos específicos del proceso que le interesa. En cada línea de tiempo se resaltan los eventos asociados con el subproceso seleccionado.|  
|**Pantalla**|Número de la pantalla cuya frecuencia de actualización se muestra. **Nota**: Algunos controladores pueden configurarse para mostrar varias pantallas físicas como una única pantalla virtual más grande. En ese caso, solo aparecería una pantalla en la lista, incluso aunque la máquina esté conectada a varias pantallas.|  
|**Filtrar**|Las palabras clave que le interesan. Solo aparecerán en la parte inferior del informe los eventos que coincidan, total o parcialmente, con una palabra clave. Si desea especificar varias palabras clave, sepárelas con punto y coma (;).|  
|**Orden de jerarquía**|Una casilla que indica si se deben conservar o ignorar las jerarquías de eventos que se han definido con marcadores de usuario.|  
  
 La lista de eventos de la parte inferior del informe de uso de la GPU muestra los detalles de cada evento.  
  
|Columna|Description|  
|------------|-----------------|  
|**Nombre de evento**|El nombre del evento de gráficos. Por lo general, cada evento se corresponde con otros dos eventos: uno de la escala de tiempo del subproceso de CPU y otro de la escala de tiempo de GPU.<br /><br /> Cuando la herramienta Uso de GPU no puede determinar el nombre de un evento, este puede definirse como "sin atributos". Para obtener más información, consulte la nota que aparece debajo de esta tabla.|  
|**Inicio de CPU (ns)**|El momento en el que se ha iniciado el evento en la CPU con una llamada a la API de Direct3D. El tiempo se mide en nanosegundos, con relación al momento en que se ha iniciado la aplicación.|  
|**Inicio de GPU (ns)**|El momento en el que se ha iniciado el evento en la GPU. El tiempo se mide en nanosegundos, con relación al momento en que se ha iniciado la aplicación.|  
|**Duración de GPU (ns)**|El tiempo que tardó el evento en completarse en la GPU, en nanosegundos.|  
|**Nombre de proceso**|El nombre de la aplicación de la que procede el evento.|  
|**Identificador de subproceso**|El identificador de subproceso del que procede el evento.|  
  
> [!IMPORTANT]
>  Para la atribución de eventos se requiere Windows 8.1. Además, si la GPU o el controlador no son compatibles con las características de instrumentación necesarias, todos los eventos se definirán como "sin atributos". Si experimenta este problema, actualice el controlador de GPU e inténtelo de nuevo. Para obtener más información, vea [Compatibilidad de hardware y controladores](#hwsupport) más adelante.  
  
## <a name="gpu-usage-settings"></a>Configuración de Uso de GPU  
 Si no desea comenzar a recopilar la información de generación de perfiles en cuanto se inicia la aplicación, puede configurar la herramienta Uso de GPU para posponer esta acción. La información de generación de perfiles puede alcanzar un tamaño considerable, por lo que esta posibilidad de retardo puede resultar interesante si sabe que las ralentizaciones en el rendimiento de la aplicación se producirán más tarde.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Para posponer la generación de perfiles de modo que no se produzca al iniciar la aplicación:  
  
1.  En el menú principal, seleccione **Depurar** y **Rendimiento y diagnósticos** (teclado: presione Alt+F2).  
  
2.  En el concentrador de rendimiento y diagnóstico, siga el vínculo de **configuración** situado junto a **Uso de GPU**.  
  
3.  En **GPU Profiling Configuration** (Configuración de generación de perfiles de GPU), vaya a la página de propiedades **General** y desactive la casilla **Begin profiling at app start** (Comenzar la generación de perfiles al iniciar la aplicación) para posponer la generación de perfiles.  
  
     ![Configure cuándo se inicia la recopilación de uso de GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
>  La generación de perfiles no se puede posponer en las aplicaciones de Direct3D 12.  
  
 Si pospone la recopilación de la información de generación de perfiles con esta opción, cuando ejecute la aplicación con la herramienta Uso de GPU, aparecerá otro vínculo en la parte inferior de la ventana de esta herramienta. Para iniciar la recopilación de la información de generación de perfiles, haga clic en el vínculo **Iniciar** del mensaje **Inicie la recopilación de datos detallados adicionales del uso de GPU**.  
  
##  <a name="hwsupport"></a> Compatibilidad de hardware y controladores  
 Se admiten el hardware y los controladores de GPU siguientes:  
  
|Vendor|Descripción de GPU|Versión del controlador necesaria|  
|------------|---------------------|-----------------------------|  
|Intel®|Procesadores Intel® Core de cuarta generación ("Haswell")<br /><br /> - Intel® HD Graphics (GT1)<br />- Intel® HD Graphics 4200 (GT2)<br />- Intel® HD Graphics 4400 (GT2)<br />- Intel® HD Graphics 4600 (GT2)<br />- Intel® HD Graphics P4600 (GT2)<br />- Intel® HD Graphics P4700 (GT2)<br />- Intel® HD Graphics 5000 (GT3)<br />- Intel® Iris™ Graphics 5100 (GT3)<br />- Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (Usar los últimos controladores)|  
|AMD®|La mayoría desde AMD Radeon™ HD serie 7000 (excepto AMD Radeon™ HD 7350-7670)<br /><br /> GPU AMD Radeon™, GPU AMD FirePro™ y aceleradores de GPU AMD FirePro con arquitectura de Graphics Core Next (GCN)<br /><br /> Unidades de procesamiento acelerado (APU) de AMD® serie E y AMD serie A, con arquitectura de Graphics Core Next (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 o versiones posteriores|  
|NVIDIA®|La mayoría desde NVIDIA® GeForce® serie 400<br /><br /> GPU NVIDIA® GeForce®, GPU NVIDIA Quadro® y aceleradores de GPU NVIDIA® Tesla™, con arquitectura de Fermi™, Kepler™ o Maxwell™|343.37 o versiones posteriores|  
  
 Actualmente no se admiten las configuraciones con varias GPU (como NVIDIA® SLI™ y AMD Crossfire™) Se admite la configuración híbrida de gráficos (como NVIDIA® Optimus™ y AMD Enduro™)  
  
## <a name="see-also"></a>Vea también  
  
-   [Solucionar los problemas de gráficos más relevantes de los juegos con las herramientas DirectX (vídeo)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools)  
-   [Herramienta Uso de GPU de Visual Studio (vídeo)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715)  
-   [Herramienta Uso de GPU de Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx)  
-   [Uso de GPU para DirectX en Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx)
- [GPUView](/windows-hardware/drivers/display/using-gpuview) 
- [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)