---
title: Análisis del uso de memoria para objetos .NET | Microsoft Docs
description: Consulte la cantidad de memoria que usa la aplicación y las rutas de acceso al código que asignan la mayor parte de la memoria mediante la herramienta de asignación de objetos de .NET.
ms.custom: SEO-VS-2020
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 4c0d8b02f867797317ff762e7a23bec042f93318
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801490"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Análisis del uso de memoria mediante la herramienta de asignación de objetos de .NET

Puede consultar la cantidad de memoria que usa la aplicación y las rutas de acceso al código que asignan la mayor parte de la memoria mediante la herramienta de asignación de objetos de .NET.

Tras ejecutar la herramienta, podrá ver las rutas de acceso de ejecución de función en las que se asignan objetos. A continuación, podrá hacer un seguimiento hasta la raíz del árbol de llamadas que más memoria consume.

## <a name="setup"></a>Programa de instalación

1. Seleccione **Alt + F2** para abrir el Generador de perfiles de rendimiento en Visual Studio.

1. Active la casilla **Seguimiento de asignación de objetos de .NET**.

   ![La herramienta para el seguimiento de asignación de objetos de Dotnet seleccionada](../profiling/media/dotnetalloctoolselected.png "La herramienta para el seguimiento de asignación de objetos de Dotnet seleccionada")

1. Seleccione el botón **Iniciar** para ejecutar la herramienta.

1. Una vez que se inicie la ejecución de la herramienta, repase el escenario del que desea generar perfiles en su aplicación. A continuación, seleccione **Detener recopilación** o cierre la aplicación para ver los datos.

   ![Una ventana que muestra Detener recopilación](../profiling/media/stopcollectionlighttheme.png "Una ventana que muestra Detener recopilación")

1. Seleccione la pestaña **Asignación**. Aparecerá contenido de la ventana similar al de la siguiente captura de pantalla.

   ![La pestaña Asignación](../profiling/media/allocationview.png "La pestaña Asignación")

Ahora puede analizar la asignación de memoria de los objetos.

Durante la recopilación, la herramienta de seguimiento puede ralentizar la aplicación de la que se generan perfiles. Si el rendimiento de la herramienta de seguimiento o la aplicación es lento, y si no es necesario que realice un seguimiento de todos los objetos, puede ajustar la frecuencia de muestreo. Para ello, seleccione el símbolo de engranaje situado junto a la herramienta de seguimiento en la página de resumen del generador de perfiles.

![Configuración de la herramienta de asignación de dotnet](../profiling/media/dotnetallocsettings.png "Configuración de la herramienta de asignación de dotnet")

Ajuste la frecuencia de muestreo a la que desee. Este cambio ayuda a acelerar el rendimiento de su aplicación durante la recopilación y el análisis.

![Una frecuencia de muestreo ajustada](../profiling/media/adjustedsamplingratedotnetalloctool.png "Una frecuencia de muestreo ajustada")

Para obtener más información sobre cómo aumentar la eficacia de la herramienta, consulte el artículo sobre cómo [optimizar la configuración del generador de perfiles](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Comprensión de los datos

![Un gráfico de la herramienta de asignación de dotnet](../profiling/media/graphdotnetalloc.png "Un gráfico de la herramienta de asignación de dotnet")

En la vista gráfica anterior, el gráfico superior muestra el número de objetos activos de la aplicación. El gráfico **diferencial de objetos** inferior muestra el cambio de porcentaje de los objetos de aplicación. Las barras rojas indican cuándo tuvo lugar la recolección de elementos no utilizados.

![Un gráfico filtrado de la hora de asignación de dotnet](../profiling/media/graphdotnetalloctimefiltered.png "Un gráfico filtrado de la hora de asignación de dotnet")

Puede filtrar los datos tabulares para mostrar la actividad durante solo un intervalo de tiempo especificado. También puede usar el zoom para ampliar o reducir el gráfico.

### <a name="allocation"></a>Asignación

![La vista Asignación expandida](../profiling/media/allocationexpandedlight.png "La vista Asignación expandida")

La vista **Asignación** muestra la ubicación de los objetos que asignan memoria y la cantidad de memoria que asignan dichos objetos.

- La columna **Tipo** es una lista de clases y estructuras que consumen memoria. Haga doble clic en un tipo para ver su seguimiento regresivo como un árbol de llamadas invertido. Solo en la vista **Asignación**, puede ver los elementos de la categoría seleccionada que consumen memoria.

- La columna **Asignaciones** muestra el número de objetos que consumen memoria dentro de una función o un tipo de asignación determinados. Esta columna solo aparece en las vistas **Asignación**, **Árbol de llamadas** y **Funciones**.

- Las columnas **Bytes** y **Tamaño medio (bytes)** no aparecen de forma predeterminada. Para mostrarlas, haga clic con el botón derecho en la columna **Tipo** o **Asignaciones** y, después, seleccione las opciones **Bytes** y **Tamaño medio (bytes)** para agregarlas al gráfico. 

   Las dos columnas son similares a **Total (asignaciones)** y **Propio (asignaciones)** , excepto en que muestran la cantidad de memoria consumida en lugar del número de objetos que consumen memoria. Estas columnas solo aparecen en la vista **Asignación**.

- En la columna **Nombre del módulo**, se muestra el módulo que contiene la función o el proceso que se llama.

Todas estas columnas se pueden ordenar. En el caso de las columnas **Tipo** y **Nombre del módulo**, puede ordenar los elementos alfabéticamente en orden ascendente o descendente. En el caso de **Asignaciones**, **Bytes** y **Tamaño medio (bytes)** , puede ordenar los elementos aumentando o reduciendo el valor numérico.

#### <a name="symbols"></a>Símbolos

Los siguientes símbolos aparecen en las pestañas **Asignación**, **Árbol de llamadas** y **Funciones**:

- ![El símbolo de tipo de valor](../profiling/media/valuetypeicon.png "El símbolo de tipo de valor"): un tipo de valor como un entero

- ![El símbolo de colección de tipo de valor](../profiling/media/valuetypecollectionicon.png "El símbolo de colección de tipo de valor"): una colección de tipo de valor como una matriz de enteros

- ![El símbolo de tipo de referencia](../profiling/media/referencetypeicon.png "El símbolo de tipo de referencia"): un tipo de referencia como una cadena

- ![El símbolo de colección de tipo de referencia](../profiling/media/referencetypecollectionicon.png "El símbolo de colección de tipo de referencia"): una colección de tipo de referencia como una matriz de cadenas.

### <a name="call-tree"></a>Árbol de llamadas

![La vista Árbol de llamadas](../profiling/media/calltreelight.png "La vista Árbol de llamadas")

La vista **Árbol de llamadas** muestra las rutas de acceso de ejecución de función que contienen objetos que asignan mucha memoria.

- La columna **Nombre de la función** muestra el proceso o nombre de la función que contiene objetos que asignan memoria. La presentación se basa en el nivel del nodo que inspecciona.
- Las columnas **Total (asignaciones)** y **Tamaño total (bytes)** muestran el número de objetos asignados y la cantidad de memoria que usa una función y todas las demás funciones a las que llama.
- Las columnas **Propio (asignaciones)** y **Tamaño automático (bytes)** muestran el número de objetos asignados y la cantidad de memoria que usa una sola función o un solo tipo de asignación seleccionados.
- La columna **Tamaño medio (bytes)** muestra la misma información que en la vista **Asignaciones**.
- En la columna **Nombre del módulo**, se muestra el módulo que contiene la función o el proceso que se llama.

   ![Una ruta de acceso activa expandida](../profiling/media/hotpathlight.png "Una ruta de acceso activa expandida")

- El botón **Expandir ruta de acceso activa** resalta una ruta de ejecución de función que contiene muchos objetos que asignan memoria. El algoritmo comienza en un nodo seleccionado por usted y resalta la ruta de acceso de la mayoría de las asignaciones, lo que le guía en su investigación.
- El botón **Mostrar ruta de acceso activa** muestra u oculta los iconos de llama que indican qué nodos forman parte de la ruta de acceso activa.

### <a name="functions"></a>Funciones

![La vista Funciones](../profiling/media/functionslight.png "La vista Funciones")

La vista **Funciones** muestra los procesos, los módulos y las funciones que asignan memoria.

- En la columna **Nombre** se muestran los procesos como nodos de nivel superior. Debajo de los procesos están los módulos y, debajo de los módulos, están las funciones.
- Estas columnas muestran la misma información que en las vistas **Asignación** y **Árbol de llamadas**:

  - **Total (asignaciones)**
  - **Propio (asignaciones)**
  - **Tamaño total (bytes)**
  - **Tamaño automático (bytes)**
  - **Tamaño medio (bytes)**

### <a name="collection"></a>Collection

![La vista de colección](../profiling/media/collectionlight.png "La vista de colección")

La vista de **colección** muestra cuántos objetos se han recopilado o conservado durante la recolección de elementos no utilizados. Esta vista también muestra gráficos circulares para visualizar los objetos recopilados y conservados por tipo.

- La columna **Recopilados** muestra el número de objetos recopilados por el recolector de elementos no utilizados.
- La columna **Restantes** muestra el número de objetos que se conservaron tras la ejecución del recolector de elementos no utilizados.

### <a name="filtering-tools"></a>Herramientas de filtrado

Las vistas **Asignaciones**, **Árbol de llamadas** y **Funciones** contienen las opciones **Mostrar solo mi código** y **Mostrar código nativo** y un cuadro de filtro.

- **Mostrar solo mi código** contrae sistemas, plataformas y otros códigos que no son de usuario en plataformas de tipo **[Código externo]** para que pueda centrarse en su código solamente. Para obtener más información, vea [Depurar solo código de usuario con Solo mi código](../debugger/just-my-code.md).
- **Mostrar código nativo** muestra código nativo en el destino de análisis y puede incluir código que no es de usuario.
- Con el cuadro de filtro, puede filtrar la columna **Nombre** o **Nombre de función** según el valor proporcionado. Escriba un valor de cadena en el cuadro. A continuación, en la tabla solo se muestran los tipos que contienen esa cadena.
