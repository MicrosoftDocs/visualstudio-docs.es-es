---
title: Cuadro de diálogo Configuración avanzada (Visualizador de simultaneidad) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e1dbe50f3161ca80b4eabe63cbf9264210e9658
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300315"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>Cuadro de diálogo Configuración avanzada (Visualizador de simultaneidad)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mediante el cuadro de diálogo **Opciones avanzadas** del Visualizador de simultaneidad, puede controlar cómo se recopilan los seguimientos.  El cuadro de diálogo tiene pestañas para los símbolos, Solo mi código, almacenamiento en búfer, filtrado, eventos de CLR, marcadores, proveedores y archivos.  
  
## <a name="symbols"></a>Símbolos  
 El Visualizador de simultaneidad utiliza los mismos valores de símbolos que el depurador de Visual Studio. El Visualizador de simultaneidad usa la configuración para resolver las pilas de llamadas asociadas a datos de rendimiento.  Cuando procesa los seguimientos, el Visualizador de simultaneidad tiene acceso a los servidores de símbolos que se especifican en la página de configuración.  Cuando se obtiene acceso a estos datos a través una red, el proceso del seguimiento se ralentiza.  Para reducir la cantidad de tiempo necesario para resolver símbolos, estos se pueden almacenar en caché localmente. Si se han descargado los símbolos, Visual Studio los cargará desde la caché local.  
  
## <a name="just-my-code"></a>Solo mi código  
 De forma predeterminada, Solo mi código es el conjunto de archivos .exe y .dll asociados a la solución actual de Visual Studio. El Visualizador de simultaneidad evalúa este conjunto de archivos cuando se utiliza la característica Solo mi código para filtrar las pilas de llamadas. En la pestaña de Solo mi código, puede agregar directorios que contienen archivos .exe y .dll a las ubicaciones que el Visualizador de simultaneidad utiliza para Solo mi código.  
  
 Las rutas de acceso de los archivos .exe y .dll se almacenan en el archivo de seguimiento cuando se recopila el seguimiento.  El cambio de este parámetro no afecta a los seguimientos recopilados previamente.  
  
## <a name="buffering"></a>Almacenamiento en búfer  
 El Visualizador de simultaneidad utiliza el Seguimiento de eventos para Windows (ETW) cuando recopila un seguimiento.  ETW utiliza varios búferes a medida que almacena eventos.  Puede que la configuración del búfer de ETW predeterminada no sea óptima en todos los casos y, eventualmente, podrían producirse problemas, tales como eventos perdidos.  Puede utilizar la pestaña Almacenamiento en búfer para configurar los valores del búfer de ETW. Para obtener más información, vea [Event Tracing](https://go.microsoft.com/fwlink/?LinkId=234579) (Seguimiento de eventos) y [EVENT_TRACE_PROPERTIES structure](https://go.microsoft.com/fwlink/?LinkId=234580) (Estructura de EVENT_TRACE_PROPERTIES).  
  
## <a name="filter"></a>Filtro  
 En la pestaña Filtro, puede seleccionar el conjunto de eventos que recopila el Visualizador de simultaneidad. La selección de un subconjunto de eventos limita los tipos de datos que se presentan en los informes y, además, reduce el tamaño de cada seguimiento y el tiempo necesario para procesarlos.  
  
### <a name="clr-events"></a>Eventos de CLR  
 Los eventos generados por Common Language Runtime (CLR) permiten al Visualizador de simultaneidad resolver las pilas de llamadas administradas.  Si deshabilita la recopilación de eventos de CLR, el tamaño del seguimiento se reducirá, pero algunas pilas de llamadas no se resolverán.  Como resultado, alguna actividad de subproceso de CPU podría clasificarse incorrectamente.  
  
### <a name="collect-for-native-processes"></a>Recopilación de procesos nativos  
 De forma predeterminada, los eventos de CLR se recopilan solo cuando se genera el perfil de un proceso administrado, porque normalmente son innecesarios para procesos nativos.  En algunos casos (por ejemplo, cuando un proceso nativo hospeda CLR), es posible que tenga que recopilar los eventos de CLR para un proceso nativo.  Si es así, seleccione la casilla **Recopilar procesos nativos**.  
  
### <a name="disable-rundown-events"></a>Deshabilitación de eventos de detención  
 CLR genera eventos de dos proveedores: tiempo de ejecución y detención.  Si desea recopilar eventos de tiempo de ejecución CLR, pero desea evitar la recopilación de eventos de detención, active la casilla **Deshabilitar eventos de detención**.  De este modo se reduce el tamaño del archivo de seguimiento generado por la recopilación, pero algunas pilas podrían no resolverse. Para obtener más información, vea [CLR ETW Providers](https://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f) (Proveedores de ETW de CLR).  
  
### <a name="sample-events"></a>Eventos de muestras  
 Puede usar eventos de ejemplo para recopilar pilas de llamadas que están asociadas a la ejecución de subprocesos. Estos eventos se recopilan aproximadamente una vez por milisegundo para los subprocesos que se ejecutan en el proceso actual. Si deshabilita la recopilación de eventos de ejemplo, se reduce el tamaño del seguimiento recopilado, pero no se podrán ver las pilas de llamadas que están asociadas a la ejecución de subprocesos.  
  
### <a name="gpu-events"></a>Eventos de GPU  
 Los eventos de GPU son eventos generados por DirectX. Si deshabilita la recopilación de eventos de GPU, el tamaño del seguimiento recopilado se reduce, pero no se puede ver la actividad de GPU en la vista de utilización ni la actividad del Motor de DirectX en la vista de subprocesos.  
  
### <a name="file-io-events"></a>Eventos de E/S de archivos  
 Los eventos de E/S de archivos representan accesos a disco en nombre del proceso actual.  Si deshabilita los eventos de E/S de archivos, el tamaño del seguimiento se reduce, pero la vista de subprocesos no notificará ninguna información sobre los canales o las operaciones de disco.  
  
## <a name="markers"></a>Markers  
 En la pestaña Marcadores, puede configurar el conjunto de proveedores de ETW que se muestran como marcadores en el Visualizador de simultaneidad.  También se puede filtrar la colección de marcadores según el nivel de importancia y la categoría de ETW.  Si usa el [SDK del Visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md) y el propio proveedor de marcadores, puede registrarlo aquí para que aparezca en la vista de subprocesos.  
  
### <a name="adding-a-new-provider"></a>Adición de un nuevo proveedor  
 Si el código usa el [SDK del Visualizador de simultaneidad](../profiling/concurrency-visualizer-sdk.md) o genera eventos ETW que siguen la convención <xref:System.Diagnostics.Tracing.EventSource>, puede ver estos eventos en el Visualizador de simultaneidad al registrarlos en este cuadro de diálogo.  
  
 En el campo Nombre, escriba un nombre que describa los tipos de eventos que genera el proveedor.  En el campo GUID, escriba el GUID asociado a este proveedor (se asocia un GUID a cada proveedor de ETW).  
  
 Opcionalmente, puede especificar el filtrado de eventos desde este proveedor en función de la categoría o del nivel de importancia.  Además, puede utilizar el campo Categoría como filtro basándose en las categorías del SDK del Visualizador de simultaneidad.  Para ello, escriba una cadena separada por comas de las categorías o de los intervalos de categorías.  De este modo, se especifican las categorías de eventos en el proveedor actual que se van a mostrar.  Si se agrega un proveedor <xref:System.Diagnostics.Tracing.EventSource>, puede usar el campo Categoría para filtrar por palabra clave de ETW.  Dado que la palabra clave es una máscara de bits, puede utilizar una cadena delimitada por comas de números enteros para especificar los bits de la máscara que se establecen. Por ejemplo, "1,2" establece el primer y segundo bit, y esto se convierte en 6 en decimal.  
  
 Puede utilizar la lista del nivel de importancia para filtrar los eventos que tienen una relevancia o nivel de ETW que sea menor que el valor especificado.  
  
### <a name="configuring-an-existing-provider"></a>Configuración de un proveedor existente  
 Para modificar los valores asociados a un proveedor existente, selecciónelo en la lista y, después, elija el botón **Editar proveedor**.  Puede cambiar el nombre, el GUID y las opciones de filtrado.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>Eliminación de los datos de marcador de filtro de los informes del Visualizador de simultaneidad  
 Si no desea que los datos de un proveedor determinado aparezcan en seguimientos futuros, desactive la casilla situada junto al proveedor que desea quitar.  
  
## <a name="files"></a>Archivos  
 En la pestaña **Archivos**, puede especificar el directorio en el que se almacenan los archivos de seguimiento cada vez que se recopila un seguimiento.  El Visualizador de simultaneidad genera cuatro archivos para cada seguimiento que recopila:  
  
- Un archivo de registro de seguimiento de eventos en modo kernel (*.kernel.etl)  
  
- Un archivo de registro de seguimiento de eventos en modo usuario (*.user.etl)  
  
- Un archivo de datos del Visualizador de simultaneidad (*.CVData)  
  
- Un archivo de seguimiento del Visualizador de simultaneidad (*.CVTrace)  
  
  Los dos archivos de registro de seguimiento de eventos almacenan los datos de seguimiento sin procesar, y los dos archivos del Visualizador de simultaneidad almacenan los datos procesados.  Los archivos de registro de seguimiento de eventos sin formato no se utilizan normalmente una vez procesado un seguimiento.  Al activar la casilla **Eliminar archivos de registro de seguimiento de eventos (ETL) tras el análisis** se reduce la cantidad de datos de seguimiento que se almacenan en el disco.  
  
## <a name="see-also"></a>Otras referencias  
 [Solo mi código](../profiling/just-my-code-threads-view.md)   
 [Marcadores del visualizador de simultaneidad](../profiling/concurrency-visualizer-markers.md)
