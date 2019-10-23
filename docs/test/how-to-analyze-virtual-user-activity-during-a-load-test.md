---
title: Análisis de la actividad de los usuarios virtuales durante las pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- virtual user activity chart, viewing
ms.assetid: 8bda19b3-91c1-4daf-b6c7-09108bddadff
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 97abfe3740ea9209768e82eca1b269cd0a381233
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644173"
---
# <a name="how-to-analyze-what-virtual-users-are-doing-during-a-load-test-using-the-virtual-user-activity-chart"></a>Procedimiento para analizar lo que hacen los usuarios virtuales durante una prueba de carga mediante el diagrama de actividad de usuarios virtuales

Vea ver la actividad de usuario virtual que está asociada a la prueba de carga mediante el **Diagrama de actividad del usuario virtual**. Cada fila del diagrama representa un usuario virtual individual. El **Diagrama de actividad del usuario virtual** muestra exactamente qué estaba ejecutando cada usuario virtual durante la prueba. Puede ver patrones de actividad de los usuarios, modelos de carga, poner en correlación pruebas con errores o lentas y ver solicitudes con otra actividad de usuarios virtuales. El **Diagrama de actividad del usuario virtual** solamente está disponible cuando una prueba de carga termina de ejecutarse.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Los siguientes procedimientos muestran cómo ver el **Diagrama de actividad del usuario virtual**, cómo investigar una actividad del usuario concreta y cómo usar el filtrado.

## <a name="to-view-the-virtual-user-activity-chart-in-your-load-test-results"></a>Para ver el Diagrama de actividad del usuario virtual en los resultados de pruebas de carga

1. Para ver los datos de usuario virtual, primero debe configurar el valor **Todos los detalles individuales** de la propiedad **Almacenamiento de detalles de tiempo** que está asociada a la prueba de carga. Después, ejecute la prueba de carga.

2. Una vez que se ejecuta la prueba de carga, se muestra la página de resumen de los resultados de pruebas. Elija el botón **Detalles de usuario** de la barra de herramientas.

     O bien

     Abra la vista Gráficos al elegir el botón **Gráficos** de la barra de herramientas. Haga clic con el botón derecho en un gráfico y, luego, seleccione **Ir a detalles de usuario**.

     Si usa esta opción, el **Diagrama de actividad del usuario virtual** ampliará automáticamente la parte de la prueba en la que hizo clic con el botón derecho. Por ejemplo, si el puntero se encuentra aproximadamente en la marca de 30 segundos, la vista de detalle se muestra aproximadamente en la marca de 30 segundos de la herramienta **Ampliar período de tiempo**, en la parte inferior del **Diagrama de actividad del usuario virtual**.

     A continuación, puede investigar los detalles de una actividad del usuario concreta en el **Diagrama de actividad del usuario virtual**.

## <a name="to-investigate-a-specific-users-activity-in-the-virtual-user-activity-chart"></a>Investigar una actividad del usuario concreta en el Diagrama de actividad del usuario virtual

1. Use la herramienta Ampliar período de tiempo en la parte inferior del **Diagrama de actividad del usuario virtual** para seleccionar un área del gráfico donde desea investigar los detalles de un usuario concreto.

2. Mantenga el puntero sobre un detalle del gráfico. Observe que se muestra la siguiente información en la información sobre herramientas:

   - **Id. de usuario**

   - **Escenario**

   - **Prueba**

   - **Dirección URL** (no se muestra en una prueba o transacción)

   - **Resultado**

   - **Explorador** (no se muestra en una prueba o transacción)

   - **Network**

   - **Hora de inicio**

   - **Duración**

   - **Agent**

   - **Registro de prueba** (vínculo al registro de prueba)

     > [!NOTE]
     > Como ayuda para depurar su aplicación, si elige el vínculo **Registro de prueba**, se abrirá el resultado de la prueba web o el resultado de la prueba unitaria asociado al registro.

     Luego, puede utilizar las operaciones para filtrar y resaltar que están disponibles en el **Diagrama de actividad del usuario virtual**.

## <a name="to-use-filtering-options-in-the-virtual-user-activity-chart"></a>Para utilizar las opciones de filtrado del Diagrama de actividad del usuario virtual

1. En **Leyenda de detalles**, use la lista desplegable para seleccionar **Prueba**, **Página** o **Transacción**.

    **Panel Leyenda de detalles**

    ![Panel Leyenda de detalles](../test/media/ltest_detailslegend.png)

2. Active o desactive las casillas correspondientes a errores, registros, pruebas, búsqueda y páginas aspx asociados a la prueba de carga.

    El **Diagrama de actividad del usuario virtual** se actualiza en consecuencia.

    El **Diagrama de actividad del usuario virtual** permite filtrar pruebas, páginas y transacciones según diversos criterios. Puede quitar ciertas pruebas de la vista, quitar todas las pruebas superadas o bien quitar las pruebas no superadas en las que se produjeron determinados errores. También puede quitar todas las pruebas que no tienen registros.

    Por ejemplo, puede seleccionar la opción **(Resaltar errores)** , que muestra todos los errores en el gráfico coloreados en rojo. También puede seleccionar la opción **(Resaltar resultados con registros)** , que muestra todos los resultados de pruebas que tienen registros coloreados en verde en el gráfico.

    **Panel Resultados del filtro**

    ![Panel Resultados del filtro](../test/media/ltest_filterresults.png)

3. En los **resultados del filtro**, active o desactive las casillas correspondientes a las siguientes opciones de filtro:

   - **Mostrar solo resultados con registros** Muestra únicamente los resultados de pruebas que tienen registros de prueba asociados.

   - **Mostrar resultados correctos** Muestra los resultados correctos.

   - **Mostrar resultados con errores** Muestra los resultados con errores que pueden ayudar en la depuración.

     > [!NOTE]
     > La lista de tipos de errores que aparece bajo el nodo **Mostrar resultados con errores** se puede investigar en mayor profundidad si se elige el botón **Tablas** de la barra de herramientas **Visor de resultados de pruebas de rendimiento web**. Para más información, consulte [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

     El **Diagrama de actividad del usuario virtual** se actualiza en consecuencia.

## <a name="see-also"></a>Vea también

- [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Tutorial: Uso del diagrama de actividad del usuario virtual para aislar problemas](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)