---
title: Tiempo de respuesta de página en una prueba de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: ba6a5b666777e692fe2c214f165c0bc1da7fee9d
ms.sourcegitcommit: 893c09d58562c378a4ba057bf2a06bde1c80df90
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2018
ms.locfileid: "35669134"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Cómo: Ver el tiempo de respuesta de la página web en una prueba de carga usando el Analizador de prueba de carga

El tiempo que tarda cada página web en cargarse se conoce como *tiempo de respuesta*. Al crear una prueba de rendimiento web, puede establecer un objetivo de tiempo de respuesta para cada solicitud de página web de la prueba de rendimiento web.

Si ejecuta una prueba de rendimiento web en condiciones de esfuerzo en una prueba de carga, podrá analizar la información siguiente de cada página:

-   El tiempo medio de respuesta de la página.

-   El porcentaje de iteraciones de la prueba que cumplen el tiempo de respuesta objetivo de la página.

-   Puede analizar los tiempos de respuesta de la página web utilizando la vista Tablas o la vista Gráficos del Analizador de prueba de carga:

-   Analizar los tiempos de respuesta de la página web en la vista de tablas

-   Analizar los tiempos de respuesta de la página web en la vista de gráficos

## <a name="view-response-time-data-in-a-table"></a>Ver datos de tiempo de respuesta en una tabla

### <a name="to-view-response-time-data-in-a-table"></a>Para ver los datos de tiempo de respuesta en una tabla

1.  En el Analizador de pruebas de carga, elija **Tablas** en la barra de herramientas para asegurarse de que se muestra la cuadrícula de la tabla.

2.  En el cuadro de lista desplegable **Tabla**, seleccione **Páginas**.

3.  Los datos de cada página se muestran en la cuadrícula. Normalmente se muestran las columnas siguientes.

    |Encabezado de columna|Descripción|
    |-|-|
    |**Página**|El nombre de la página Web.|
    |**Escenario**|El nombre del escenario. Importante si la prueba de rendimiento web contempla varios escenarios posibles.|
    |**Prueba**|El nombre de la prueba de rendimiento web. Importante si hay más de una prueba de rendimiento web en la prueba de carga.|
    |**Network**|El tipo de red.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Total**|El número total de solicitudes realizadas para la página web. Éste es el total de iteraciones en la prueba de carga.|
    |**Pro.**|Tiempo de respuesta promedio de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Min**|Tiempo de respuesta mínimo de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Valor medio**|Tiempo de respuesta mediana de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**90 %**|El percentil 90 del tiempo de respuesta. Esto indica que el 90 por ciento de las páginas respondieron más rápidamente que este número y el 10 por ciento de las páginas respondieron más lentamente.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**95 %**|El percentil 95 del tiempo de respuesta. Esto indica que el 95 por ciento de las páginas respondieron más rápidamente que este número y el 5 por ciento de las páginas respondieron más lentamente.|
    |**99 %**|El percentil 99 del tiempo de respuesta. Esto indica que el 99 por ciento de las páginas respondieron más rápidamente que este número y el 1 por ciento de las páginas respondieron más lentamente.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Max**|Tiempo de respuesta máximo de página.<br /><br /> De forma predeterminada, estos datos no se recopilan. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Desv. est.**|De forma predeterminada, no se recogen datos de la desviación estándar. Para recopilar estos datos, en el **Editor de pruebas de carga**, en el nodo **Parámetros de ejecución**, seleccione el nodo del parámetro de ejecución que quiere cambiar. En la ventana **Propiedades**, en la propiedad **Almacenamiento de detalles de tiempo**, seleccione **Todos los detalles individuales**.|
    |**Tiempo de la página**|El tiempo medio de respuesta de todas las solicitudes realizadas para la página web.|
    |**Objetivo**|El tiempo de la página definido como objetivo. Éste es un valor constante para la página. **Nota:** El objetivo de tiempo de la página solo se muestra si se ha definido el objetivo para la solicitud en la prueba de rendimiento web.|
    |**% que cumple el objetivo**|El porcentaje de las solicitudes realizadas para la página web que cumplen el objetivo de tiempo de respuesta.|

 Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Ver datos de tiempo de respuesta en un gráfico

Puede ver también los datos de tiempo de respuesta en un gráfico para determinar cómo cambian estos datos a lo largo del tiempo durante la prueba de carga. Esto es especialmente útil si el modelo de carga aumenta cuando se ejecuta la prueba, (como ocurre cuando se utiliza un modelo de carga por pasos). Para obtener más información, vea [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md).

### <a name="to-view-response-time-data-in-a-graph"></a>Para ver los datos de tiempo de respuesta en un gráfico

1.  En el Analizador de pruebas de carga, elija **Gráficos** en la barra de herramientas para asegurarse de que se muestra el gráfico.

2.  En la ventana **Contadores**, expanda el nodo del escenario en el que esté interesado, (por ejemplo, `Scenario1`).

3.  Expanda el nodo de la prueba de rendimiento web en el que esté interesado.

4.  Expanda el nodo **Páginas**.

5.  Expanda el nodo de la página en el que esté interesado.

6.  Haga clic con el botón derecho en **% de páginas que cumplen el objetivo** y, luego, elija **Mostrar contador en el gráfico**.

     Los datos se agregan al gráfico.

7.  (Opcional) Repita el paso anterior para el tiempo medio de la página, el objetivo de tiempo de respuesta de la página y el número total de páginas.

    > [!NOTE]
    > El objetivo de tiempo de respuesta de la página es constante.

 Para obtener más información, vea [Analizar los resultados de pruebas de carga en la vista Gráficos del Analizador de pruebas de carga](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Vea también

- [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Cómo: Obtener acceso a los resultados de pruebas de carga para su análisis](../test/how-to-access-load-test-results-for-analysis.md)
- [Analizar resultados de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)