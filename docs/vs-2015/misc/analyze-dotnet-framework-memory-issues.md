---
title: Analizar problemas de memoria de .NET Framework | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a51cbe851b6566ab210a3c8ae12a9b7c2e0d2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107663"
---
# <a name="analyze-net-framework-memory-issues"></a>Analizar problemas de memoria de .NET Framework
Use el analizador de memoria administrada de Visual Studio para detectar pérdidas de memoria o un uso ineficaz de esta en el código de .NET Framework. La versión mínima de .NET Framework del código de destino es .NET Framework 4.5.  
  
 La herramienta de análisis de memoria analiza la información de *archivos con datos del montón de volcado* que una copia de los objetos de memoria de una aplicación. Puede recopilar archivos de volcado de memoria (.dmp) en el IDE de Visual Studio o usando otras herramientas del sistema.  
  
- Puede analizar una sola instantánea para entender el impacto relativo de los tipos de objeto en el uso de la memoria y buscar código en la aplicación que use la memoria de forma ineficaz.  
  
- También puede comparar (*diff*) dos instantáneas de una aplicación para buscar las áreas del código que hacen de la memoria que se usan para aumentar con el tiempo.  
  
  Para ver un tutorial del analizador de memoria administrada, consulte [utilizando Visual Studio 2013 para diagnosticar problemas de memoria de .NET en producción](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) en el Visual Studio ALM + blog de Team Foundation Server.  
  
## <a name="BKMK_Contents"></a> Contenido  
 [Uso de memoria en aplicaciones de .NET Framework](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identificar un problema de memoria en una aplicación](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Recopilar instantáneas de memoria](#BKMK_Collect_memory_snapshots)  
  
 [Analizar el uso de memoria](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Uso de memoria en aplicaciones de .NET Framework  
 .NET Framework es un runtime de recolección de elementos no utilizados, de modo que, en la mayoría de las aplicaciones, el uso de la memoria no supone ningún problema. Sin embargo, en aplicaciones de ejecución prolongada, como los servicios Web y las aplicaciones web, y en los dispositivos que tienen una cantidad limitada de memoria, la acumulación de objetos en la memoria puede afectar al rendimiento de la aplicación y del dispositivo donde se ejecuta. Un uso de excesivo de la memoria puede privar de recursos a la aplicación y al equipo si el recolector de elementos no utilizados se ejecuta con demasiada frecuencia, o el sistema operativo se ve forzado a mover memoria entre la RAM y el disco. En el peor de los casos, una aplicación puede bloquearse con una excepción de "Memoria insuficiente".  
  
 .NET *montón administrado* es una región de memoria virtual donde se almacenan los objetos de referencia creados por una aplicación. El recolector de elementos no utilizados (GC) administra la duración de los objetos. Dicho recolector usa referencias para realizar un seguimiento de los objetos que ocupan bloques de memoria. Se genera una referencia cuando un objeto se crea y se asigna a una variable. Un solo objeto puede tener varias referencias. Por ejemplo, se pueden crear referencias adicionales a un objeto agregando dicho objeto a una clase, colección u otra estructura de datos, o bien asignándolo a una segunda variable. Una forma menos obvia de crear una referencia es al agregar un objeto un controlador al evento de otro objeto. En este caso, el segundo objeto contiene la referencia al primero hasta que el controlador se quita explícitamente o se destruye el segundo objeto.  
  
 Para cada aplicación, el recolector de elementos no utilizados mantiene un árbol de referencias que realiza un seguimiento de los objetos a los que hace referencia la aplicación. El *árbol de referencias* con un conjunto de raíces, que incluye objetos globales y estáticos, así como las pilas de subprocesos asociados y dinámicamente crea una instancia de objetos. Un objeto se considera raíz si tiene al menos un objeto primario que contiene una referencia a este. El recolector de elementos no utilizados puede reclamar la memoria de un objeto solamente cuando ningún otro objeto o variable de la aplicación haga referencia a él.  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identificar un problema de memoria en una aplicación  
 El síntoma más visible de los problemas de memoria es el rendimiento de la aplicación, especialmente si empeora con el tiempo. La degradación del rendimiento de otras aplicaciones mientras se ejecuta la aplicación también puede indicar un problema de memoria. Si sospecha que un problema de memoria, use una herramienta como el Administrador de tareas o [Monitor de rendimiento de Windows](http://technet.microsoft.com/library/cc749249.aspx) para investigar en profundidad. Por ejemplo, busque un incremento del tamaño total de la memoria que no se pueda explicar como posible origen de pérdidas de memoria:  
  
 ![Crecimiento de memoria coherente en el Monitor de recursos](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Puede que también observe picos de memoria más grandes de lo normal según sus conocimientos del código, lo que puede ser indicativo de un uso ineficaz de la memoria en un procedimiento:  
  
 ![Los picos de memoria en el Administrador de recursos](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Recopilar instantáneas de memoria  
 La herramienta de análisis de memoria analiza la información de *los archivos de volcado* que contienen información del montón. Puede crear archivos de volcado en Visual Studio, o puede usar una herramienta como [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) desde [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Consulte [¿qué es un volcado de memoria, y cómo se crea uno?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) en el blog del equipo del depurador de Visual Studio.  
  
> [!NOTE]
>  La mayoría de las herramientas pueden recopilar información de volcado de memoria con o sin datos completos de memoria del montón. El analizador de memoria de Visual Studio requiere información completa del montón.  
  
 **Para recopilar un volcado de memoria de Visual Studio**  
  
1. Puede crear un archivo de volcado de memoria para un proceso que se inició desde un proyecto de Visual Studio o bien asociar el depurador a un proceso en ejecución. Consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Detenga la ejecución. El depurador se detiene cuando se elige **interrumpir todos** en el **depurar** menú, o en una excepción o en un punto de interrupción  
  
3. En el **depurar** menú, elija **Guardar volcado como**. En el **Guardar volcado como** diálogo cuadro, especifique una ubicación y asegúrese de que **minivolcado con montón** (predeterminado) está seleccionado en el **Guardar como tipo** lista.  
  
   **Para comparar dos instantáneas de memoria**  
  
   Para analizar el incremento de uso de la memoria de una aplicación, recopile dos archivos de volcado de memoria de una sola instancia de la aplicación.  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analizar el uso de memoria  
 [Filtrar la lista de objetos](#BKMK_Filter_the_list_of_objects) **&#124;** [analizar datos de memoria de una sola instantánea](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [comparar dos de memoria instantáneas](#BKMK_Compare_two_memory_snapshots)  
  
 Para analizar un archivo de volcado de memoria para detectar problemas de uso de memoria:  
  
1. En Visual Studio, elija **archivo**, **abierto** y especifique el archivo de volcado de memoria.  
  
2. En el **resumen del archivo de minivolcado** página, elija **depurar memoria administrada**.  
  
    ![Página de resumen del archivo de volcado de memoria](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   El analizador de memoria inicia una sesión de depuración para analizar el archivo y muestra los resultados en la página Vista del montón:  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filtrar la lista de objetos  
 De forma predeterminada, el analizador de memoria filtra la lista de objetos de una instantánea de memoria para mostrar solo los tipos e instancias que son código de usuario, así como para mostrar solo aquellos tipos cuyo tamaño inclusivo total supera un porcentaje del umbral del tamaño total del montón. Puede cambiar estas opciones en el **ver configuración** lista:  
  
|||  
|-|-|  
|**Habilite Solo mi código**|Solo mi código oculta la mayoría de los objetos del sistema comunes, de forma que en la lista solo aparezcan los tipos que cree.<br /><br /> También puede establecer la opción solo mi código en Visual Studio **opciones** cuadro de diálogo. En el menú **Depurar** , elija **Opciones y configuración**. En el **depuración**/**General** ficha, elija o borre **solo mi código**.|  
|**Contraer objetos pequeños**|**Contraer objetos pequeños** oculta todos los tipos cuyo tamaño inclusivo total es inferior al 0,5 por ciento del tamaño total del montón.|  
  
 También puede filtrar la lista de tipos escribiendo una cadena en el **búsqueda** cuadro. La lista muestra solo aquellos tipos cuyos nombres contienen la cadena.  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analizar datos de memoria de una sola instantánea  
 Visual Studio inicia una nueva sesión de depuración para analizar el archivo y muestra los datos de memoria en la ventana Vista del montón.  
  
 ![La lista Tipo de objeto](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabla Tipo de objeto  
 En la tabla superior se muestran los tipos de objetos que se mantienen en la memoria.  
  
- **Recuento** muestra el número de instancias del tipo en la instantánea.  
  
- **Tamaño (Bytes)** es el tamaño de todas las instancias del tipo, excepto el tamaño de los objetos que contiene referencias. A la clase  
  
- **Tamaño inclusivo (Bytes)** incluye los tamaños de los objetos que se hace referencia.  
  
  Puede elegir el icono de instancias (![el icono de la instancia de la columna de tipo de objeto](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) en el **tipo de objeto** columna para ver una lista de las instancias de la tipo.  
  
#### <a name="instance-table"></a>Tabla Instancia  
 ![Tabla de instancias](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instancia** es la ubicación de memoria del objeto que actúa como el identificador de objeto del objeto  
  
- **Valor** muestra el valor real de los tipos de valor. Puede desplazar el puntero sobre el nombre de un tipo de referencia para ver sus valores de datos en una ventana de información sobre datos.  
  
   ![Los valores en una sugerencia de datos de instancia](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Tamaño (Bytes)** es el tamaño del objeto, excepto el tamaño de los objetos que contiene referencias. A la clase  
  
- **Tamaño inclusivo (Bytes)** incluye los tamaños de los objetos que se hace referencia.  
  
  De forma predeterminada, los tipos y las instancias se ordenan por **tamaño inclusivo (Bytes)**. Elija un encabezado de columna de la lista para cambiar el criterio de ordenación.  
  
#### <a name="paths-to-root"></a>Rutas de acceso al nodo raíz  
  
- Para un tipo seleccionado en el **tipo de objeto** tabla, el **rutas de acceso a la raíz** tabla muestra las jerarquías de tipo único que conducen a objetos raíz para todos los objetos del tipo, junto con el número de referencias a la tipo que está por encima de él en la jerarquía.  
  
- Para un objeto seleccionado de la instancia de un tipo, **rutas de acceso a la raíz** muestra un gráfico de los objetos reales que contienen una referencia a la instancia. Puede desplazar el puntero sobre el nombre del objeto para ver sus valores de datos en una ventana de información sobre datos.  
  
#### <a name="referenced-types--referenced-objects"></a>Tipos a los que se hace referencia/Objetos a los que se hace referencia  
  
- Para un tipo seleccionado en el **tipo de objeto** tabla, el **hace referencia a tipos** pestaña muestra el tamaño y el número de tipos que se hace referencia que se incluyen en todos los objetos del tipo seleccionado.  
  
- Para una instancia seleccionada de un tipo, **hace referencia a objetos** muestra los objetos que son retenidos por la instancia seleccionada. Puede desplazar el puntero sobre el nombre para ver sus valores de datos en una ventana de información sobre datos.  
  
  **Referencias circulares**  
  
  Un objeto puede hacer referencia a otro objeto que contenga directa o indirectamente una referencia al primero. Cuando el analizador de memoria detecta esta situación, detiene la expansión de la ruta de acceso de referencia y agrega un **[ciclo detectado]** anotación a la lista del primer objeto y se detiene.  
  
  **Tipos raíz**  
  
  El analizador de memoria agrega anotaciones a objetos raíz que describen la clase de referencia que se aplica:  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|**Variable estática** `VariableName`|Una variable estática. `VariableName` es el nombre de la variable.|  
|**Identificador de finalización**|Una referencia de la cola del finalizador.|  
|**Variable local**|Variable local.|  
|**Identificador seguro**|Identificador a una referencia segura de la tabla de identificadores de objetos.|  
|**Async. Anclado asincrónico**|Objeto anclado asincrónico de la tabla de identificadores de objetos.|  
|**Identificador dependiente**|Objeto dependiente de la tabla de identificadores de objetos.|  
|**Anclado asincrónico**|Referencia segura anclada de la tabla de identificadores de objetos.|  
|**Identificador RefCount**|Objeto que se cuenta por referencias de la tabla de identificadores de objetos.|  
|**Identificador Sizedref**|Identificador seguro que mantiene un tamaño aproximado del cierre colectivo de todos los objetos y raíces de objetos en tiempo de recolección de elementos no utilizados.|  
|**Variable local anclada**|Variable local anclada.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Comparar dos instantáneas de memoria  
 Puede comparar dos archivos de volcado de memoria de un proceso para encontrar los objetos que podrían ser la causa de pérdidas de memoria. El intervalo entre la recolección del primer archivo (anterior) y el segundo (posterior) debe ser lo suficientemente grande para que el incremento del número de objetos con pérdidas de memoria sea evidente. Para comparar ambos archivos:  
  
1. Abra el segundo archivo de volcado de memoria y, a continuación, elija **depurar memoria administrada** en el **resumen del archivo de minivolcado** página.  
  
2. En la página de informe de análisis de memoria, abra el **Seleccionar línea de base** lista y, a continuación, elija **examinar** para especificar el primer archivo de volcado de memoria.  
  
   El analizador agrega columnas al panel superior del informe que muestran la diferencia entre el **recuento**, **tamaño**, y **tamaño inclusivo** de los tipos a los valores de la instantánea anterior.  
  
   ![Columnas de diferencia en la lista tipo](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Un **recuento de referencias Diff** columna también se agrega a la **rutas de acceso a la raíz** tabla.  
  
   ![Volver al principio](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenido](#BKMK_Contents)  
  
## <a name="see-also"></a>Vea también  
 [Blog de VS ALM TFS: Con Visual Studio 2013 para diagnosticar problemas de memoria de .NET en producción](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio TV &#124; análisis de memoria administrada](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; cuadro de herramientas de Visual Studio &#124; administrado de análisis de memoria en Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)