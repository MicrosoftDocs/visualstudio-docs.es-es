---
title: Aplicación de la distribución al retraso del ritmo de las pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 25b22ff696fb12e4924587313cde8fe387900fe9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model"></a>Cómo: Aplicar la distribución al retraso del ritmo cuando se usa un modelo de combinación de pruebas basado en el ritmo del usuario

Después de crear la prueba de carga con el Asistente para prueba de carga nueva, puede usar el Editor de pruebas de carga para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba.

La propiedad **Aplicar distribución a intervalo de velocidad** se establece en la ventana Propiedades. Las propiedades del escenario de prueba de carga se modifican con el Editor de prueba de carga.

> [!NOTE]
> La propiedad **Aplicar distribución a intervalo de velocidad** solo se aplica si la *combinación de pruebas de carga* se configura a partir de la velocidad del usuario. Para obtener más información, vea [Modificar los modelos de combinación de texto para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

El valor de **Aplicar distribución a intervalo de velocidad** se puede establecer en true o en false:

-   **True**: el escenario aplicará retrasos de distribución estadística normales especificados por el valor de la columna **Pruebas por usuario y por hora** del cuadro de diálogo Editar combinación de pruebas. Para obtener más información, vea [Modificar los modelos de combinación de texto para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Por ejemplo, suponga que ha establecido el valor de **Pruebas por usuario y por hora** en el cuadro de diálogo Editar combinación de pruebas para el conjunto de pruebas en dos usuarios por hora. Si la propiedad **Aplicar distribución a intervalo de velocidad** está establecida en **True**, se aplicará una distribución estadística normal al tiempo de espera entre las pruebas. Se seguirán ejecutando dos pruebas por hora, pero no habrá necesariamente un retraso de 30 minutos entre ellas. La primera prueba podría ejecutarse después de cuatro minutos y la segunda después de 45 minutos.

-   **False**: las pruebas se ejecutarán a la velocidad especificada para el valor de la columna **Pruebas por usuario y por hora** en el cuadro de diálogo Editar combinación de pruebas. Para obtener más información, vea [Modificar los modelos de combinación de texto para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Por ejemplo, suponga que ha establecido el valor de **Pruebas por usuario y por hora** en el cuadro de diálogo Editar combinación de pruebas para el conjunto de pruebas en dos usuarios por hora. Si la propiedad **Aplicar distribución a intervalo de velocidad** está establecida en **False**, no está proporcionando ninguna libertad cuando se ejecuten las pruebas. La prueba se ejecutará cada 30 minutos. Esto asegura que ejecutará dos pruebas por hora.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Para especificar la configuración de la propiedad Aplicar distribución a intervalo de velocidad para un escenario

1.  Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2.  En la carpeta **Escenarios** del árbol de pruebas de carga, elija el nodo del escenario para el que quiera especificar los agentes que se van a usar.

3.  En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

4.  En el valor de propiedad **Aplicar distribución a intervalo de velocidad**, seleccione **True** o **False**.

5.  Después de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga usando el nuevo valor de **Aplicar distribución a intervalo de velocidad**.

## <a name="see-also"></a>Vea también

- [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)