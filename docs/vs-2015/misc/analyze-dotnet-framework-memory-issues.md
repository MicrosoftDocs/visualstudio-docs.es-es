---
title: Analyze .NET Framework memory issues | Microsoft Docs
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
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295898"
---
# <a name="analyze-net-framework-memory-issues"></a>Analizar problemas de memoria de .NET Framework
Use el analizador de memoria administrada de Visual Studio para detectar pérdidas de memoria o un uso ineficaz de esta en el código de .NET Framework. La versión mínima de .NET Framework del código de destino es .NET Framework 4.5.  
  
 The memory analysis tool analyzes information in *dump files with heap data* that a copy of the objects in an app's memory. Puede recopilar archivos de volcado de memoria (.dmp) en el IDE de Visual Studio o usando otras herramientas del sistema.  
  
- Puede analizar una sola instantánea para entender el impacto relativo de los tipos de objeto en el uso de la memoria y buscar código en la aplicación que use la memoria de forma ineficaz.  
  
- You can also compare (*diff*) two snapshots of an app to find areas in your code that cause the memory use to increase over time.  
  
  For a walkthrough of the managed memory analyzer, see [Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) on the Visual Studio ALM + Team Foundation Server blog .  
  
## <a name="BKMK_Contents"></a> Contenido  
 [Memory use in .NET Framework apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identify a memory issue in an app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collect memory snapshots](#BKMK_Collect_memory_snapshots)  
  
 [Analyze memory use](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Memory use in .NET Framework apps  
 .NET Framework es un runtime de recolección de elementos no utilizados, de modo que, en la mayoría de las aplicaciones, el uso de la memoria no supone ningún problema. Sin embargo, en aplicaciones de ejecución prolongada, como los servicios Web y las aplicaciones web, y en los dispositivos que tienen una cantidad limitada de memoria, la acumulación de objetos en la memoria puede afectar al rendimiento de la aplicación y del dispositivo donde se ejecuta. Un uso de excesivo de la memoria puede privar de recursos a la aplicación y al equipo si el recolector de elementos no utilizados se ejecuta con demasiada frecuencia, o el sistema operativo se ve forzado a mover memoria entre la RAM y el disco. En el peor de los casos, una aplicación puede bloquearse con una excepción de "Memoria insuficiente".  
  
 The .NET *managed heap* is a region of virtual memory where reference objects created by an app are stored. El recolector de elementos no utilizados (GC) administra la duración de los objetos. Dicho recolector usa referencias para realizar un seguimiento de los objetos que ocupan bloques de memoria. Se genera una referencia cuando un objeto se crea y se asigna a una variable. Un solo objeto puede tener varias referencias. Por ejemplo, se pueden crear referencias adicionales a un objeto agregando dicho objeto a una clase, colección u otra estructura de datos, o bien asignándolo a una segunda variable. Una forma menos obvia de crear una referencia es al agregar un objeto un controlador al evento de otro objeto. En este caso, el segundo objeto contiene la referencia al primero hasta que el controlador se quita explícitamente o se destruye el segundo objeto.  
  
 Para cada aplicación, el recolector de elementos no utilizados mantiene un árbol de referencias que realiza un seguimiento de los objetos a los que hace referencia la aplicación. The *reference tree* has a set of roots, which includes global and static objects, as well as associated thread stacks and dynamically instantiated objects. Un objeto se considera raíz si tiene al menos un objeto primario que contiene una referencia a este. El recolector de elementos no utilizados puede reclamar la memoria de un objeto solamente cuando ningún otro objeto o variable de la aplicación haga referencia a él.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identify a memory issue in an app  
 El síntoma más visible de los problemas de memoria es el rendimiento de la aplicación, especialmente si empeora con el tiempo. La degradación del rendimiento de otras aplicaciones mientras se ejecuta la aplicación también puede indicar un problema de memoria. If you suspect a memory issue, use a tool like Task Manager or [Windows Performance Monitor](https://technet.microsoft.com/library/cc749249.aspx) to investigate further. Por ejemplo, busque un incremento del tamaño total de la memoria que no se pueda explicar como posible origen de pérdidas de memoria:  
  
 ![Consistent memory growth in Resource Monitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Puede que también observe picos de memoria más grandes de lo normal según sus conocimientos del código, lo que puede ser indicativo de un uso ineficaz de la memoria en un procedimiento:  
  
 ![Memory spikes in Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Collect memory snapshots  
 The memory analysis tool analyzes information in *dump files* that contain heap information. You can create dump files in Visual Studio, or you can use a tool like [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) from [Windows Sysinternals](https://technet.microsoft.com/sysinternals). See [What is a dump, and how do I create one?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) on the Visual Studio Debugger Team blog.  
  
> [!NOTE]
> La mayoría de las herramientas pueden recopilar información de volcado de memoria con o sin datos completos de memoria del montón. El analizador de memoria de Visual Studio requiere información completa del montón.  
  
 **To collect a dump from Visual Studio**  
  
1. Puede crear un archivo de volcado de memoria para un proceso que se inició desde un proyecto de Visual Studio o bien asociar el depurador a un proceso en ejecución. See [Attach to Running Processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Detenga la ejecución. The debugger stops when you choose **Break All** on the **Debug** menu, or at an exception or at a breakpoint  
  
3. On the **Debug** menu, choose **Save Dump As**. In the **Save Dump As** dialog box, specify a location and make sure that **Minidump with Heap** (the default) is selected in the **Save as type** list.  
  
   **To compare two memory snapshots**  
  
   Para analizar el incremento de uso de la memoria de una aplicación, recopile dos archivos de volcado de memoria de una sola instancia de la aplicación.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analyze memory use  
 [Filter the list of objects](#BKMK_Filter_the_list_of_objects) **&#124;** [Analyze memory data in from a single snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Compare two memory snapshots](#BKMK_Compare_two_memory_snapshots)  
  
 Para analizar un archivo de volcado de memoria para detectar problemas de uso de memoria:  
  
1. In Visual Studio, choose **File**, **Open** and specify the dump file.  
  
2. On the **Minidump File Summary** page, choose **Debug Managed Memory**.  
  
    ![Dump file summary page](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   El analizador de memoria inicia una sesión de depuración para analizar el archivo y muestra los resultados en la página Vista del montón:  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filter the list of objects  
 De forma predeterminada, el analizador de memoria filtra la lista de objetos de una instantánea de memoria para mostrar solo los tipos e instancias que son código de usuario, así como para mostrar solo aquellos tipos cuyo tamaño inclusivo total supera un porcentaje del umbral del tamaño total del montón. You can change these options in the **View Settings** list:  
  
|||  
|-|-|  
|**Habilite Solo mi código**|Solo mi código oculta la mayoría de los objetos del sistema comunes, de forma que en la lista solo aparezcan los tipos que cree.<br /><br /> You can also set the Just My Code option in the Visual Studio **Options** dialog box. En el menú **Depurar** , elija **Opciones y configuración**. In the **Debugging**/**General** tab, choose or clear **Just My Code**.|  
|**Collapse Small Objects**|**Collapse Small Objects** hides all types whose total inclusive size is less than 0.5 percent of the total heap size.|  
  
 You can also filter the type list by entering a string in the **Search** box. La lista muestra solo aquellos tipos cuyos nombres contienen la cadena.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analyze memory data in from a single snapshot  
 Visual Studio inicia una nueva sesión de depuración para analizar el archivo y muestra los datos de memoria en la ventana Vista del montón.  
  
 ![The Object Type list](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Tabla Tipo de objeto  
 En la tabla superior se muestran los tipos de objetos que se mantienen en la memoria.  
  
- **Count** shows the number of instances of the type in the snapshot.  
  
- **Size (Bytes)** is the size of the all instances of the type, excluding the size of objects it holds references to. A la clase  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  You can choose the instances icon (![The instance icon in the Object Type column](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in the **Object Type** column to view a list of the instances of the type.  
  
#### <a name="instance-table"></a>Tabla Instancia  
 ![Instances table](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** is the memory location of the object that serves as the object identifier of the object  
  
- **Value** shows the actual value of value types. Puede desplazar el puntero sobre el nombre de un tipo de referencia para ver sus valores de datos en una ventana de información sobre datos.  
  
   ![Instance values in a data tip](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Size (Bytes)** is the size of the object, excluding the size of objects it holds references to. A la clase  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  By default, types and instances are sorted by **Inclusive Size (Bytes)** . Elija un encabezado de columna de la lista para cambiar el criterio de ordenación.  
  
#### <a name="paths-to-root"></a>Rutas de acceso al nodo raíz  
  
- For a type selected from the **Object Type** table, the **Paths to Root** table shows the unique type hierarchies that lead to root objects for all objects of the type, along with the number of references to the type that is above it in the hierarchy.  
  
- For an object selected from the instance of a type, **Paths to Root** shows a graph of the actual objects that hold a reference to the instance. Puede desplazar el puntero sobre el nombre del objeto para ver sus valores de datos en una ventana de información sobre datos.  
  
#### <a name="referenced-types--referenced-objects"></a>Tipos a los que se hace referencia/Objetos a los que se hace referencia  
  
- For a type selected from the **Object Type** table, the **Referenced Types** tab shows the size and number of referenced types held by all objects of the selected type.  
  
- For a selected instance of a type, **Referenced Objects** shows the objects that are held by the selected instance. Puede desplazar el puntero sobre el nombre para ver sus valores de datos en una ventana de información sobre datos.  
  
  **Circular references**  
  
  Un objeto puede hacer referencia a otro objeto que contenga directa o indirectamente una referencia al primero. When the memory analyzer encounters this situation, it stops expanding the reference path and adds a **[Cycle Detected]** annotation to the listing of the first object and stops.  
  
  **Root types**  
  
  El analizador de memoria agrega anotaciones a objetos raíz que describen la clase de referencia que se aplica:  
  
|Anotación|Descripción|  
|----------------|-----------------|  
|**Static variable** `VariableName`|Una variable estática. `VariableName` es el nombre de la variable.|  
|**Finalization Handle**|Una referencia de la cola del finalizador.|  
|**Local Variable**|Variable local.|  
|**Strong Handle**|Identificador a una referencia segura de la tabla de identificadores de objetos.|  
|**Async. Pinned Handle**|Objeto anclado asincrónico de la tabla de identificadores de objetos.|  
|**Dependent Handle**|Objeto dependiente de la tabla de identificadores de objetos.|  
|**Pinned Handle**|Referencia segura anclada de la tabla de identificadores de objetos.|  
|**RefCount Handle**|Objeto que se cuenta por referencias de la tabla de identificadores de objetos.|  
|**SizedRef Handle**|Identificador seguro que mantiene un tamaño aproximado del cierre colectivo de todos los objetos y raíces de objetos en tiempo de recolección de elementos no utilizados.|  
|**Pinned local variable**|Variable local anclada.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Compare two memory snapshots  
 Puede comparar dos archivos de volcado de memoria de un proceso para encontrar los objetos que podrían ser la causa de pérdidas de memoria. El intervalo entre la recolección del primer archivo (anterior) y el segundo (posterior) debe ser lo suficientemente grande para que el incremento del número de objetos con pérdidas de memoria sea evidente. Para comparar ambos archivos:  
  
1. Open the second dump file, and then choose **Debug Managed Memory** on the **Minidump File Summary** page.  
  
2. On the memory analysis report page, open the **Select baseline** list, and then choose **Browse** to specify the first dump file.  
  
   The analyzer adds columns to the top pane of the report that display the difference between the **Count**, **Size**, and **Inclusive Size** of the types to those values in the earlier snapshot.  
  
   ![Diff columns in the type list](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **Reference Count Diff** column is also added to the **Paths to Root** table.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Vea también  
 [VS ALM TFS Blog: Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed Memory Analysis](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio Toolbox &#124; Managed Memory Analysis in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)