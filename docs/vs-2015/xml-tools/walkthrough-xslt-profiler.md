---
title: 'Tutorial: generador de perfiles XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669526"
---
# <a name="walkthrough-xslt-profiler"></a>Tutorial: Generador de perfiles XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El generador de perfiles XSLT crea informes de rendimiento de XSLT detallados que ayudan a medir, evaluar y solucionar problemas relacionados con el rendimiento en el código XSLT. El generador de perfiles XSLT incluye sugerencias útiles para la optimización de hojas de estilos XSL y XSLT. Para las aplicaciones XSLT que exigen el máximo rendimiento, esta herramienta puede ser esencial.

## <a name="prerequisites"></a>Prerrequisitos
 Los procedimientos del tutorial siguiente requieren Visual Studio 2010 y la versión 4.0 de .NET Framework. El generador de perfiles XSLT solo está disponible en Microsoft Visual Studio Team System con las herramientas de generación de perfiles instaladas.

### <a name="create-the-performance-report"></a>Cree el informe de rendimiento

1. Abra un documento XSLT en Visual Studio.

2. Haga clic en la opción **generar Perfil de XSLT** que está disponible en el menú XML.

3. Proporcione un documento XML de entrada. Si no hay ningún documento XML abierto, se le solicitará que lo abra.

4. Se inicia el análisis y una barra de progreso muestra el progreso dentro del editor.

5. El resultado XSLT se muestra en el panel de resultados.

6. Una vez finalizada la sesión de rendimiento, compruebe el informe de rendimiento. Los datos guardados en un informe de rendimiento permiten ver y analizar el rendimiento de XSLT.

### <a name="get-all-the-available-views"></a>Obtenga todas las vistas disponibles

1. Haga clic en la lista desplegable **Vista actual** para obtener todas las vistas disponibles.

2. Seleccione la opción **Vista de resumen** en la lista desplegable **Vista actual**. De forma predeterminada, en la **Vista de resumen** se muestra un informe de rendimiento. Esta vista es un punto de partida para determinar las problemas de rendimiento con los documentos XSLT. La **Vista de resumen** incluye los puntos de datos siguientes:

    - Funciones más llamadas

    - Funciones con la mayor parte del trabajo individual

    - Funciones que tardan más tiempo en ejecutarse

3. De forma predeterminada, hay tres columnas para cada punto de datos: el nombre de la función, el número de llamadas en valor absoluto y un valor del porcentaje de esa función con respecto al total de llamadas a funciones. Desde cada punto de datos de la **Vista de resumen**, puede desplazarse a vistas más detalladas haciendo clic con el botón derecho en los puntos de datos de la función.

4. Seleccione la opción de la **Vista de función** en la lista desplegable **Vista actual**. La **Vista de función** muestra las funciones a las que se llama durante la generación de perfiles. Puede ordenar los datos si hace clic en el nombre de una columna. Las columnas que se muestran de forma predeterminada son:

    - **Nombre de la función**

    - **Tiempo inclusivo transcurrido**

    - **Tiempo exclusivo transcurrido**

    - **Tiempo inclusivo de aplicación**

    - **Tiempo exclusivo de aplicación**

    - **Número de llamadas**

5. Todas las columnas de tiempo se muestran en valores absolutos y en porcentajes. El término **Exclusivo** hace referencia al tiempo total que una función dedicó a ejecutarse, excluyendo el tiempo empleado por otras funciones llamadas durante la ejecución de dicha función.

6. El término **Inclusivo** hace referencia al tiempo total que una función dedicó a ejecutarse, incluyendo el tiempo de ejecución empleado por las funciones llamadas y por cualquier otra función llamada a su vez por estas.

### <a name="select-callercallee-view"></a>Seleccione la vista Llamador y destinatario

1. Seleccione la vista **Llamador y destinatario** en la lista desplegable **Vista actual**.

2. La vista **Llamador y destinatario** tiene las tres partes siguientes:

    - **Funciones que llamaron**: todas las funciones que llamaron a una función determinada se muestran en la parte superior de la vista.

    - **Función actual**: la función a la que se llamó se muestra en la parte central de la vista.

    - **Funciones a las que llamó** : todas las funciones a las que llamó la función determinada se enumeran en la parte inferior de la vista.

3. Si una función denominada `SyncToNavigator` aparece en la parte central de la vista, todas las funciones que han llamado a la función `SyncToNavigator` aparecen en la parte superior de la vista, y todas las funciones a las que ha llamado `SyncToNavigator` aparecen en la parte inferior de la vista.

4. Puede cambiar la función de la parte central de la vista haciendo doble clic en cualquiera de las funciones mostradas en las otras dos partes de la vista. A continuación, la vista se actualiza automáticamente para reflejar los cambios.

5. También puede ordenar los datos haciendo clic en los nombres de las columnas.

### <a name="select-calltree-view"></a>Seleccione la vista Árbol de llamadas

1. Seleccione la vista **Árbol de llamadas** en la lista desplegable **Vista actual**. Esta vista es una vista de árbol de la ejecución del programa.

2. La vista **Árbol de llamadas** muestra el nombre del proceso como raíz del árbol. Las funciones son los nodos del árbol. Esta vista le permite obtener información detallada sobre seguimientos de llamada concretos y analizar cuáles tienen el mayor impacto sobre el rendimiento. La vista es similar a la vista **Pila de llamadas** disponible durante la depuración. Además de las columnas de la **vista de función**, en la vista **Árbol de llamadas** existe una columna adicional para mostrar el **Nombre del módulo**.

3. Seleccione **Marcas** en la lista desplegable **Vista actual**.

4. Con el generador de perfiles XSLT, hay marcas que aparecen en la secuencia de colección de datos con un comentario asociado. Las marcas son lugares en el código que tienen contadores. Cuando se indica al generador de perfiles XSLT que recopile los contadores de rendimiento de XSLT, estos se recopilan cada vez que se ejecuta una de dichas marcas. Los datos se muestran en una tabla que contiene el **Id. de marca**, el **Nombre de marca** (**Programa de inicio**, **Programa de finalización**) y la **Marca de tiempo**. Las marcas no se agregan y se muestran en orden cronológico en la vista **Marcas** del informe de rendimiento.

### <a name="select-modules-in-the-current-view"></a>Seleccione Módulos en la vista actual

1. Seleccione **Módulos** en la lista desplegable **Vista actual**.

2. La vista de módulos es una lista plana de todas las funciones agregadas al nivel de módulo. Expanda o contraiga el nombre del módulo para mostrar o cerrar la vista de los datos de rendimiento del módulo. Puede ordenar los datos si hace clic en el nombre de una columna. De forma predeterminada, hay valores absolutos y porcentajes para **Tiempo inclusivo transcurrido**, **Tiempo exclusivo transcurrido**, **Tiempo inclusivo de aplicación**, **Tiempo exclusivo de aplicación** y **Número de llamadas**.

3. Seleccione **Proceso** en la lista desplegable **Vista actual**.

4. La vista Proceso muestra una tabla que incluye el **Id. de proceso**, el **Nombre de proceso**, la **Hora de inicio** y la **Hora de finalización**. Puede ordenar los datos haciendo clic en los nombres de las columnas.

## <a name="see-also"></a>Consulte también
 [Tutorial: uso de la jerarquía de XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
