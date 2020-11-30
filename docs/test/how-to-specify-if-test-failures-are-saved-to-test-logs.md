---
title: Almacenamiento del registro de errores de prueba de carga
description: Aprenda cómo especificar que quiere guardar el registro de pruebas si se produce un error en una prueba de carga cambiando la propiedad Guardar registro si la prueba no es correcta.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6dbde0f1a1f854bfd7dc6c2f74e3081a33b4796
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439910"
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Cómo: Especificar si los errores de las pruebas se guardan en los registros de pruebas mediante el Editor de pruebas de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de las pruebas de carga de modo que satisfagan las necesidades y los objetivos de la prueba. Consulte [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md). Para especificar si desea guardar el registro de pruebas si se produce un error en una prueba de carga, puede cambiar la propiedad **Guardar registro si la prueba no es correcta**.

> [!NOTE]
> Para obtener una lista completa de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Para especificar si se guarda el registro de pruebas cuando se produce un error de una prueba de un escenario

1. Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2. En la carpeta **Parámetros de ejecución** del árbol de la prueba de carga, elija el nodo de parámetros de ejecución para el que desea especificar el número máximo de iteraciones de prueba.

3. En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades de los parámetros de ejecución se muestran en la ventana **Propiedades**.

4. En la propiedad **Guardar registro si la prueba no es correcta**, seleccione **True** o **False** para especificar si quiere guardar el registro de pruebas en caso de error de una prueba en el escenario.

     Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**.

     Los datos guardados en el registro se pueden ver mediante la vista Tablas del Analizador de prueba de carga. Para obtener más información, vea [Analizar los errores y resultados de pruebas de carga en la vista Tablas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="see-also"></a>Vea también

- [Modificar escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
- [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md)
