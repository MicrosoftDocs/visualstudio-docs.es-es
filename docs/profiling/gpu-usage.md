---
title: Uso de GPU | Microsoft Docs
ms.date: 11/01/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6aa4cce032a5eb80a11568a83c1166b5690bd688
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85279890"
---
# <a name="gpu-usage"></a>Uso de GPU

Emplee la herramienta Uso de GPU del concentrador de rendimiento y diagnóstico de Visual Studio para comprender mejor el uso de hardware de alto nivel de la aplicación Direct3D. Ayuda a ver si el rendimiento de la aplicación está enlazado a la CPU o a la GPU y a obtener más información sobre cómo usar el hardware de la plataforma con mayor eficacia. Uso de GPU admite aplicaciones que usan Direct3D 12, Direct3D 11 y Direct3D 10. No admite otras API de gráficos, como Direct2D u OpenGL.

La ventana de **informe de Uso de GPU** tiene el siguiente aspecto:

![Captura de pantalla del informe de Uso de GPU, con las escalas de tiempo de CPU y GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")

## <a name="requirements"></a>Requisitos

Además de los requisitos de diagnóstico de gráficos, se requiere lo siguiente para usar la herramienta Uso de GPU:

- Una GPU y un controlador compatibles con la instrumentación de intervalos necesaria.

  > [!NOTE]
  > Para obtener más información sobre el hardware y los controladores compatibles, vea [Compatibilidad de hardware y controladores](#hwsupport) al final de este documento.

Para obtener más información sobre los requisitos de diagnóstico de gráficos, consulte este tema de [introducción](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).

## <a name="use-the-gpu-usage-tool"></a>Uso de la herramienta Uso de GPU

Al ejecutar la aplicación en la herramienta Uso de GPU, Visual Studio crea una sesión de diagnóstico. En esta sesión se muestra información de alto nivel sobre el rendimiento de la representación de la aplicación y el uso de la GPU en tiempo real.

Para iniciar la herramienta Uso de GPU:

1. En el menú principal, elija **Depurar** > **Rendimiento y diagnósticos** (o, en el teclado, presione Alt+F2).

2. En el concentrador de **rendimiento y diagnóstico**, active la casilla junto a **Uso de GPU**. Si lo prefiere, active las casillas situadas junto a otras herramientas que le interesen. Puede ejecutar varias herramientas de rendimiento y diagnóstico de manera simultánea para obtener una imagen más completa del rendimiento de la aplicación.

    ![Captura de pantalla del concentrador de rendimiento y diagnóstico, con Uso de GPU seleccionado](media/gpuusageselected.png "Uso de GPU seleccionado")

   > [!NOTE]
   > No todas las herramientas de rendimiento y diagnóstico pueden usarse al mismo tiempo.

3. En la parte inferior del concentrador de **rendimiento y diagnóstico**, seleccione **Iniciar** para ejecutar la aplicación con las herramientas que ha seleccionado.

La información de alto nivel que se muestra en tiempo real incluye los intervalos y la velocidad de fotogramas, y el uso de la GPU. Aunque todos estos fragmentos de información se representan gráficamente de forma independiente, todos ellos usan una escala de tiempo común para poder comprender fácilmente las relaciones.

Los gráficos **Tiempo entre fotogramas (ms)** y **Fotogramas por segundo (FPS)** tienen dos líneas rojas horizontales cada uno que muestran destinos de rendimiento de 60 y 30 fotogramas por segundo. En el gráfico Tiempo entre fotogramas, la aplicación supera el destino de rendimiento si el gráfico está por debajo de la línea. Si el gráfico está por encima de la línea, significa que no alcanza este destino. En el gráfico Fotogramas por segundo ocurre lo contrario: la aplicación supera el destino de rendimiento si el gráfico está por encima de la línea y, si está por debajo, no alcanza este destino. Estos gráficos se usan fundamentalmente para obtener información de alto nivel sobre el rendimiento de la aplicación y para identificar ralentizaciones que posiblemente se quieran investigar. Por ejemplo, podría garantizarse investigación adicional si ve una disminución repentina de la velocidad de fotogramas o un aumento del uso de la GPU.

Mientras la aplicación se ejecuta con la herramienta Uso de GPU, la sesión de diagnóstico también recopila información detallada sobre los eventos de gráficos que se han ejecutado en la GPU. Use esta información para generar un informe más pormenorizado del uso que la aplicación realiza del hardware. Este informe tarda cierto tiempo en generarse a partir de la información recopilada, por lo que solo se encuentra disponible una vez que la sesión de diagnóstico ha recopilado toda la información.

Si desea examinar un problema de uso o rendimiento con mayor detalle, detenga la recopilación de información de rendimiento para que pueda generar el informe.

Para generar y ver el informe Uso de GPU:

1. Seleccione el vínculo **Detener colección** en la parte inferior de la ventana de sesión de diagnóstico, o seleccione **Detener** en la esquina superior izquierda.

   ![Captura de pantalla de la ventana de sesión de diagnóstico](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")

2. En la parte superior del informe, seleccione una sección en uno de los gráficos en los que se muestra el problema que desea investigar. La selección puede tener una duración de hasta 3 segundos. Las secciones más largas se truncan hacia el principio.

   ![Captura de pantalla de la ventana de sesión de diagnóstico](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")

3. Para ver una escala de tiempo detallada de la selección, seleccione **ver detalles** en el mensaje **...haga clic aquí para ver detalles de uso de la GPU del intervalo**, en la parte inferior del informe.

   ![Captura de pantalla de la ventana de sesión de diagnóstico, con el intervalo seleccionado](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")

Esta selección abre un nuevo documento con pestañas que contiene el informe. El informe Uso de GPU ayuda a ver cuándo se inicia un evento gráfico en la CPU, cuándo llega a la GPU y cuánto tiempo precisa la GPU para ejecutarlo. Esta información puede ayudarle a identificar los cuellos de botella y las oportunidades para incrementar el paralelismo del código.

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Exportar a GPUView o a Windows Performance Analyzer

A partir de Visual Studio 2017, puede abrir estos datos con [GPUView](/windows-hardware/drivers/display/using-gpuview) y [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer). Solo ha de seleccionar los vínculos **Abrir en GpuView** o **Abrir en WPA** de la esquina inferior derecha de la sesión de diagnóstico.

![Captura de pantalla de la ventana de sesión de diagnóstico, con los vínculos resaltados](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="use-the-gpu-usage-report"></a>Uso del informe Uso de GPU

La parte superior del informe Uso de GPU muestra escalas de tiempo de las actividades de procesamiento de la CPU, de representación de la GPU y de copia de la GPU. Estas escalas de tiempo se dividen mediante barras verticales de color gris claro que indican la sincronización vertical de la pantalla. La frecuencia de las barras coincide con la frecuencia de actualización de una de las pantallas (seleccionada mediante la lista desplegable **Pantalla**) de la que se han recopilado los datos de uso de la GPU.

Dado que la pantalla puede tener una frecuencia de actualización mayor que el destino de rendimiento de la aplicación, no puede haber una relación de uno a uno entre la sincronización vertical y la velocidad de fotogramas que debe alcanzar la aplicación. Para alcanzar su destino de rendimiento, una aplicación debe completar todo el procesamiento, realizar la representación y realizar una llamada `Present()` a la velocidad de fotogramas de destino. Sin embargo, el fotograma representado no se muestra hasta la siguiente sincronización vertical tras `Present()`.

En la parte inferior del informe Uso de GPU se muestran los eventos de gráficos que se han producido durante el período de tiempo del informe. Cuando se selecciona un evento, aparece un marcador en los eventos correspondientes de las escalas de tiempo relevantes. Normalmente, un evento en un subproceso de la CPU muestra la llamada API, mientras que otro evento en una de las escalas de tiempo de la GPU muestra el momento en que la GPU ha finalizado la tarea. Del mismo modo, cuando se selecciona un evento en una escala de tiempo, el informe resalta el evento de gráficos correspondiente en la parte inferior del informe.

Al alejar las escalas de tiempo de la parte superior del informe, solo se ven los eventos de mayor duración. Para ver los eventos de menor duración, acérquese a las escalas de tiempo con Ctrl + rueda (del dispositivo señalador), o con el control de escalado de la esquina inferior izquierda del panel superior. También puede arrastrar el contenido del panel de la escala de tiempo para desplazarse por los eventos registrados.

Para encontrar lo que busca, filtre el informe Uso de GPU por nombres de proceso, identificadores de subproceso y el nombre del evento. Además, puede elegir la frecuencia de actualización de la pantalla que determina las líneas de sincronización vertical. Puede ordenar los eventos jerárquicamente si la aplicación usa la interfaz [ID3DUserDefinedAnnotation](/windows/desktop/api/d3d11_1/nn-d3d11_1-id3duserdefinedannotation) para agrupar los comandos de representación.

 Más información:

|Control de filtro|Descripción|
|--------------------|-----------------|
|**Process**|El nombre del proceso que le interesa. Esta lista desplegable contiene todos los procesos que usan la GPU durante la sesión de diagnóstico. El color asociado con el proceso es el color de la actividad del subproceso en las escalas de tiempo.|
|**Subproceso**|El identificador de subproceso que le interesa. En una aplicación multiproceso, esta información puede ayudarle a aislar subprocesos concretos pertenecientes al proceso que le interesa. En cada línea de tiempo se resaltan los eventos asociados con el subproceso seleccionado.|
|**Pantalla**|El número de la pantalla cuya frecuencia de actualización se muestra. Algunos controladores pueden configurarse para mostrar varias pantallas físicas como una única pantalla virtual más grande. En ese caso, solo aparecería una pantalla en la lista, incluso aunque la máquina esté conectada a varias pantallas.|
|**Filtrar**|Las palabras clave que le interesan. Solo aparecen en la parte inferior del informe los eventos que coinciden, total o parcialmente, con una palabra clave. Si desea especificar varias palabras clave, sepárelas con punto y coma (;).|
|**Orden de jerarquía**|Una casilla que indica si se deben conservar o ignorar las jerarquías de eventos que se han definido con marcadores de usuario.|

La lista de eventos de la parte inferior del informe Uso de GPU muestra los detalles de cada evento.

|Columna|Descripción|
|------------|-----------------|
|**Nombre de evento**|El nombre del evento de gráficos. Por lo general, cada evento se corresponde con un evento de una escala de tiempo de subproceso de CPU y un evento de escala de tiempo de GPU. Cuando la herramienta Uso de GPU no puede determinar el nombre de un evento, este puede definirse como *sin atributos*. Para obtener más información, consulte la nota que aparece después de esta tabla.|
|**Inicio de CPU (ns)**|El momento en el que se ha iniciado el evento en la CPU con una llamada a la API de Direct3D. El tiempo se mide en nanosegundos, con relación al momento en que se ha iniciado la aplicación.|
|**Inicio de GPU (ns)**|El momento en el que se ha iniciado el evento en la GPU. El tiempo se mide en nanosegundos, con relación al momento en que se ha iniciado la aplicación.|
|**Duración de GPU (ns)**|El tiempo, en nanosegundos, que tardó el evento en completarse en la GPU.|
|**Nombre de proceso**|El nombre de la aplicación de la que procede el evento.|
|**Identificador de subproceso**|El identificador de subproceso del que procede el evento.|

> [!IMPORTANT]
> Además, si la GPU o el controlador no son compatibles con las características de instrumentación necesarias, todos los eventos se definirán como *sin atributos*. Si experimenta este problema, actualice el controlador de GPU e inténtelo de nuevo. Para obtener más información, consulte [Compatibilidad de hardware y controladores](#hwsupport) al final de este documento.

## <a name="gpu-usage-settings"></a>Configuración de Uso de GPU

Si no desea comenzar a recopilar la información de generación de perfiles en cuanto se inicia la aplicación, puede configurar la herramienta Uso de GPU para posponer esta acción. Puesto que la información de generación de perfiles puede alcanzar un tamaño considerable, esta acción resulta útil si sabe que las ralentizaciones en el rendimiento de la aplicación no van a aparecer hasta más adelante.

Para posponer la generación de perfiles de modo que no se produzca al iniciar la aplicación:

1. En el menú principal, elija **Depurar** > **Rendimiento y diagnósticos** (o, en el teclado, presione Alt+F2).

2. En el concentrador de **rendimiento y diagnóstico**, situado junto a **Uso de GPU**, seleccione el vínculo de **configuración**.

3. En **Configuración de generación de perfiles de GPU**, vaya a la página de propiedades **General** y desactive la casilla **Comenzar la generación de perfiles al iniciar la aplicación** para posponer la generación de perfiles.

   ![Captura de pantalla de las páginas de propiedades de un objeto, que muestra opciones de colección](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")

> [!IMPORTANT]
> En este momento, no puede posponer la generación de perfiles para las aplicaciones Direct3D 12.

Después de ejecutar la aplicación en la herramienta Uso de GPU, aparece otro vínculo en la parte inferior de la ventana de la herramienta Uso de GPU. Para iniciar la recopilación de la información de generación de perfiles, haga clic en el vínculo **Iniciar** del mensaje **Inicie la recopilación de datos detallados adicionales del uso de GPU**.

## <a name="hardware-and-driver-support"></a><a name="hwsupport"></a> Compatibilidad de hardware y controladores

Se admiten el hardware y los controladores de GPU siguientes:

|Vendor|Descripción de GPU|Versión del controlador necesaria|
|------------|---------------------|-----------------------------|
|Intel®|Procesadores Intel® Core de cuarta generación ("Haswell")<br /><br /> - Intel® HD Graphics (GT1)<br />- Intel® HD Graphics 4200 (GT2)<br />- Intel® HD Graphics 4400 (GT2)<br />- Intel® HD Graphics 4600 (GT2)<br />- Intel® HD Graphics P4600 (GT2)<br />- Intel® HD Graphics P4700 (GT2)<br />- Intel® HD Graphics 5000 (GT3)<br />- Intel® Iris™ Graphics 5100 (GT3)<br />- Intel® Iris™ Pro Graphics 5200 (GT3e)|(Usar los últimos controladores)|
|AMD®|La mayoría desde AMD Radeon™ HD serie 7000 (excepto AMD Radeon™ HD 7350-7670)<br /><br /> GPU AMD Radeon™, GPU AMD FirePro™ y aceleradores de GPU AMD FirePro con arquitectura de Graphics Core Next (GCN)<br /><br /> Unidades de procesamiento acelerado (APU) de AMD® serie E y AMD serie A, con arquitectura de Graphics Core Next (GCN) ("Kaveri", "Kabini", "Temash", "Beema", "Mullins")|14.7 RC3 o posterior|
|NVIDIA®|La mayoría desde NVIDIA® GeForce® serie 400<br /><br /> GPU NVIDIA® GeForce®, GPU NVIDIA Quadro® y aceleradores de GPU NVIDIA® Tesla™, con arquitectura de Fermi™, Kepler™ o Maxwell™|343.37 o posterior|

 De momento no se admiten configuraciones con varias GPU, como NVIDIA® SLI™ y AMD Crossfire™. Se admiten las configuraciones híbridas de gráficos (como NVIDIA® Optimus™ y AMD Enduro™).
