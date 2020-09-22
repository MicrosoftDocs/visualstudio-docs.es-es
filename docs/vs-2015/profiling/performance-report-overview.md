---
title: Información general sobre el informe de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, about performance rerports
- performance, reports
- performance reports, about performance reports
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd8732a914581b39566bac88fe73698850893f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842442"
---
# <a name="performance-report-overview"></a>Información general sobre el informe de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede ver los datos de generación de perfiles de una sesión de rendimiento en la ventana **Informe de rendimiento** del entorno de desarrollo integrado (IDE) de Visual Studio Team System Development Edition. Los datos de generación de perfiles se guardan en archivos .vsp y .vsps. Las ventanas de la vista Informe permiten ver y analizar problemas de rendimiento de la aplicación.  
  
> [!CAUTION]
> Un archivo de datos de generación de perfiles contiene información confidencial, como el nombre del equipo, la versión del sistema operativo, las rutas de acceso de archivo, información de la memoria y otros datos de configuración del equipo. Se debe mantener un control estricto sobre la distribución de los datos, tanto en su formato nativo .vsp como cuando se exporta a un archivo .csv o .xml.  
>   
> Si se recopilan datos de seguimiento de eventos como parte de la sesión de rendimiento, puede aparecer información adicional en el archivo de registro de seguimiento de eventos (.etl). Esta información incluye su nombre de usuario y dominio, por lo tanto, se debe mantener un control estricto sobre la distribución del archivo de registro.  
  
## <a name="performance-report-window"></a>Ventana Informe de rendimiento  
 La ventana Informe de rendimiento es una ventana de herramientas que se utiliza para ver, administrar y filtrar los datos de rendimiento, e incluye un control de consulta personalizable.  
  
 Puede tener acceso a cada vista en la barra de herramientas principal de la ventana Informe de rendimiento. Haga clic en la flecha situada junto a la lista **Vista actual** para mostrar y seleccionar las vistas individuales que están disponibles.  
  
 La ventana Informe de rendimiento proporciona las siguientes vistas de datos:  
  
### <a name="summary-view"></a>Vista Resumen  
 De forma predeterminada, en la vista Resumen se muestran los datos de generación de perfiles. Esta vista es un punto de partida en la investigación de problemas de rendimiento. Desde cada línea de la vista Resumen, puede desplazarse a vistas más detalladas haciendo clic con el botón derecho en el nombre del módulo o la función. Para obtener más información, consulte [Vista Resumen](../profiling/summary-view.md).  
  
### <a name="callercallee-view"></a>Vista Llamador y destinatario  
 La vista Llamador y destinatario muestra un árbol de llamadas para una función individual. Esta vista está dividida en tres partes:  
  
- La función de destino se muestra en el centro de la vista.  
  
- Las funciones que llamaron a la función (llamadores) se muestran por encima de la función de destino.  
  
- Las funciones a las que llama la función de destino (destinatarios) se muestran debajo de la función de destino.  
  
  Puede seleccionar una función diferente haciendo doble clic en cualquier función de la lista de llamadores o destinatarios. Para obtener más información, consulte [Vista Llamador y destinatario](../profiling/caller-callee-view.md).  
  
### <a name="call-tree-view"></a>Vista Árbol de llamadas  
 La vista Árbol de llamadas muestra las rutas de acceso de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles. La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función muestra todas las funciones a las que llamó, así como los datos de rendimiento de esas llamadas a funciones.  
  
 La vista Árbol de llamadas también puede expandir y resaltar la ruta de acceso de ejecución de una función que consumió más tiempo o de la que se han tomado muestras con más frecuencia. Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en la función y después haga clic en **Expandir ruta de acceso activa**. Para obtener más información, consulte [Vista Árbol de llamadas](../profiling/call-tree-view.md).  
  
### <a name="process-view"></a>Vista Proceso  
 La vista Proceso muestra los datos de rendimiento correspondientes a cada proceso y subproceso del que se generan perfiles. Para obtener más información, consulte [Vista Proceso](../profiling/process-view.md).  
  
### <a name="modules-view"></a>Vista Módulos  
 La vista Módulos enumera los módulos del proyecto y presenta los datos de generación de perfiles para cada módulo. Expanda o contraiga el nombre del módulo para mostrar los datos de generación de perfiles de función. Cuando los datos se recopilan mediante el muestreo, también están disponibles los datos de generación de perfiles del puntero de instrucciones y de líneas del código fuente. Para obtener más información, consulte [Vista Módulos](../profiling/modules-view.md).  
  
### <a name="functions-view"></a>Vista Funciones  
 La vista Funciones muestra las funciones que se llamaron durante la generación de perfiles. Para obtener más información, consulte [Vista Funciones](../profiling/functions-view.md).  
  
### <a name="line-view"></a>Vista Líneas  
 La vista Líneas permite ver las líneas de código fuente específico que se ejecutaron durante la generación de perfiles de muestreo. Para obtener más información, consulte [Vista Líneas](../profiling/lines-view.md).  
  
### <a name="instruction-pointer-ip-view"></a>Vista Puntero de instrucciones (IP)  
 La vista Punteros de instrucción permite ver instrucciones concretas que se ejecutaron durante la generación de perfiles de muestreo. Para obtener más información, consulte [Vista Punteros de instrucción (IP)](../profiling/instruction-pointers-ips-view.md).  
  
### <a name="allocation-view"></a>Vista Asignación  
 La vista Asignación está disponible si **Recopilar asignación de objetos .NET** se seleccionó en la página **General** del cuadro de diálogo de propiedades de la **Sesión de rendimiento**. Consulte [información general sobre la sesión de rendimiento](../profiling/performance-session-overview.md). La vista Asignación enumera los objetos .NET asignados por la aplicación o el componente. Cuando se expande una fila de objetos, se muestra un árbol de llamadas. El árbol de llamadas muestra las rutas de acceso de ejecución que dieron lugar a la creación del objeto. También se muestra información sobre el número de asignaciones inclusivas y exclusivas para cada función en el árbol de llamadas. La vista Asignación también puede expandir y resaltar la ruta de acceso de ejecución de una función que asignó el mayor número de objetos. Para mostrar la ruta de acceso más activa, haga clic con el botón derecho en la función y después haga clic en **Expandir ruta de acceso activa**. Para obtener más información, consulte [Recopilación de datos de asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) y [Vista Asignación](../profiling/dotnet-memory-allocations-view.md).  
  
### <a name="objects-lifetime-view"></a>Vista Duración del objeto  
 La vista Duración del objeto está disponible si se ha seleccionado **Recopilar información de asignación de objetos .NET** y **Recopilar también la información de duración de los objetos .NET** en la página **General** del cuadro de diálogo de propiedades de la **Sesión de rendimiento**.  
  
 La vista Duración del objeto muestra el número total de instancias de cada tipo y el número de objetos recopilados en cada generación de la recolección de elementos no utilizados. Para obtener más información, consulte [Vista Duración del objeto](../profiling/object-lifetime-view.md).  
  
## <a name="customizable-filter-control"></a>Control de filtro personalizable  
 El control de filtro personalizable tiene las siguientes opciones:  
  
- **Importar filtro**: recupera una consulta personalizada guardada previamente.  
  
- **Exportar filtro**: guarda la consulta personalizada en la ubicación especificada.  
  
- **Ejecutar consulta**: ejecuta la consulta como se muestra en el control de consultas personalizadas.  
  
- **Detener consulta**: detiene la ejecución de una consulta. Este botón no está disponible si no se está ejecutando ninguna consulta.  
  
- **Mostrar consulta**: muestra u oculta el control de consultas personalizadas.  
  
- **Guardar analizado**: guarda el informe junto con su análisis actual como un archivo .vsps.  
  
- **Exportar**: guarda el informe actual en un archivo con formato .CSV o .XML, con opciones para guardar las diferentes vistas.  
  
## <a name="see-also"></a>Consulte también  
 [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)   
 [Vistas de informes de rendimiento](../profiling/performance-report-views.md)
