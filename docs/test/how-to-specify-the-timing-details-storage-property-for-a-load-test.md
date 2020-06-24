---
title: Propiedad Almacenamiento de detalles de tiempo de un parámetro de ejecución de una prueba de carga
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0225ae23ed141b317d4424da573593d446766f43
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287316"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>Cómo: Especificar la propiedad Almacenamiento de detalles de tiempo de un parámetro de ejecución de una prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar la configuración de modo que satisfaga las necesidades y los objetivos de la prueba.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Puede editar el valor de la propiedad **Almacenamiento de detalles de tiempo** de los parámetros de ejecución en la ventana **Propiedades**. La propiedad **Almacenamiento de detalles de tiempo** se puede establecer en cualquiera de las opciones siguientes:

- **Todos los detalles individuales:** recopila y almacena datos de tiempo individuales de cada prueba, transacción y página emitidos durante la prueba.

  > [!NOTE]
  > La opción **Todos los detalles individuales** debe estar seleccionada para permitir que aparezcan los datos de usuarios virtuales en los resultados de pruebas de carga. Para obtener más información, vea [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

- **Ninguno:** no recopila detalles de tiempo individuales. Sin embargo, los valores promedio todavía están disponibles.

- **Solo estadísticas:** almacena datos de tiempo individuales, pero solo como datos de percentil. De este modo, se ahorra espacio.

  **Consideraciones sobre la propiedad Almacenamiento de detalles de tiempo**

  Si la propiedad **Almacenamiento de detalles de tiempo** está habilitada, se almacena el tiempo que tarda en ejecutarse cada prueba, transacción y página individual durante la prueba de carga en el repositorio de resultados de pruebas de carga. Esto permite mostrar datos como percentiles 90 y 95 en el **Analizador de pruebas de carga** en las tablas **Pruebas**, **Transacciones** y **Páginas**.

  Si la propiedad **Almacenamiento de detalles de tiempo** está habilitada, al establecer su valor en **Solo estadísticas** o en **Todos los detalles individuales**, se cronometran todas las pruebas, páginas y transacciones individuales y los datos de percentiles se calculan a partir de los datos de tiempo individuales. La diferencia es que con la opción **Solo estadísticas**, después de calcular los datos de percentiles, los datos de tiempo individuales se eliminan del repositorio. Esto reduce la cantidad de espacio necesario en el repositorio cuando se usan detalles de tiempo. Pero es posible que quiera procesar los datos detallados de tiempo de otras maneras mediante las herramientas de SQL, en cuyo caso se debe usar la opción **Todos los detalles individuales** para que los datos detallados de tiempo estén disponibles para ese procesamiento. Además, si establece la propiedad en **AllIndividualDetails**, puede analizar la actividad de los usuarios virtuales mediante el **Diagrama de actividad del usuario virtual** del **Analizador de pruebas de carga** una vez que se complete la ejecución de la prueba de carga. Para obtener más información, vea [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

  La cantidad de espacio necesario en el repositorio de resultados de pruebas de carga para almacenar los detalles de tiempo puede ser muy grande, sobre todo si se trata de pruebas de carga de ejecución prolongada. Además, se tarda más tiempo en almacenar estos datos en dicho repositorio al final de la prueba de carga, ya que los datos se almacenan en los agentes de prueba de carga hasta que finaliza la ejecución de la prueba, momento en el cual los datos se almacenan en el repositorio. De forma predeterminada, la propiedad **Almacenamiento de detalles de tiempo** está habilitada. Si esto supone algún problema para el entorno de pruebas, puede establecer **Almacenamiento de detalles de tiempo** en **Ninguno**.

  Los datos de detalles de tiempo se almacenan en el archivo *LoadTestItemResults.dat* durante la ejecución y se devuelven al controlador cuando la prueba de carga se ha completado. En el caso de una prueba de carga de ejecución prolongada, el tamaño del archivo es grande. Si no hay espacio en disco suficiente en el equipo del agente, esto será un problema.

  Si va a actualizar un proyecto de una versión anterior de Visual Studio Load Test, use el procedimiento siguiente para habilitar la recopilación de detalles completos.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Para configurar la propiedad Almacenamiento de detalles de tiempo en una prueba de carga

1. Abra una prueba de carga en el Editor de prueba de carga.

2. Expanda el nodo **Parámetros de ejecución** de la prueba de carga.

3. Elija el parámetro de ejecución que quiera configurar, por ejemplo, **Run Settings1[Active]** .

4. Abra la ventana **Propiedades**. En el menú **Ver**, seleccione la ventana **Propiedades**.

5. En la categoría **Resultados**, elija la propiedad **Almacenamiento de detalles de tiempo** y seleccione **Todos los detalles individuales**.

     Después de haber configurado el valor **Todos los detalles individuales** de la propiedad **Almacenamiento de detalles de tiempo**, puede ejecutar la prueba de carga y ver el **Diagrama de actividad del usuario virtual**. Para obtener más información, vea [Cómo: Analizar lo que hacen los usuarios virtuales durante una prueba de carga mediante el Diagrama de actividad de los usuarios virtuales](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Vea también

- [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Tutorial: Usar el Diagrama de actividad del usuario virtual para aislar problemas de rendimiento](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
