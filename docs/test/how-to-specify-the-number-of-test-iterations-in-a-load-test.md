---
title: Especificación del número de iteraciones de prueba en los parámetros de ejecución de una prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa5de5f7f9c1bfef78ad3698886e8d7af43a4812
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653389"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Procedimiento para especificar el número de iteraciones de prueba en los parámetros de ejecución de una prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba. Para obtener más información, vea [Tutorial: Creación y ejecución de una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md).

Con el **Editor de pruebas de carga**, puede modificar la propiedad **Iteraciones de prueba** de un valor de parámetro de ejecución en la ventana **Propiedades**. La propiedad **Iteraciones de prueba** especifica el número de iteraciones que se ejecutan en todas las pruebas unitarias y de rendimiento web en todos los escenarios de una prueba de carga con el **Editor de pruebas de carga**.

> [!NOTE]
> Para obtener una lista completa de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Para especificar el número de iteraciones de prueba en un parámetro de ejecución

1. Abra una prueba de carga.

     El **Editor de pruebas de carga** se abre y muestra el árbol de la prueba de carga.

2. En el árbol de la prueba de carga, en la carpeta **Parámetros de ejecución**, elija un parámetro de ejecución.

3. En el menú **Ver**, seleccione la ventana **Propiedades** para ver las propiedades y categorías del parámetro de ejecución de carga.

4. Establezca la propiedad **Usar iteraciones de prueba** en **True**.

5. En la propiedad **Iteraciones de prueba**, escriba un número que indique la cifra de iteraciones de prueba que se van a ejecutar durante la prueba de carga.

6. Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Iteraciones de prueba**.

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)