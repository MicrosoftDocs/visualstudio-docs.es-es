---
title: Guardar registros de pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 9ac88d8a-4777-462c-aa0e-244dadb2cfd1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 3464ffc1db1a757ac20e3f77d0d901ec731a7cab
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381939"
---
# <a name="how-to-specify-how-frequently-test-logs-are-saved-using-the-load-test-editor"></a>Cómo: Especificar la frecuencia con que se guardan los registros de pruebas mediante el Editor de pruebas de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de las pruebas de carga de modo que satisfagan las necesidades y los objetivos de la prueba. Para obtener más información, vea [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md).

> [!NOTE]
> Para obtener una lista completa de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

Puede especificar la frecuencia con la que se guarda el registro de prueba en una prueba de carga con el **Editor de pruebas de carga** si cambia la propiedad **Frecuencia de guardado del registro para pruebas completadas** en la ventana **Propiedades**.

## <a name="to-specify-the-frequency-for-saving-the-test-log-in-a-load-test"></a>Para especificar la frecuencia para guardar el registro de pruebas en una prueba de carga

1.  Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Muestra el árbol de la prueba de carga.

2.  En la carpeta **Parámetros de ejecución** del árbol de la prueba de carga, elija el nodo del parámetro de ejecución para el que quiere especificar la frecuencia con que se guarda el registro de prueba.

3.  En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades del escenario se muestran en la ventana **Propiedades**.

4.  En el cuadro de texto de la propiedad **Frecuencia de guardado del registro para pruebas completadas**, escriba un número para indicar la frecuencia con la que se escribirá el registro de prueba. El número indica que en el registro de prueba se guardará una prueba de cada número de pruebas especificado. Por ejemplo, si se especifica el valor diez, significa que se escribirá en el registro de prueba la décima, la vigésima, la trigésima, y así sucesivamente.

    > [!NOTE]
    > Si se usa el valor 0 para la propiedad **Frecuencia de guardado del registro para pruebas completadas**, no se guarda ningún registro de prueba.

5.  Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**.

     Los datos guardados en el registro se pueden ver mediante la vista Tablas del Analizador de prueba de carga. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Cómo: Especificar si los errores de las pruebas se guardan en los registros de pruebas](../test/how-to-specify-if-test-failures-are-saved-to-test-logs.md)
- [Cómo: Configurar los resultados de pruebas para recopilar información completa para habilitar la actividad de usuario virtual en los resultados de pruebas](../test/how-to-configure-load-tests-to-collect-full-details.md)