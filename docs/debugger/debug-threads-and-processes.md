---
title: Herramientas para depurar procesos y subprocesos | Documentos de Microsoft
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb8c8abab1dc4b8f5778ed4b76688f8a3946e461
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888834"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Herramientas para depurar subprocesos y procesos en Visual Studio
*Subprocesos* y *procesos* son conceptos relacionados en informática. Los dos representan secuencias de instrucciones que se deben ejecutar en un orden concreto. Sin embargo, las instrucciones de subprocesos o procesos independientes se pueden ejecutar en paralelo.  
  
 Los procesos existen en el sistema operativo y corresponden a lo que los usuarios consideran programas o aplicaciones. Por otra parte, un subproceso existe dentro de un proceso. Por este motivo, los subprocesos se denominan a veces *procesos ligeros*. Cada proceso está compuesto por uno o más subprocesos.  
  
 La existencia de varios procesos permite a un equipo realizar más de una tarea a la vez. La existencia de varios subprocesos permite a un proceso dividir el trabajo que se va a realizar en paralelo. En un equipo con multiprocesadores, los procesos o subprocesos se pueden ejecutar en procesadores diferentes. Esto permite realizar un verdadero procesamiento en paralelo.  
  
 El procesamiento paralelo perfecto no siempre es posible. En ocasiones, los subprocesos deben sincronizarse. Es posible que un subproceso tenga que esperar al resultado de otro subproceso, o necesite acceso exclusivo a un recurso que otro subproceso esté utilizando. Los problemas de sincronización son una causa común de errores en las aplicaciones multiproceso. A veces, los subprocesos pueden acabar esperando un recurso que nunca está disponible. Esto da como resultado una condición denominada *interbloqueo*.  
  
 El depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona herramientas eficaces pero fáciles de usar para depurar subprocesos y procesos.  
  
## <a name="tools-and-features"></a>Herramientas y características
Las herramientas que necesita para usar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dependen de qué tipo de código está intentando depurar:

- Para los procesos, las herramientas principales son el **asociar al proceso** cuadro de diálogo, el **procesos** ventana y el **ubicación de depuración** barra de herramientas.

- Para los subprocesos, las herramientas principales para depurar subprocesos son la **subprocesos** (ventana), los marcadores de subprocesos en ventanas de código fuente, **pilas paralelas** ventana, **inspección paralela** ventana, y el **ubicación de depuración** barra de herramientas.  
  
- Para el código que usa el <xref:System.Threading.Tasks.Task> en el [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), el [Runtime de simultaneidad](/cpp/parallel/concrt/concurrency-runtime/) (código nativo), las herramientas principales para depurar aplicaciones multiproceso son el **Pilas paralelas** ventana, el **inspección paralela** ventana y el **tareas** ventana (la **tareas** ventana también admite la Objeto de compromiso de JavaScript).

- Para depurar subprocesos en la GPU, la herramienta principal es el **subprocesos de GPU** windows.  
  
  La tabla siguiente muestra la información disponible y las acciones que se pueden realizar en cada uno de estos lugares:  
  
|Interfaz de usuario|Información disponible|Acciones que puede realizar|  
|--------------------|---------------------------|-----------------------------|  
|**Asociar al proceso** cuadro de diálogo|Procesos disponibles que puede asociar:<br /><br /> : Nombre del proceso (.exe)<br />-Número de identificación proceso<br />: Título de la barra de menús<br />-Tipo (administrado v4.0; Administrador v2.0, v1.1, v1.0; x86; x64; IA64)<br />: Nombre de usuario (nombre de cuenta)<br />: Número de sesión|Seleccionar un proceso para asociar<br /><br /> Seleccionar un equipo remoto<br /><br /> Cambiar el tipo de transporte para conectar a equipos remotos.|  
|**Procesos** ventana|Procesos asociados:<br /><br /> : Nombre del proceso<br />-Número de identificación proceso<br />-Path para procesar .exe<br />: Título de la barra de menús<br />-Estado (Inter. En ejecución)<br />-Depuración (nativa, administrada y así sucesivamente.)<br />-Tipo de transporte (predeterminado, nativo sin autenticación)<br />-Calificador de transporte (equipo remoto)|Herramientas:<br /><br /> -Adjuntar<br />-Desasociar<br />: Finalizar<br /><br /> Menú contextual:<br /><br /> -Adjuntar<br />-Desasociar<br />-Desasociar cuando se detiene la depuración<br />: Finalizar|  
|**Subprocesos** ventana|Subprocesos en el proceso actual:<br /><br /> : Id. de subproceso<br />: Id. administrado<br />-Categoría (subproceso principal, subproceso de interfaz, controlador de llamadas a procedimientos remotos o subproceso de trabajo)<br />-Nombre del subproceso<br />-La ubicación donde se crea el subproceso<br />-Prioridad<br />: Máscara de afinidad<br />-Recuento de suspendidos<br />: Nombre del proceso<br />: Indicador de marca<br />-Indicador suspendido|Herramientas:<br /><br /> : Búsqueda<br />-Pila de llamadas buscar<br />-Marcar solo mi código<br />-Marcar selección de módulos personalizados<br />-Agrupar por<br />-Las columnas<br />-Expandir o Contraer pilas de llamadas<br />-Expandir o contraer grupos<br />-Inmovilizar o reanudar subprocesos<br /><br /> Menú contextual:<br /><br /> -Mostrar subprocesos en código fuente<br />-Cambiar a un subproceso<br />-Inmovilizar un subproceso en ejecución<br />-Reanudar un subproceso inmovilizado<br />-Marcar un subproceso para su estudio adicional<br />-Demarcar un subproceso<br />-Cambiar el nombre de un subproceso<br />-Mostrar y ocultar subprocesos<br /><br /> Otras acciones:<br /><br /> -Ver la pila de llamadas para un subproceso en una información sobre datos|  
|Ventana de código fuente|Indicadores de subproceso en el margen interno izquierdo indican uno o varios subprocesos (desactivado de forma predeterminada, se activan mediante el menú contextual en **subprocesos** ventana)|Menú contextual:<br /><br /> -Cambiar a un subproceso<br />-Marcar un subproceso para su estudio adicional<br />-Demarcar un subproceso|  
|**Ubicación de depuración** barra de herramientas|-Proceso actual<br />-Suspender la aplicación<br />-Reanudar la aplicación<br />-Suspender y cerrar la aplicación<br />-Subproceso actual<br />-Alternar estado marcado del subproceso actual<br />-Mostrar sólo subprocesos marcados<br />-Mostrar solo proceso actual<br />-Marco de pila actual|-Cambiar a otro proceso<br />-Suspender, reanudar o cerrar la aplicación<br />-Cambiar a otro subproceso en el proceso actual<br />-Cambiar a otro marco de pila en el subproceso actual<br />-Marcar o desmarcar subprocesos<br />-Mostrar sólo subprocesos marcados<br />-Muestra sólo el proceso actual|  
|**Pilas paralelas** ventana|-Las pilas de llamadas para varios subprocesos en una ventana.<br />-Marco de pila activo para cada subproceso.<br />-Los llamadores y destinatarios de cualquier método.|-Filtrar subprocesos especificados<br />-Cambiar a vista de tareas<br />-Marcar o desmarcar un subproceso<br />: Zoom|   
|**Inspección paralela** ventana|-La columna de marca, en el que puede marcar un subproceso que desea prestar especial atención a.<br />-La columna del marco, en el que una flecha indica el marco seleccionado.<br />: Una columna configurable que puede mostrar el equipo, proceso, mosaico, tarea y subproceso.|-Marcar o desmarcar un subproceso<br />-Mostrar sólo subprocesos marcados<br />-Cambiar marcos<br />-Ordenar una columna<br />-Subprocesos de grupo<br />-Inmovilizar o reanudar subprocesos<br />-exportar los datos en la ventana Inspección paralela| 
|**Tareas** ventana|: Permite ver información acerca de <xref:System.Threading.Tasks.Task> objetos, incluidos el identificador de tarea, estado de la tarea (programado, ejecución, en espera, interbloqueada) y qué subproceso se asigna a la tarea.<br />-Ubicación actual en la pila de llamadas.<br />-Pasado a la tarea en tiempo de creación de delegado|-Cambiar a tarea actual<br />-Marcar o desmarcar una tarea<br />-Inmovilizar o reanudar una tarea|  
|**Subprocesos de GPU** ventana|-La columna de marca, en el que puede marcar un subproceso que desea prestar especial atención a.<br />-La columna del subproceso actual, en el que una flecha amarilla indica que el subproceso actual.<br />-El **el número de subprocesos** columna, que muestra el número de subprocesos en la misma ubicación.<br />-El **línea** columna, que muestra la línea de código donde se encuentra cada grupo de subprocesos.<br />-El **dirección** columna, que muestra la dirección de la instrucción donde se encuentra cada grupo de subprocesos.<br />-El **ubicación** columna, que es la ubicación en el código de la dirección.<br />-El **estado** columna, que muestra si el subproceso está activo o bloqueado.<br />-El **icono** columna, que muestra el índice de los subprocesos del mosaico de la fila.|-Cambiar a un subproceso diferente<br />: Muestra un mosaico y subproceso determinados<br />-Mostrar u ocultar una columna<br />-Ordenar por columna<br />-Subprocesos de grupo<br />-Inmovilizar o reanudar subprocesos<br />-Marcar o desmarcar un subproceso<br />-Mostrar sólo subprocesos marcados|  
  
## <a name="see-also"></a>Vea también  
 [Adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Depurar aplicaciones multiproceso](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurar código de GPU](../debugger/debugging-gpu-code.md)