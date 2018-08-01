---
title: Emulación del uso real de un sitio web para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load model, specifying
- load test load model, specifying
ms.assetid: b7fae849-0538-40d1-ab35-2bb3a0fe4393
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 682370de0964e8bc96a069f015f37144f4d9a83f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177271"
---
# <a name="emulate-expected-real-world-usage-of-a-website-or-application-in-a-load-test-using-a-test-mix-model"></a>Emulación del uso real esperado de una aplicación o un sitio web en una prueba de carga mediante un modelo de combinación de pruebas

Puede usar opciones de modelos de carga para predecir de forma más precisa el uso real esperado del sitio web o la aplicación cuyas pruebas de carga está realizando. Esto es importante porque una prueba de carga que no se basa en un modelo de carga preciso puede generar resultados engañosos.

## <a name="test-mix-model-enhancements"></a>Mejoras en el modelo de combinación de pruebas

Mediante el Editor de prueba de carga o el asistente para modelo de combinación de pruebas, puede especificar los tipos siguientes de combinación de pruebas para un escenario de prueba de carga. Para más información, consulte [Cambiar el modelo de combinación de pruebas en un escenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

Puede especificar una de las siguientes opciones de modelo de combinación de pruebas para el escenario de la prueba de carga:

-   **Basado en el número total de pruebas:** determina qué prueba unitaria o de rendimiento web se ejecuta cuando un usuario virtual inicia una iteración de prueba. Al final de la prueba de carga, el número de veces que se ha ejecutado una prueba determinada coincide con la distribución de pruebas asignada. Use este modelo de combinación de pruebas cuando base la combinación de pruebas en porcentajes de transacciones en un registro de IIS o en datos de producción. Para más información, consulte [Porcentaje basado en las pruebas iniciadas](#BasedOnTestsStarted).

-   **Basado en el número de usuarios virtuales:** determina el porcentaje de usuarios virtuales que ejecutan una prueba unitaria o de rendimiento web determinada. En cualquier punto de la prueba de carga, el número de usuarios que ejecutan una prueba determinada coincide con la distribución asignada. Use este modelo de combinación de pruebas cuando base la combinación de pruebas en el porcentaje de usuarios que ejecutan una prueba determinada. Para obtener más información, vea [Porcentaje basado en usuarios virtuales](#PercentageBasedonVirtualUsers).

-   **Basado en la velocidad del usuario:** durante la prueba de carga, cada prueba unitaria o de rendimiento web se ejecuta un número especificado de veces por usuario y por hora. Use este modelo de combinación de pruebas cuando desee que los usuarios virtuales ejecuten pruebas a una determinada velocidad durante la prueba de carga. Para obtener más información, vea [Combinación de pruebas a un ritmo regulado](#PacingTestMix).

    > [!TIP]
    > ¿Cuándo debe elegir **Porcentaje de combinación de pruebas** y **Porcentaje basado en usuarios virtuales**? La diferencia entre estas dos opciones es importante cuando algunas pruebas de la combinación de pruebas tienen una duración mucho mayor que otras. En esta situación, probablemente debería elegir **Porcentaje basado en usuarios virtuales**. Esta opción ayuda a evitar una ejecución de pruebas en la que haya muchas probabilidades de que demasiados usuarios ejecuten pruebas de larga duración. Pero si todas las pruebas tienen una duración similar, es más seguro elegir **Porcentaje de combinación de pruebas**.

-   **Basado en el orden secuencial:** cada usuario virtual ejecuta las pruebas unitarias o de rendimiento web en el mismo orden en que se definen en el escenario. El usuario virtual seguirá recorriendo las pruebas en este orden hasta que se complete la prueba de carga. Para más información, consulte [Orden secuencial](#SequentialOrder).

###  <a name="BasedOnTestsStarted"></a> Porcentaje basado en las pruebas iniciadas
 Para cada prueba de la combinación, puede especificar un porcentaje que determine la frecuencia con la que la prueba se selecciona como la siguiente prueba que se va a ejecutar. Por ejemplo, podría asignar los valores de porcentaje siguientes a tres pruebas:

-   PruebaA (50%)

-   PruebaB (35%)

-   PruebaC (15%)

 Si utiliza estos valores, la siguiente prueba que se inicia se basa en los porcentajes asignados. Para ello no se tiene en cuenta el número de usuarios virtuales que ejecutan actualmente cada prueba.

###  <a name="PercentageBasedonVirtualUsers"></a> Porcentaje basado en los usuarios virtuales
 Este modelo de combinación de pruebas determina el porcentaje de usuarios virtuales que ejecutarán una prueba determinada. Si utiliza este modelo de combinación de pruebas, la siguiente prueba que se inicia no se basa sólo en los porcentajes asignados, sino también en el porcentaje de usuarios virtuales que ejecutan actualmente una determinada prueba. En cualquier punto de la prueba de carga, el número de usuarios que ejecutan una determinada prueba coincide de la forma más precisa posible con la distribución asignada.

###  <a name="PacingTestMix"></a> Combinación de pruebas a un ritmo regulado
 Si especifica una combinación de pruebas a un ritmo regulado, definirá una frecuencia de ejecución de pruebas para cada usuario virtual y prueba de la combinación de pruebas. Para cada prueba, esta frecuencia se expresa como ejecución de las pruebas por usuario virtual y hora. Por ejemplo, podría asignar la siguiente combinación de pruebas a ritmo regulado para las pruebas siguientes:

-   PruebaA: 4 pruebas por usuario y hora

-   PruebaB: 2 pruebas por usuario y hora

-   PruebaC: 0,125 pruebas por usuario y hora

 Si utiliza el modelo de combinación de pruebas a ritmo regulado, el motor de tiempo de ejecución de pruebas de carga garantiza que la frecuencia real a la que se inician las pruebas sea menor o igual que la frecuencia especificada. Si las pruebas se ejecutan demasiado tiempo para que pueda completarse el número asignado, se devuelve un error.

 La opción **Tiempo de reflexión entre iteraciones de la prueba** no se aplica cuando se usa la combinación de pruebas a un ritmo regulado.

#### <a name="apply-distribution-to-pacing-delay"></a>Aplicar distribución a intervalo de velocidad
 El valor de la propiedad **Aplicar distribución a intervalo de velocidad** en un escenario de prueba de carga se puede establecer en true o en false:

-   **True**: el escenario aplica retrasos de distribución estadística típicos especificados por el valor de la columna **Pruebas por usuario y por hora** del cuadro de diálogo **Editar combinación de pruebas**. Para más información, consulte [Editar modelos de combinación de pruebas para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Por ejemplo, suponga que ha establecido el valor de **Pruebas por usuario y por hora** del cuadro de diálogo **Editar combinación de pruebas** del conjunto de pruebas en 2 usuarios por hora. Si la propiedad **Aplicar distribución a intervalo de velocidad** está establecida en **True**, se aplica una distribución estadística típica al tiempo de espera entre las pruebas. Se seguirán ejecutando 2 pruebas por hora, pero no habrá necesariamente 30 minutos entre ellas. La primera prueba podría ejecutarse después de 4 minutos y la segunda después de 45 minutos.

-   **False**: las pruebas se ejecutan a la velocidad especificada por el valor de la columna **Pruebas por usuario y por hora** en el cuadro de diálogo **Editar combinación de pruebas**. Para más información, consulte [Editar modelos de combinación de pruebas para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

     Por ejemplo, suponga que ha establecido el valor de **Pruebas por usuario y por hora** del cuadro de diálogo **Editar combinación de pruebas** del conjunto de pruebas en 2 usuarios por hora. Si la propiedad **Aplicar distribución a intervalo de velocidad** se establece en **False**, no está proporcionando ninguna libertad cuando se ejecuten las pruebas. La prueba se ejecutará cada 30 minutos. Esto asegura que ejecutará 2 pruebas por hora.

 Para más información, consulte [Cómo: Aplicar distribución a intervalo de velocidad en un modelo de combinación de pruebas basado en el ritmo del usuario](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md).

###  <a name="SequentialOrder"></a> Orden secuencial
 Al seleccionar la opción Por orden de pruebas secuencial permite a los usuarios virtuales ejecutar todas las pruebas del escenario en el orden con que se definieron las pruebas.

## <a name="test-iterations-property"></a>Propiedad de iteraciones de prueba
 En las propiedades de parámetros de ejecución, puede especificar un valor para la propiedad Iteraciones de prueba. Este valor es el número de iteraciones de pruebas que se ejecutan en una prueba de carga. Una vez iniciado el número especificado de iteraciones de pruebas, no se iniciará ninguna otra iteración de pruebas cualquiera que sea la configuración de los perfiles de carga. Cuando el número de iteraciones de pruebas especificado se completa, la prueba de carga finaliza. Para más información, consulte [Cómo: Especificar el número de iteraciones de prueba de un parámetro de ejecución](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md).

## <a name="initialize-and-terminate-tests"></a>Pruebas de inicialización y terminación
 Puede seleccionar pruebas que se ejecuten al principio y al final de la sesión de pruebas de carga de cada usuario virtual. Para más información, consulte [Editar modelos de combinación de pruebas para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).

-   **Prueba de inicialización**. Cada usuario virtual ejecuta esta prueba antes que cualquier otra prueba de la combinación.

-   **Prueba de terminación**. Esta prueba se ejecuta una vez ejecutadas todas las pruebas de un determinado usuario virtual.

 Tenga en cuenta las siguientes consideraciones sobre las pruebas de inicialización y terminación:

-   Puede especificar la duración de la prueba de carga por tiempo en lugar de por número de iteraciones. En ese caso, cuando concluye la duración de la ejecución de la prueba de carga, no se ejecuta la prueba de terminación.

-   Si la prueba de inicialización es una prueba unitaria o una prueba de rendimiento web, se guarda el estado del objeto TestContext o WebTestContext una vez finalizada la prueba de inicialización. Este estado se utilizará entonces como el contexto de inicio para las iteraciones de las pruebas de la combinación de pruebas.

-   Los nuevos Usuarios, definidos en la propiedad del escenario Porcentaje de nuevos usuarios, siempre ejecutan la prueba de inicialización, una iteración de una prueba de la combinación de pruebas y la prueba de terminación.

## <a name="see-also"></a>Vea también

- [Editar modelos de combinación de pruebas para especificar la probabilidad de que un usuario virtual ejecute una prueba](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)
- [Editar los modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md)
- [Editar la combinación de pruebas para especificar qué pruebas incluir en un escenario de prueba de carga](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)
- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)
- [Cambiar el modelo de combinación de pruebas en un escenario](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)