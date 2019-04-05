---
title: 'Tutorial: XSLT Profiler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1fd5f581308a677f1de7cd9311d4a8649b3ea4fc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987429"
---
# <a name="walkthrough-xslt-profiler"></a>Tutorial: Generador de perfiles XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El generador de perfiles XSLT crea informes de rendimiento de XSLT detallados que ayudan a medir, evaluar y solucionar problemas relacionados con el rendimiento en el código XSLT. El generador de perfiles XSLT incluye sugerencias útiles para la optimización de hojas de estilos XSL y XSLT. Para las aplicaciones XSLT que exigen el máximo rendimiento, esta herramienta puede ser esencial.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Los procedimientos del tutorial siguiente requieren Visual Studio 2010 y la versión 4.0 de .NET Framework. El generador de perfiles XSLT solo está disponible en Microsoft Visual Studio Team System con las herramientas de generación de perfiles instaladas.  
  
### <a name="create-the-performance-report"></a>Cree el informe de rendimiento  
  
1.  Abra un documento XSLT en Visual Studio.  
  
2.  Haga clic en el **perfil XSLT** opción que está disponible en el menú XML.  
  
3.  Proporcione un documento XML de entrada. Si no hay ningún documento XML abierto, se le solicitará que lo abra.  
  
4.  Se inicia el análisis y una barra de progreso muestra el progreso dentro del editor.  
  
5.  El resultado XSLT se muestra en el panel de resultados.  
  
6.  Una vez finalizada la sesión de rendimiento, compruebe el informe de rendimiento. Los datos guardados en un informe de rendimiento permiten ver y analizar el rendimiento de XSLT.  
  
### <a name="get-all-the-available-views"></a>Obtenga todas las vistas disponibles  
  
1.  Haga clic en el **vista actual** lista desplegable para obtener todas las vistas disponibles.  
  
2.  Seleccione el **vista resumen** opción el **vista actual** lista desplegable. De forma predeterminada, se muestra un informe de rendimiento en el **vista resumen**. Esta vista es un punto de partida para determinar las problemas de rendimiento con los documentos XSLT. El **vista resumen** enumera los puntos de datos siguientes:  
  
    -   Funciones más llamadas  
  
    -   Funciones con la mayor parte del trabajo individual  
  
    -   Funciones que tardan más tiempo en ejecutarse  
  
3.  De forma predeterminada, hay tres columnas para cada punto de datos: el nombre de la función, el número de llamadas en valor absoluto y un valor del porcentaje de esa función con respecto al total de llamadas a funciones. Desde datos de cada punto en el **vista resumen**, puede navegar a vistas más detalladas haciendo clic en los puntos de datos de la función.  
  
4.  Seleccione el **vista función** opción el **vista actual** lista desplegable. El **vista función** enumera las funciones que se llama durante la generación de perfiles. Puede ordenar los datos si hace clic en el nombre de una columna. Las columnas que se muestran de forma predeterminada son:  
  
    -   **Nombre de la función**  
  
    -   **Tiempo inclusivo transcurrido**  
  
    -   **Tiempo exclusivo transcurrido**  
  
    -   **Tiempo inclusivo de aplicación**  
  
    -   **Tiempo exclusivo de aplicación**  
  
    -   **Número de llamadas**  
  
5.  Todas las columnas de tiempo se muestran en valores absolutos y en porcentajes. El término **exclusivo** se refiere al tiempo total de una función dedicó a ejecutarse, excluyendo el tiempo empleado por otras funciones llamadas durante la ejecución de esta función.  
  
6.  El término **Inclusive** se refiere al tiempo total que una función dedicó a ejecutarse, incluyendo el tiempo de ejecución de todas las funciones llamadas y si llama a cualquiera de estas otras funciones.  
  
### <a name="select-callercallee-view"></a>Seleccione la vista Llamador y destinatario  
  
1.  Seleccione **llamador y destinatario** ver en el **vista actual** lista desplegable.  
  
2.  El **llamador y destinatario** vista tiene las siguientes tres partes distintas:  
  
    -   **Funciones que llamaron a**: Todas las funciones que llamaron a una función determinada se muestran en la parte superior de la vista.  
  
    -   **Función actual**: La función concreta que se llamó se muestra en la parte central de la vista.  
  
    -   **Las funciones llamadas por** : Se muestran todas las funciones a las que llamó la función concreta en la parte inferior de la vista.  
  
3.  Si una función denominada `SyncToNavigator` aparece en la parte central de la vista, todas las funciones que han llamado a la función `SyncToNavigator` aparecen en la parte superior de la vista, y todas las funciones a las que ha llamado `SyncToNavigator` aparecen en la parte inferior de la vista.  
  
4.  Puede cambiar la función de la parte central de la vista haciendo doble clic en cualquiera de las funciones mostradas en las otras dos partes de la vista. A continuación, la vista se actualiza automáticamente para reflejar los cambios.  
  
5.  También puede ordenar los datos haciendo clic en los nombres de las columnas.  
  
### <a name="select-calltree-view"></a>Seleccione la vista Árbol de llamadas  
  
1.  Seleccione **vista árbol de llamadas** en el **vista actual** lista desplegable. Esta vista es una vista de árbol de la ejecución del programa.  
  
2.  El **vista árbol de llamadas** muestra la raíz del árbol como el nombre del proceso. Las funciones son los nodos del árbol. Esta vista le permite obtener información detallada sobre seguimientos de llamada concretos y analizar cuáles tienen el mayor impacto sobre el rendimiento. La vista es similar a la **vista de la pila de llamadas** disponible durante la depuración. Además de las columnas en el **vista función**, en el **vista árbol de llamadas**, hay una columna adicional para mostrar el **nombre del módulo**.  
  
3.  Seleccione **marcas** en el **vista actual** lista desplegable.  
  
4.  Con el generador de perfiles XSLT, hay marcas que aparecen en la secuencia de colección de datos con un comentario asociado. Las marcas son lugares en el código que tienen contadores. Cuando se indica al generador de perfiles XSLT que recopile los contadores de rendimiento de XSLT, estos se recopilan cada vez que se ejecuta una de dichas marcas. Los datos se muestran en una tabla que contiene el **Id. de marca**, **nombre de la marca** (**iniciar programa**, **programa final**) y el  **Marca de tiempo**. Las marcas no se agregan y se muestran en orden cronológico en el **vista marcas** del informe de rendimiento.  
  
### <a name="select-modules-in-the-current-view"></a>Seleccione Módulos en la vista actual  
  
1.  Seleccione **módulos** en el **vista actual** lista desplegable.  
  
2.  La vista de módulos es una lista plana de todas las funciones agregadas al nivel de módulo. Expanda o contraiga el nombre del módulo para mostrar o cerrar la vista de los datos de rendimiento del módulo. Puede ordenar los datos si hace clic en el nombre de una columna. De forma predeterminada, hay valores absolutos y porcentajes para **tiempo inclusivo transcurrido**, **tiempo exclusivo transcurrido**, **tiempo inclusivo de aplicación**, **Tiempo exclusivo de aplicación**, y **número de llamadas**.  
  
3.  Seleccione **proceso** en el **vista actual** lista desplegable.  
  
4.  La vista proceso muestra una tabla que incluye la **Id. de proceso**, **nombre del proceso**, **hora de inicio**y el **hora de finalización**. Puede ordenar los datos haciendo clic en los nombres de las columnas.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Uso de la jerarquía XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
