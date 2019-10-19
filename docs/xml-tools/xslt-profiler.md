---
title: Rendimiento XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2866e9b19ea2b79bf8435d81c93443bb20ff4fec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645907"
---
# <a name="the-xslt-profiler"></a>El generador de perfiles XSLT

El generador de perfiles XSLT crea informes de rendimiento de XSLT detallados que ayudan a medir, evaluar y solucionar problemas relacionados con el rendimiento en el código XSLT. El generador de perfiles XSLT incluye sugerencias útiles para la optimización de hojas de estilos XSL y XSLT. Para las aplicaciones XSLT que exigen el máximo rendimiento, esta herramienta puede ser esencial.

El generador de perfiles XSLT forma parte de Visual Studio y está disponible en el menú **XML** .

![Generador de perfiles XSLT](../xml-tools/media/profile-xslt-menu.png)

> [!NOTE]
> El generador de perfiles XSLT solo está disponible en la edición Enterprise de Visual Studio.

## <a name="create-a-performance-report"></a>Crear un informe de rendimiento

1. Abra un documento XSLT en Visual Studio.

2. En la barra de menús, elija **XML**  > **perfil XSLT**.

3. Proporcione un documento XML de entrada. Si no hay ningún documento XML abierto, se le solicitará que lo abra.

   Se inicia el análisis y una barra de progreso muestra el progreso dentro del editor. La salida XSLT también está visible.

4. Una vez finalizada la sesión de rendimiento, compruebe el informe de rendimiento para analizar el rendimiento de XSLT.

## <a name="get-all-available-views"></a>Obtener todas las vistas disponibles

1. Haga clic en la lista desplegable **vista actual** para obtener todas las vistas disponibles.

2. Seleccione la opción **vista de Resumen** en la lista desplegable **vista actual** . De forma predeterminada, se muestra un informe de rendimiento en la **vista de Resumen**. Esta vista es un punto de partida para determinar las problemas de rendimiento con los documentos XSLT. La **vista Resumen** muestra los siguientes puntos de datos:

   - Funciones más llamadas

   - Funciones con la mayor parte del trabajo individual

   - Funciones que tardan más tiempo en ejecutarse

   De forma predeterminada, hay tres columnas para cada punto de datos: el nombre de la función, el número de llamadas en valor absoluto y un valor del porcentaje de esa función con respecto al total de llamadas a funciones. En cada punto de datos de la **vista de Resumen**, puede desplazarse a vistas más detalladas haciendo clic con el botón derecho en los puntos de datos de la función.

3. Seleccione la opción **vista de función** en la lista desplegable **vista actual** . La **vista de función** muestra las funciones a las que se llama durante la generación de perfiles. Puede ordenar los datos si hace clic en el nombre de una columna. Las columnas que se muestran de forma predeterminada son:

    - **Nombre de la función**

    - **Tiempo inclusivo transcurrido**

    - **Tiempo exclusivo transcurrido**

    - **Tiempo inclusivo de aplicación**

    - **Tiempo exclusivo de aplicación**

    - **Número de llamadas**

   Todas las columnas de tiempo se muestran en valores absolutos y en porcentajes. El término **exclusivo** hace referencia al tiempo total que una función dedicó a ejecutarse en exclusiva el tiempo empleado por otras funciones llamadas durante la ejecución de esta función.

   El término **inclusivo** hace referencia al tiempo total que una función dedicó a ejecutarse, incluido el tiempo de ejecución de todas las funciones a las que llamó y si cualquiera de estas llamadas a funciones llama a otras funciones.

## <a name="select-callercallee-view"></a>Seleccione la vista Llamador y destinatario

Seleccione la vista **llamador y destinatario** en la lista desplegable **vista actual** . La vista **llamador y destinatario** tiene las tres partes distintas siguientes:

- **Funciones que llamaron**a: todas las funciones que llamaron a una función determinada se enumeran en la parte superior de la vista.

- **Función actual**: la función determinada a la que se llamó se muestra en la parte central de la vista.

- **Funciones a las que llamó**: todas las funciones a las que llamó la función determinada se enumeran en la parte inferior de la vista.

Si una función denominada `SyncToNavigator` aparece en la parte central de la vista, todas las funciones que han llamado a la función `SyncToNavigator` aparecen en la parte superior de la vista, y todas las funciones a las que ha llamado `SyncToNavigator` aparecen en la parte inferior de la vista.

- Puede cambiar la función de la parte central de la vista haciendo doble clic en cualquiera de las funciones mostradas en las otras dos partes de la vista. A continuación, la vista se actualiza automáticamente para reflejar los cambios.

- También puede ordenar los datos haciendo clic en los nombres de las columnas.

## <a name="select-call-tree-view"></a>Seleccionar vista de árbol de llamadas

- Seleccione la **vista árbol de llamadas** en la lista desplegable **vista actual** . Esta vista es una vista de árbol de la ejecución del programa.

   La **vista árbol de llamadas** muestra la raíz del árbol como el nombre del proceso. Las funciones son los nodos del árbol. Esta vista le permite obtener información detallada sobre seguimientos de llamada concretos y analizar cuáles tienen el mayor impacto sobre el rendimiento. La vista es similar a la **vista pila de llamadas** disponible durante la depuración. Además de las columnas de la **vista de función**, en la **vista árbol de llamadas**hay una columna adicional para mostrar el nombre del **módulo**.

- Seleccione **marcas** en la lista desplegable **vista actual** .

   Con el generador de perfiles XSLT, hay marcas que se muestran en la secuencia de recopilación de datos con un comentario asociado. Las marcas son lugares en el código que tienen contadores. Cuando se indica al generador de perfiles XSLT que recopile los contadores de rendimiento de XSLT, estos se recopilan cada vez que se ejecuta una de dichas marcas. Los datos se muestran en una tabla que contiene **el identificador de marca**, el nombre de **marca** (**programa de inicio**, programa de **finalización**) y la **marca de tiempo**. Las marcas no se agregan y se muestran en orden cronológico en la **vista marcas** del informe de rendimiento.

## <a name="select-modules-in-the-current-view"></a>Seleccione Módulos en la vista actual

- Seleccione **módulos** en la lista desplegable **vista actual** .

   La vista de módulos es una lista plana de todas las funciones agregadas al nivel de módulo. Expanda o contraiga el nombre del módulo para mostrar o cerrar la vista de los datos de rendimiento del módulo. Puede ordenar los datos si hace clic en el nombre de una columna. De forma predeterminada, hay valores absolutos y números de porcentaje para **el tiempo inclusivo transcurrido**, **tiempo exclusivo transcurrido**, **tiempo inclusivo de aplicación**, tiempo **exclusivo de aplicación**y **número de llamadas**.

- Seleccione **proceso** en la lista desplegable **vista actual** .

   La vista proceso muestra una tabla que incluye el **identificador del proceso**, el **nombre del proceso**, la **hora de inicio**y la **hora de finalización**. Puede ordenar los datos haciendo clic en los nombres de las columnas.

## <a name="see-also"></a>Vea también

- [Tutorial: uso de la jerarquía de XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)