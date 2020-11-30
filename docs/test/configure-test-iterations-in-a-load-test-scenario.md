---
title: Configuración de iteraciones de prueba para pruebas de carga
description: Aprenda a configurar los valores de iteración de prueba, a fin de configurar el número máximo de iteraciones del escenario y cuánto tiempo de pausa debe haber entre ellas.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, scenarios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5316b03220a094d3280aba3eb8c46f190a2874f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442565"
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Configurar iteraciones de prueba en un escenario de prueba de carga

Para configurar los parámetros de iteración de prueba, edite un escenario de prueba de carga mediante el Editor de pruebas de carga y la ventana **Propiedades**. De forma predeterminada, un escenario de prueba de carga se configura sin especificar iteraciones de pruebas máximas. Tiene la posibilidad de configurar el número máximo de iteraciones del escenario y el tiempo de pausa entre ellas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Especificar el número máximo de iteraciones de prueba para un escenario

Puede especificar el número máximo de veces que quiere que se ejecuten las pruebas para un escenario usando el Editor de pruebas de carga para cambiar la propiedad **Iteraciones de pruebas máximas** en la ventana **Propiedades**.

La propiedad **Iteraciones de pruebas máximas** controla el número máximo de iteraciones de pruebas que se deben ejecutar para el escenario. Al igual que sucede con la propiedad **Iteraciones de prueba** en los parámetros de ejecución de pruebas de carga, se trata del número máximo para todos los usuarios en todos los agentes, es decir, no es un valor por usuario.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

Para la combinación de pruebas secuencial, una iteración es un paso a través de todas las pruebas de la combinación. Para todas las demás combinaciones de pruebas, cada ejecución de pruebas se considera una iteración. Para más información, consulte [Control de combinaciones](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

Si la prueba de carga es una prueba de carga basada en la duración y la duración expira antes de que el número de iteraciones se haya completado, la prueba se seguirá deteniendo. Si la prueba está basada en la iteración, y las iteraciones de pruebas finalizan antes de las iteraciones del escenario, la prueba se detendrá. La duración se configura mediante la propiedad **Duración de la ejecución** de la ventana **Propiedades** asociada a un parámetro de ejecución en una prueba de carga.

Cuando se consiga el número de iteraciones del escenario, el escenario dejará de ejecutarse, pero cualquier otro escenario activo lo seguirá haciendo.

> [!NOTE]
> Una propiedad relacionada es la propiedad **Único** de un origen de datos de prueba web, que se mueve secuencialmente a través de los datos, fila a fila, pero una sola vez para cada registro. Para obtener más información, consulte [Agregar un origen de datos a una prueba de rendimiento web](../test/add-a-data-source-to-a-web-performance-test.md).

La propiedad **Iteraciones de pruebas máximas** es útil en varias situaciones. Algunos evaluadores de carga prefieren realizar las pruebas basadas en iteración, mientras que otros las prefieren basadas en la duración.

![Especificar iteraciones de prueba en un escenario](../test/media/loadtest_prop.png)

### <a name="to-specify-the-maximum-test-iterations"></a>Para especificar el número máximo de iteraciones de prueba

1. Abra una prueba de carga.

2. Aparecerá el Editor de prueba de carga. Se mostrará el árbol de la prueba de carga.

3. En la carpeta **Escenarios** del árbol de la prueba de carga, elija el nodo de escenario para el que desea especificar el número máximo de iteraciones de prueba.

4. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

5. En el cuadro de texto de la propiedad **Iteraciones de pruebas máximas**, escriba un valor que indique el número máximo de pruebas que se ejecutarán para el escenario cuando se ejecute la prueba de carga.

    > [!NOTE]
    > Si se usa el valor 0 para la propiedad **Iteraciones de pruebas máximas**, no se especifica un número máximo de iteraciones.

6. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. A continuación, puede ejecutar su prueba de carga con el nuevo valor de **Iteraciones de pruebas máximas**.

## <a name="specify-think-times-between-test-iterations-for-a-scenario"></a>Especificar los tiempos de reflexión de usuario entre iteraciones de prueba en un escenario

La propiedad **Tiempo de reflexión entre iteraciones de la prueba** se establece desde la ventana **Propiedades** mientras se editan las propiedades del escenario de prueba de carga en el Editor de pruebas de carga.

La propiedad **Tiempo de reflexión entre iteraciones de la prueba** se emplea para especificar el número de segundos que hay que esperar antes de iniciar una iteración de la prueba.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, vea [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-time-between-test-iterations"></a>Para especificar el tiempo de reflexión de usuario entre iteraciones de prueba

1. Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Escenarios** de árboles de la prueba de carga, elija el nodo de escenario cuyo tiempo de reflexión de usuario quiere especificar.

3. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

4. En el valor de la propiedad **Tiempo de reflexión entre iteraciones de la prueba**, escriba un número que represente el número de segundos que se va a esperar antes de iniciar la siguiente iteración de la prueba.

5. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. A continuación, puede ejecutar la prueba de carga con el nuevo valor de **Tiempo de reflexión entre iteraciones de la prueba**.

## <a name="see-also"></a>Consulte también

- [Editar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Configuración de agentes y controladores de pruebas para pruebas de carga](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)
- [Modificar los tiempos de reflexión de usuario para simular los retrasos de la interacción humana en un sitio web](../test/edit-think-times-in-load-test-scenarios.md)
