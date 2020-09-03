---
title: Tiempo de respuesta de página en una prueba de carga
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1affda002290a191fde6d5115094a2185ac8bfcb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85287056"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Procedimiento para ver el tiempo de respuesta de la página web en una prueba de carga mediante el Analizador de pruebas de carga

El tiempo que tarda cada página web en cargarse se conoce como *tiempo de respuesta*. Al crear una prueba de rendimiento web, puede establecer un objetivo de tiempo de respuesta para cada solicitud de página web de la prueba de rendimiento web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Si ejecuta una prueba de rendimiento web en condiciones de carga en una prueba de carga, podrá analizar la información siguiente de cada página:

- El tiempo medio de respuesta de la página.

- El porcentaje de iteraciones de la prueba que cumplen el tiempo de respuesta objetivo de la página.

- Puede analizar los tiempos de respuesta de la página web mediante las vistas Tablas o Gráficos del **Analizador de pruebas de carga**:

- Análisis de los tiempos de respuesta de la página web en la vista Tablas

- Análisis de los tiempos de respuesta de la página web en la vista Gráficos

## <a name="view-response-time-data-in-a-table"></a>Ver datos de tiempo de respuesta en una tabla

1. En el **Analizador de pruebas de carga**, elija **Tablas** en la barra de herramientas para asegurarse de que se muestre la cuadrícula de tabla.

2. En el cuadro de lista desplegable **Tabla**, seleccione **Páginas**.

3. Los datos de cada página se muestran en la cuadrícula. Normalmente se muestran las columnas siguientes.

   |Encabezado de columna|Descripción|
   |-|-|
   |**Página**|El nombre de la página web.|
   |**Escenario**|El nombre del escenario. Importante si la prueba de rendimiento web contempla varios escenarios posibles.|
   |**Prueba**|El nombre de la prueba de rendimiento web. Importante si hay más de una prueba de rendimiento web en la prueba de carga.|
   |**Network**|El tipo de red.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Total**|El número total de solicitudes realizadas de la página web. Éste es el total de iteraciones en la prueba de carga.|
   |**Pro.**|Tiempo de respuesta promedio de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Min**|Tiempo de respuesta mínimo de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Valor medio**|Tiempo de respuesta mediana de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**90 %**|El percentil 90 del tiempo de respuesta. Esto indica que el 90 por ciento de las páginas respondieron más rápidamente que este número y el 10 por ciento de las páginas respondieron más lentamente.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**95 %**|El percentil 95 del tiempo de respuesta. Esto indica que el 95 por ciento de las páginas respondieron más rápidamente que este número y el 5 por ciento de las páginas respondieron más lentamente.|
   |**99 %**|El percentil 99 del tiempo de respuesta. Esto indica que el 99 por ciento de las páginas respondieron más rápidamente que este número y el 1 por ciento de las páginas respondieron más lentamente.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Max**|Tiempo de respuesta máximo de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Desv. est.**|De forma predeterminada, no se recogen datos de la desviación estándar. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
   |**Tiempo de la página**|El tiempo medio de respuesta de todas las solicitudes realizadas de la página web.|
   |**Objetivo**|El tiempo de la página definido como objetivo. Éste es un valor constante para la página. **Nota:**  El objetivo de tiempo de la página solo se muestra si se ha definido el objetivo para la solicitud en la prueba de rendimiento web.|
   |**% que cumple el objetivo**|El porcentaje de las solicitudes realizadas para la página web que cumplen el objetivo de tiempo de respuesta.|

   Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Ver datos de tiempo de respuesta en un gráfico

Puede ver también los datos de tiempo de respuesta en un gráfico para determinar cómo cambian estos datos a lo largo del tiempo durante la prueba de carga. Esto es especialmente útil si el modelo de carga aumenta cuando se ejecuta la prueba, (como ocurre cuando se utiliza un modelo de carga por pasos). Para obtener más información, vea [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Para ver los datos de tiempo de respuesta en un gráfico:

1. En el **Analizador de pruebas de carga**, elija **Gráficos** en la barra de herramientas para asegurarse de que se muestre el gráfico.

2. En la ventana **Contadores**, expanda el nodo del escenario en el que esté interesado, (por ejemplo, `Scenario1`).

3. Expanda el nodo de la prueba de rendimiento web en el que esté interesado.

4. Expanda el nodo **Páginas**.

5. Expanda el nodo de la página en el que esté interesado.

6. Haga clic con el botón derecho en **% de páginas que cumplen el objetivo** y, luego, elija **Mostrar contador en el gráfico**.

    Los datos se agregan al gráfico.

7. (Opcional) Repita el paso anterior para  **Tiempo promedio de la página**, **Objetivo de tiempo de respuesta** y **Total de páginas**.

   > [!NOTE]
   > **Objetivo de tiempo de respuesta** es constante.

   Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Vea también

- [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Cómo: Acceder a los resultados de pruebas de carga para el análisis](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizar los resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
