---
title: Configurar retrasos de inicio de escenario para pruebas de carga en Visual Studio
description: Aprenda a especificar un retraso antes de que se inicie un escenario en una prueba de carga mediante el Editor de pruebas de carga y la ventana Propiedades.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec94fc67dbf42cd2631af1a655d6b8deab54fabc
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441513"
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Configurar retrasos de inicio de escenario en pruebas de carga

Con el Editor de pruebas de carga y la ventana **Propiedades**, especifique un retraso antes de que se inicie un escenario en una prueba de carga.

Por ejemplo, tal vez desee usar la propiedad **Retrasar hora de inicio** si necesita que un escenario empiece a generar elementos que usa otro escenario. Puede retrasar el escenario consumidor para permitir que el escenario productor rellene algunos datos.

Otro ejemplo es que puede tener un escenario que solo se ejecute en determinado momento del día. De forma que desea retrasar el inicio del escenario para simular esto.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="specify-the-delay-start-time-of-a-scenario"></a>Especificar el retraso de la hora de inicio de un escenario

Puede especificar un retraso antes de iniciar un escenario en una prueba de carga utilizando el Editor de pruebas de carga para cambiar la propiedad **Retrasar hora de inicio** en la ventana **Propiedades**.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

Un ejemplo de una instancia en la que puede que desee utilizar la propiedad **Retrasar hora de inicio** es si necesita que un escenario empiece a generar elementos que utiliza otro escenario. Puede retrasar el escenario consumidor para permitir que el escenario productor rellene algunos datos.

Otro ejemplo es que puede tener un escenario que solo se ejecute en determinado momento del día. Por tanto, desea retrasar el inicio del escenario para simular esto.

> [!NOTE]
> Para obtener una lista completa de las propiedades de los parámetros de ejecución y sus descripciones, vea [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Para especificar la hora de inicio del retraso de un escenario

1. Abra una prueba de carga.

     Aparecerá el Editor de prueba de carga. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Escenarios** del árbol de la prueba de carga, elija el nodo de escenario para el que desea especificar el retraso de la hora de inicio.

3. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

4. En el cuadro de texto de la propiedad **Retrasar hora de inicio**, escriba un valor de tiempo que indique el tiempo que desea esperar una vez que se inicie la prueba de carga antes de iniciar el escenario cuando se ejecuta la prueba de carga.

    > [!NOTE]
    > Si el valor de la propiedad **Deshabilitar durante el calentamiento** del escenario se establece en **True**, el valor de tiempo de la propiedad **Retrasar hora de inicio** se aplicará después del período de calentamiento. Puede controlar qué escenarios se incluyen en el calentamiento utilizando la propiedad de escenario **Deshabilitar durante el calentamiento**.

5. Después de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. A continuación, puede ejecutar la prueba de carga usando el nuevo valor de **Retrasar hora de inicio**.

## <a name="enable-and-disable-whether-a-scenario-runs-during-the-warm-up-period"></a>Habilitar y deshabilitar si un escenario se ejecuta durante el período de preparación

La propiedad **Deshabilitar durante el calentamiento** se establece mediante la ventana **Propiedades**. La edición de propiedades de escenario de la prueba de carga se establece mediante el Editor de prueba de carga.

La propiedad **Deshabilitar durante el calentamiento** se utiliza para indicar si el escenario se debería ejecutar o no durante el período de preparación que se especifica en la propiedad **Retrasar hora de inicio**. Para obtener más información, revise el procedimiento anterior [Especificar el retraso de la hora de inicio de un escenario](#specify-the-delay-start-time-of-a-scenario).

> [!NOTE]
> Para obtener una lista completa de las propiedades de los parámetros de ejecución y sus descripciones, vea [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Para habilitar o deshabilitar el período de preparación de un escenario

1. Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Escenarios** de árboles de la prueba de carga, elija el nodo de escenario cuyo comportamiento de preparación quiere cambiar.

3. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

     En la propiedad **Deshabilitar durante el calentamiento**, seleccione **True** o **False**.

4. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. A continuación, puede ejecutar la prueba de carga con el nuevo valor de **Deshabilitar durante el calentamiento**.

## <a name="see-also"></a>Consulte también

- [Editar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Configuración de agentes y controladores de pruebas para pruebas de carga](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)
