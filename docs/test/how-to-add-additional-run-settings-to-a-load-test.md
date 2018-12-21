---
title: Adición de parámetros de ejecución a una prueba de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, adding
- load tests, run settings
ms.assetid: 257d2a24-d582-4cfe-8b2b-51f51ba9cc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 439120b80350081e1770ccce619d51b92673feef
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048059"
---
# <a name="how-to-add-additional-run-settings-to-a-load-test"></a>Procedimiento para agregar más parámetros de ejecución a una prueba de carga

Los parámetros de ejecución de una prueba de carga determinan una variedad de otros valores. Estos incluyen la duración de la prueba, el nivel de detalle de la colección de resultados y los conjuntos de contadores que se recopilan cuando se ejecuta la prueba. Puede crear y almacenar varios parámetros de ejecución para cada prueba de carga, y seleccionar una configuración determinada para utilizarla durante la ejecución de la prueba. Cuando crea la prueba de carga mediante el **Asistente para prueba de carga nueva**, se agrega un parámetro de ejecución inicial a la prueba de carga.

Puede agregar más parámetros de ejecución a la prueba de carga con distintas configuraciones de propiedades para poder realizar la prueba de carga en condiciones diferentes. Por ejemplo, puede agregar una nueva configuración de pruebas y utilizar una velocidad de muestra diferente o especificar una duración más larga. Solo puede utilizar un parámetro de ejecución cada vez y especificar qué parámetro de ejecución desea utilizar marcándolo como activo.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-another-run-setting"></a>Para agregar otro parámetro de ejecución

1.  Abra una prueba de carga.

2.  (Opcional) Expanda la carpeta **Parámetros de ejecución**.

3.  Haga clic con el botón derecho en la carpeta **Parámetros de ejecución** y seleccione **Agregar parámetros de ejecución**.

     Se agregará un nuevo parámetro de ejecución a la carpeta **Parámetros de ejecución**.

4.  En el menú **Ver**, elija la ventana **Propiedades**.

     Se mostrará la ventana **Propiedades** con las propiedades de los parámetros de ejecución seleccionados.

5.  En la ventana **Propiedades**, use el cuadro de texto de la propiedad **Name** para asignar al nuevo parámetro de ejecución un nombre que describa su propósito (por ejemplo, **Parámetro de ejecución: ejecución de cinco minutos**).

6.  Use la ventana **Propiedades** para cambiar los parámetros de ejecución. Por ejemplo, cambie la duración de ejecución a **00:05:00** para ejecutar la prueba durante cinco minutos.

    > [!NOTE]
    > Para obtener una lista completa de las propiedades de los parámetros de ejecución y sus descripciones, consulte [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

     Ahora puede especificar que desea utilizar el parámetro de ejecución agregado estableciéndolo en el activo. Para obtener más información, vea [Cómo: Seleccionar el parámetro de ejecución activo de una prueba de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md).

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)