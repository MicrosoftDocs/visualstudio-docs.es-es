---
title: Adición de conjuntos de contadores personalizados para pruebas de carga en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- counter sets
- load tests, counter sets
ms.assetid: 499aca80-1069-408d-ac68-326da6a50645
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: bd58cc29368ed66d3dd8c35fa4bdf3c87aa6a747
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-custom-counter-sets-using-the-load-test-editor"></a>Cómo: Agregar conjuntos de contadores personalizados usando el Editor de prueba de carga

Cuando se crea una prueba de carga con el **Asistente para prueba de carga nueva**, se agrega un conjunto de contadores inicial. Este conjunto inicial de contadores ofrece una serie de conjuntos de contadores predefinidos para la prueba de carga.

> [!NOTE]
> Si las pruebas de carga se distribuyen entre varios equipos remotos, los contadores de controlador y de agente se asignan automáticamente a los conjuntos de contadores de controlador y de agente. Para obtener más información sobre cómo usar equipos remotos en la prueba de carga, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

Los contadores se administran en el **Editor de pruebas de carga**. Los conjuntos de contadores que ya se han agregado a la prueba están visibles en el nodo **Conjuntos de contadores** de la prueba de carga. Después de crear una prueba de carga, puede agregar nuevos conjuntos de contadores personalizados a la misma.

![Conjunto de contadores personalizado](../test/media/loadtestcustomcounter.png "LoadTestCustomCounter")

## <a name="to-add-a-custom-counter-set-to-a-load-test"></a>Para agregar un conjunto de contadores personalizados a una prueba de carga

1.  Abra una prueba de carga.

2.  Expanda el nodo **Conjuntos de contadores**. Todos los conjuntos de contadores que se hayan agregado a la prueba de carga estarán visibles.

3.  Haga clic con el botón derecho en el nodo **Conjuntos de contadores** y seleccione **Agregar conjunto de contadores personalizados**.

    > [!NOTE]
    > El conjunto de contadores recibe un nombre predeterminado, como **Custom1**. Este nombre puede cambiarse en la ventana **Propiedades**. Pulse F4 para abrir la ventana **Propiedades**.

4.  Para agregar contadores a su conjunto de contadores personalizados, haga clic con el botón derecho en el nuevo conjunto de contadores y, a continuación, elija **Agregar contadores**. Para obtener más información sobre cómo agregar contadores, vea [Cómo: Agregar contadores a conjuntos de contadores](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md).

    > [!NOTE]
    > Otra forma de agregar un conjunto de contadores personalizados es hacer clic con el botón secundario en un conjunto de contadores existente, elegir copiar y, a continuación, pegarlo en el nodo de conjuntos de contadores. Si se copian contadores adicionales que no son necesarios, pueden eliminarse. Puede cambiar el nombre del nuevo conjunto de contadores en la ventana **Propiedades**.

## <a name="see-also"></a>Vea también

- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)