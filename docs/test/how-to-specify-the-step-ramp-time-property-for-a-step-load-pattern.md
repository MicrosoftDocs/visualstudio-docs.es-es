---
title: Tiempo de rampa de paso de un modelo de carga de pasos para pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, load patterns
ms.assetid: 4a69e857-f93b-4907-9a01-fd1b66291205
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a45bcbdc149a6d3665efb0bc203d4a21138c979a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653350"
---
# <a name="how-to-specify-the-step-ramp-time-property-for-a-step-load-pattern"></a>Procedimiento Especificar la propiedad Tiempo de rampa de paso de un modelo de carga por pasos

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba. Para obtener más información, vea [Tutorial: Creación y ejecución de una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Para obtener una lista completa de las propiedades de los escenarios de pruebas de carga y sus descripciones, consulte [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md).

La propiedad **Tiempo de rampa de paso** se establece en la ventana **Propiedades**. Para modificar las propiedades del escenario de prueba de carga se usa el **Editor de pruebas de carga**.

La propiedad **Tiempo de rampa de paso** solo se usa con un modelo de carga de pasos. Para obtener más información, vea [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Los modelos de carga por pasos se usan para aumentar la carga en el servidor o los servidores mientras se ejecuta la prueba de carga, de forma que se vea cómo varía el rendimiento a medida que aumenta la carga de usuarios. Por ejemplo, para observar el rendimiento del servidor o los servidores cuando aumenta la carga de usuarios a 2000, ejecute una prueba de carga de 10 horas utilizando un modelo de carga por pasos con las siguientes propiedades:

- Recuento inicial de usuarios: 100

- Recuento máximo de usuarios: 2000

- Duración del paso (segundos): 1800

- Tiempo de rampa de paso (segundos): 20

- Recuento de usuarios por pasos: 100

Estas configuraciones hacen que la prueba de carga se ejecute durante 30 minutos (1800 segundos) con cargas de 100, 200, 300 y hasta 2000 usuarios.

> [!NOTE]
> La propiedad **Tiempo de rampa de paso** es la única de estas propiedades que no está disponible en el **Asistente para prueba de carga nueva**.

La propiedad **Tiempo de rampa de paso** permite que el aumento de un paso al siguiente (por ejemplo, de 100 a 200 usuarios) sea gradual en lugar de inmediato. En el ejemplo, la carga de usuarios aumentaría de 100 a 200 usuarios en un período de 20 segundos (un aumento de 5 usuarios cada segundo).

## <a name="to-edit-the-step-ramp-time-property-for-a-step-load-pattern"></a>Para editar la propiedad Tiempo de rampa de paso de un modelo de carga por pasos

1. Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Escenarios** del árbol de prueba de carga, abra el nodo del escenario para el que quiere especificar el tiempo de rampa de paso.

3. Seleccione el nodo **Modelo de carga de pasos**.

    > [!NOTE]
    > El modelo de carga para el escenario debe ser un modelo de carga de pasos. Si no es así, el modelo de carga mostrará el tipo de modelo de carga que está asociado al escenario. Para obtener más información, vea [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md).

4. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

5. Establezca el valor de la propiedad **Tiempo de rampa de paso** al escribir un número para los segundos que lleva en cada paso agregar gradualmente a los usuarios especificados en la propiedad **Recuento de usuarios por pasos**.

6. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Tiempo de rampa de paso**.

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)
- [Modificar modelos de carga para modelar las actividades de usuarios virtuales](../test/edit-load-patterns-to-model-virtual-user-activities.md)