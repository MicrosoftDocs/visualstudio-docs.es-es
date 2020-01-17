---
title: Análisis del uso de memoria para objetos .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886765"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Análisis del uso de memoria mediante la herramienta de asignación de objetos de .NET

Puede consultar la cantidad de memoria que está usando la aplicación y las rutas de acceso al código que asignan la mayor parte de la memoria mediante la herramienta de asignación de objetos de .NET.

Después de ejecutar la herramienta, puede ver las rutas de acceso de ejecución de la función en las que se asignan los objetos para remitir a la raíz del árbol de llamadas que ocupa la mayor parte de memoria.

## <a name="setup"></a>Programa de instalación

1. Abra el Generador de perfiles de rendimiento (**Alt+F2)** en Visual Studio.
2.  Active la casilla **Seguimiento de asignación de objetos de .NET**.

![Concentrador de diagnóstico](../profiling/media/diaghub.png "Concentrador de diagnóstico")

> [!NOTE]
> El proyecto de inicio se selecciona como **Destino de análisis** de forma predeterminada, pero esto se puede cambiar en el proceso en ejecución, los ejecutables, las aplicaciones en ejecución y las aplicaciones instaladas. Para ello, abra el menú desplegable **Cambiar destino** y seleccione la opción pertinente entre las disponibles.

   La herramienta de asignación de objetos de .NET no admite actualmente ejecutables en el menú desplegable. Tendrá que pasar por el sistema de proyecto exe para usar la herramienta. Para ello, cierre la solución actual (**Archivo** -> **Cerrar solución**) y, a continuación, presione **Archivo** -> **Abrir un proyecto o una solución** y seleccione el archivo. exe.

![Destino del análisis](../profiling/media/analysistarget.png "Destino del análisis")

3. Haga clic en el botón **Iniciar** para ejecutar la herramienta.

![Detener recopilación](../profiling/media/stopcollection.png "Detener colección")

4. Una vez que la herramienta empiece a ejecutarse, recorra el escenario deseado en la aplicación y, a continuación, presione **Detener colección** o cierre la aplicación para ver los datos.
5. Haga clic en la pestaña **Asignación**; debería ver una imagen similar a la que se muestra a continuación.

![Asignación](../profiling/media/allocation.png "Asignación")

¡Enhorabuena! Ahora puede analizar la asignación de memoria de los objetos.

## <a name="understand-your-data"></a>Comprensión de los datos

### <a name="collection"></a>Collection

![Colección](../profiling/media/collection.png "Collection")

La vista de colección le permite ver cuántos objetos se han recopilado durante la recolección de elementos no utilizados y cuántos se han conservado. Esta vista también proporciona algunos gráficos circulares para visualizar los objetos recopilados y conservados por tipo.

- La columna **Recopilados** muestra el número de objetos recopilados por el recolector de elementos no utilizados.
- La columna **Restantes** muestra el número de objetos que se conservaron tras la ejecución del recolector de elementos no utilizados.

### <a name="allocation"></a>Asignación

![Asignación expandida](../profiling/media/allocationexpanded.png "Asignación expandida")

La vista de asignación permite ver la ubicación de los objetos que asignan memoria y la cantidad de memoria que asignan dichos objetos.

- La columna **Nombre** es una lista de las distintas clases y estructuras que ocupan memoria. Cada elemento de la columna es un nodo que se puede expandir si hay elementos dentro de esa categoría que ocupan memoria. (Solo vista **Asignación**)
- La columna **Total (asignaciones)** muestra el número de objetos de un tipo de asignación determinado que ocupan memoria. (Vista **Asignación**, **Árbol de llamadas** y **Funciones**)
- La columna **Propio (asignaciones)** muestra el número de objetos dentro de un elemento individual que ocupa memoria. (Vista **Asignación**, **Árbol de llamadas** y **Funciones**)
- Las tres columnas se pueden ordenar. En el caso de la columna **Nombre**, los elementos se ordenan alfabéticamente (ya sea hacia delante o hacia atrás). Para **Total** y **Propio (asignaciones)** , puede ordenar numéricamente (ya sea de forma creciente o decreciente).
- De forma predeterminada, las columnas **Tamaño total (bytes)** y **Tamaño automático (bytes)** no están activadas. Para habilitarlas, haga clic con el botón derecho en las columnas **Nombre**, **Total** o **Propio (asignaciones)** y, a continuación, haga clic en las opciones **Tamaño total** y **Tamaño automático** para agregarlas al gráfico. Las dos columnas son similares a **Total (asignaciones)** y **Propio (asignaciones)** , salvo que, en lugar de mostrar el número de objetos que ocupan memoria, muestran la cantidad total de memoria en bytes que esos objetos ocupan. [Solo vista Asignación]

### <a name="call-tree"></a>Árbol de llamadas

![Árbol de llamadas](../profiling/media/calltree.png "Árbol de llamadas")

La vista **Árbol de llamadas** le permite ver las rutas de acceso de ejecución de funciones que contienen objetos que asignan mucha memoria.

- La columna **Nombre de la función** muestra el proceso o el nombre de la función que contiene objetos que asignan memoria según el nivel del nodo que se está inspeccionando.
- Las columnas **Total** y **Propio (asignaciones)** muestran la misma información que la vista **Asignación**.
- En la columna **Nombre del módulo**, se muestra el módulo que contiene la función o el proceso que se llama.

![Ruta de acceso activa](../profiling/media/hotpath.png "Ruta de acceso activa")

- El botón **Expandir ruta de acceso activa** resalta una ruta de ejecución de función que contiene muchos objetos que asignan memoria. El algoritmo comienza en un nodo de interés seleccionado por el usuario y resalta la ruta de acceso de la mayoría de las asignaciones, lo que guía al usuario en su investigación.
- El botón **Mostrar ruta de acceso activa** activa o desactiva los iconos de llama que indican qué nodo forma parte de la **ruta de acceso activa**.

### <a name="functions"></a>Funciones

![Funciones](../profiling/media/functions.png "Funciones")

La vista **Funciones** muestra los procesos, los módulos y las funciones que asignan memoria.

- En la columna **Nombre** se muestran los procesos como nodos de nivel superior. Debajo de los procesos están los módulos y, debajo de los módulos, están las funciones.
- Las columnas **Total** y **Propio (asignaciones)** muestran la misma información que la vista **Asignación**.

Las vistas **Asignaciones**, **Árbol de llamadas** y **Funciones** contienen las opciones **Mostrar solo mi código**, **Mostrar código nativo** y **Buscar**:

![Barra de filtros](../profiling/media/filterbar.png "Barra de filtros")

- **Mostrar solo mi código** contrae sistemas, plataformas y otros códigos que no son de usuario y en plataformas de tipo **[Código externo]** para que el código de usuario pueda centrarse. Para obtener más información, vea [Depurar solo código de usuario con Solo mi código](../debugger/just-my-code.md).
- **Mostrar código nativo** muestra código nativo en el destino de análisis, incluido el código que no es de usuario si se selecciona.
- El **cuadro de filtro** permite filtrar el nombre la columna **Nombre** o **Nombre de función** según el parámetro proporcionado. Simplemente escriba en el campo y la tabla debería filtrar para mostrar solo los tipos que contienen la cadena proporcionada.
