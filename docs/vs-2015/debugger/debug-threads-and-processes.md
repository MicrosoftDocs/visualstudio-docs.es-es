---
title: Depurar subprocesos y procesos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df9bc7cdb185edd27d7572c1436db442514d38e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202562"
---
# <a name="debug-threads-and-processes"></a>Depurar procesos y subprocesos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los subprocesos * y *los procesos* son conceptos relacionados en informática. Los dos representan secuencias de instrucciones que se deben ejecutar en un orden concreto. Sin embargo, las instrucciones de subprocesos o procesos independientes se pueden ejecutar en paralelo.  
  
 Los procesos existen en el sistema operativo y corresponden a lo que los usuarios consideran programas o aplicaciones. Por otra parte, un subproceso existe dentro de un proceso. Por esta razón, los subprocesos se denominan a veces *procesos ligeros*. Cada proceso está compuesto por uno o más subprocesos.  
  
 La existencia de varios procesos permite a un equipo realizar más de una tarea a la vez. La existencia de varios subprocesos permite a un proceso dividir el trabajo que se va a realizar en paralelo. En un equipo con multiprocesadores, los procesos o subprocesos se pueden ejecutar en procesadores diferentes. Esto permite realizar un verdadero procesamiento en paralelo.  
  
 El procesamiento paralelo perfecto no siempre es posible. En ocasiones, los subprocesos deben sincronizarse. Es posible que un subproceso tenga que esperar al resultado de otro subproceso, o necesite acceso exclusivo a un recurso que otro subproceso esté utilizando. Los problemas de sincronización son una causa común de errores en las aplicaciones multiproceso. A veces, los subprocesos pueden acabar esperando un recurso que nunca está disponible. Esto provoca una condición denominada *interbloqueo*.  
  
 El depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona herramientas eficaces pero fáciles de usar para depurar subprocesos y procesos.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Herramientas para depurar subprocesos y procesos en Visual Studio  
 Las herramientas principales para trabajar con procesos en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] son el cuadro de diálogo **asociar al proceso** , la ventana **procesos** y la barra de herramientas **Ubicación de depuración** . Las herramientas principales para depurar subprocesos son la ventana **subprocesos** , los marcadores de subproceso en las ventanas de código fuente y la barra de herramientas **Ubicación de depuración** .  
  
 Las herramientas principales para depurar aplicaciones multiproceso son las ventanas **pilas paralelas** y **tareas paralelas**, **inspección paralela**y **subprocesos de GPU** .  
  
 La tabla siguiente muestra la información disponible y las acciones que se pueden realizar en cada uno de estos lugares:  
  
|Interfaz de usuario|Información disponible|Acciones que puede realizar|  
|--------------------|---------------------------|-----------------------------|  
|Cuadro de diálogo **Asociar al proceso**|Procesos disponibles que puede asociar:<br /><br /> -   Nombre del proceso (.exe)<br />-   Número de id. del proceso<br />-   Título de la barra de menú<br />-   Tipo (Administrado v4.0; Administrador v2.0, v1.1, v1.0; x86; x64; IA64)<br />-   Nombre de usuario (nombre de la cuenta)<br />-   Número de la sesión|Seleccionar un proceso para asociar<br /><br /> Seleccionar un equipo remoto<br /><br /> Cambiar el tipo de transporte para conectar a equipos remotos.|  
|Ventana **Procesos**|Procesos asociados:<br /><br /> -   Nombre del proceso<br />-   Número de id. del proceso<br />-   Ruta de acceso al archivo .exe del proceso<br />-   Título de la barra de menú<br />-   Estado (Inter., En ejecución)<br />-   Depuración (nativa, administrada, etc.)<br />-   Tipo de transporte (predeterminado, nativo sin autenticación)<br />-   Calificador de transporte (equipo remoto)|Herramientas:<br /><br /> -   Asociar<br />-   Desasociar<br />-   Finalizar<br /><br /> Menú contextual:<br /><br /> -   Asociar<br />-   Desasociar<br />-   Desasociar cuando se detenga la depuración<br />-   Finalizar|  
|Ventana **Subprocesos**|Subprocesos en el proceso actual:<br /><br /> -   Identificador de subproceso<br />-   Identificador administrado<br />-   Categoría (subproceso principal, subproceso de interfaz, controlador de llamadas a procedimientos remotos o subproceso de trabajo)<br />-   Nombre del subproceso<br />-   Ubicación donde se creó el subproceso<br />-   Prioridad<br />-   Máscara de afinidad<br />-   Recuento de suspendidos<br />-   Nombre del proceso<br />-   Indicador de marca<br />-   Indicador suspendido|Herramientas:<br /><br /> -   Buscar<br />-   Buscar en pila de llamadas<br />-   Marcar solo mi código<br />-   Marcar selección de módulos personalizados<br />-   Agrupar por<br />-   Columnas<br />-   Expandir o contraer pilas de llamadas<br />-   Expandir o contraer grupos<br />-   Inmovilizar o reanudar subprocesos<br /><br /> Menú contextual:<br /><br /> -   Mostrar subprocesos en código fuente<br />-   Modificar a un subproceso<br />-   Inmovilizar un subproceso en ejecución<br />-   Reanudar un subproceso inmovilizado<br />-   Marcar un subproceso para su estudio adicional<br />-   Quitar el marcador a un subproceso<br />-   Cambiar el nombre de un subproceso<br />-   Mostrar y ocultar subprocesos<br /><br /> Otras acciones:<br /><br /> -   Ver la pila de llamadas de un subproceso en una información sobre datos|  
|Ventana de código fuente|Los indicadores de subproceso del margen interno izquierdo indican uno o varios procesos (desactivados de forma predeterminada, se activan mediante el menú contextual de la ventana **Subprocesos**)|Menú contextual:<br /><br /> -   Modificar a un subproceso<br />-   Marcar un subproceso para su estudio adicional<br />-   Quitar el marcador a un subproceso|  
|Barra de herramientas **Ubicación de depuración**|-   Proceso actual<br />-   Suspender la aplicación<br />-   Reanudar la aplicación<br />-   Suspender y cerrar la aplicación<br />-   Subproceso actual<br />-   Alternar estado marcado del subproceso actual<br />-   Mostrar solo los subprocesos marcados<br />-   Mostrar solo el proceso actual<br />-   Marco de pila actual|-   Modificar a otro proceso<br />-   Suspender, reanudar o cerrar la aplicación<br />-   Modificar a otro subproceso en el proceso actual<br />-   Modificar a otro marco de pila en el subproceso actual<br />-   Marcar o desmarcar subprocesos<br />-   Mostrar solo los subprocesos marcados<br />-   Mostrar solo el proceso actual|  
|Ventana **Pilas paralelas**|-   Pilas de llamadas para varios subprocesos en una ventana.<br />-   Marco de pila activa para cada subproceso.<br />-   Llamadores y destinatarios de cualquier método|-   Filtrar subprocesos especificados<br />-Cambiar a la vista de tareas paralelas<br />-   Marcar o demarcar un subproceso<br />-   Zoom|  
|Ventana **tareas paralelas**|-   Vea información sobre los objetos <xref:System.Threading.Tasks.Task>, como el identificador de tarea, el estado de la tarea (programado, en ejecución, en espera, interbloqueada) y qué subproceso está asignado a la tarea.<br />-   Ubicación actual en la pila de llamadas.<br />-   Delegado pasado a la tarea en el momento de creación|-   Pasar a la tarea actual<br />-   Marcar o desmarcar una tarea<br />-   Inmovilizar o reanudar una tarea|  
|Ventana **Inspección paralela**|-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.<br />-   La columna de marcos, en la que una flecha indica el marco seleccionado.<br />-   Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.|-   Marcar o demarcar un subproceso<br />-   Mostrar solo subprocesos marcados<br />-   Cambiar marcos<br />-   Ordenar una columna<br />-   Agrupar subprocesos<br />-   Inmovilizar o reanudar subprocesos<br />-   Exportar los datos en la ventana Inspección paralela|  
|Ventana **Subprocesos de GPU**|-   La columna de marcas, en la que puede marcar un subproceso al que desee prestar especial atención.<br />-La columna de subproceso activo, donde una flecha amarilla indica un subproceso activo. Una flecha indica un subproceso en el que la ejecución interrumpió el depurador.<br />-   La columna **Recuento de subprocesos**, que muestra el número de subprocesos en la misma ubicación.<br />-   La columna **Línea**, que muestra la línea de código en la que se encuentra cada grupo de subprocesos.<br />-   La columna **Dirección**, que muestra la dirección de instrucción en la que se encuentra cada grupo de subprocesos.<br />-   La columna **Ubicación**, que es la ubicación en el código de la dirección.<br />-   La columna **Estado**, que muestra si el subproceso está activo o bloqueado.<br />-   La columna **Mosaico**, que muestra el índice del mosaico para los subprocesos de la fila.|-Cambiar a un subproceso activo diferente<br />-   Mostrar un mosaico y subproceso determinados<br />-   Mostrar u ocultar una columna<br />-   Ordenar por columna<br />-   Agrupar subprocesos<br />-   Inmovilizar o reanudar subprocesos<br />-   Marcar o demarcar un subproceso<br />-   Mostrar solo subprocesos marcados|  
  
## <a name="see-also"></a>Consulte también  
 [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Depuración de aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurar código de GPU](../debugger/debugging-gpu-code.md)
