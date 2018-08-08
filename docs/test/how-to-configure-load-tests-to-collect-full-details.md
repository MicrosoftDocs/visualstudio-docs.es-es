---
title: Recopilación de información completa de usuarios virtuales para pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 70930a09f01450d59b44678ebd26d7e742af7294
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379630"
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Cómo: Configurar las pruebas de carga para recopilar información completa para habilitar la actividad de usuario virtual en los resultados de pruebas

Para usar el **Diagrama de actividad del usuario virtual** de la prueba de carga, debe configurar la prueba de carga para recopilar todos los detalles. Para configurar la prueba de carga de este modo, seleccione el valor **Todos los detalles individuales** para la propiedad **Almacenamiento de detalles de tiempo** que está asociada a la prueba de carga. En este modo, la prueba de carga recopilará información detallada sobre cada prueba, página y transacción.

 Si va a actualizar un proyecto de una versión anterior de prueba de carga de Visual Studio, realice los pasos del siguiente procedimiento para habilitar la recopilación de detalles completos.

 El valor **Todos los detalles individuales** de la propiedad **Almacenamiento de detalles de tiempo** se puede establecer en cualquiera de las siguientes opciones:

-   **Todos los detalles individuales:** recopila y almacena datos de tiempo individuales de cada prueba, transacción y página emitidos durante la prueba.

    > [!NOTE]
    > La opción **Todos los detalles individuales** debe estar seleccionada para permitir que aparezcan los datos de usuarios virtuales en los resultados de pruebas de carga.

-   **Ninguno:** no recopila detalles de tiempo individuales. Sin embargo, los valores promedio todavía están disponibles.

-   **Solo estadísticas:** almacena datos de tiempo individuales, pero solo como datos de percentil. De este modo, se ahorra espacio.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>Para configurar la propiedad Almacenamiento de detalles de tiempo en una prueba de carga

1.  Abra una prueba de carga en el **Editor de pruebas de carga**.

2.  Expanda el nodo **Parámetros de ejecución** de la prueba de carga.

3.  Elija el parámetro de ejecución que quiera configurar, por ejemplo, **Run Settings1[Active]**.

4.  Abra la ventana **Propiedades**. En el menú **Ver**, seleccione la ventana **Propiedades**.

5.  En la categoría **Resultados**, elija la propiedad **Almacenamiento de detalles de tiempo** y seleccione **Todos los detalles individuales**.

     Después de haber configurado el valor **Todos los detalles individuales** de la propiedad **Almacenamiento de detalles de tiempo**, puede ejecutar la prueba de carga y ver el **Diagrama de actividad del usuario virtual**. Para obtener más información, vea [Cómo: Analizar lo que hacen los usuarios virtuales durante una prueba de carga mediante el Diagrama de actividad de los usuarios virtuales](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Vea también

- [Analizar la actividad de usuario virtual de prueba de carga en la vista Detalles del Analizador de prueba de carga](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Tutorial: Usar el Diagrama de actividad del usuario virtual para aislar problemas de rendimiento](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)