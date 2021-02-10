---
title: Adición de una regla de umbral para pruebas de carga
description: Conozca las reglas de umbral de las pruebas de carga, que comparan un valor de contador de rendimiento con un valor constante o con otro valor de contador de rendimiento.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: aa8e9af0c4ca25b29e0194e5515250ceb4cd6254
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908646"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Cómo: Agregar una regla de umbral mediante el Editor de pruebas de carga

Las reglas de umbral de las pruebas de carga comparan un valor de contador de rendimiento con un valor constante o con otro valor de contador de rendimiento.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>Para agregar una regla de umbral

1. Abra una prueba de carga.

2. En el Editor de pruebas de carga, expanda el nodo **Conjuntos de contadores**.

3. Expanda una de las **Categorías de contador** en uno de los Conjuntos de contadores. Por ejemplo, puede seleccionar **LoadTest:Scenario**. Expanda el nodo.

4. Haga clic con el botón derecho en uno de los contadores, por ejemplo, **Carga de usuarios**, bajo **LoadTest:Scenario**. Seleccione **Agregar regla de umbral**.

     Se mostrará el cuadro de diálogo **Agregar regla de umbral**.

5. Puede elegir dos tipos de reglas: **Comparar constante** y **Comparar contador**. Seleccione el tipo adecuado y establezca los valores.

    > [!NOTE]
    > Establezca la propiedad **Alertar si se supera** en **True** para indicar que exceder un umbral supone un problema, o en **False** para indicar que no alcanzar un umbral supone un problema.

## <a name="see-also"></a>Vea también

- [Analizar las infracciones de las reglas de umbral](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Especificar los conjuntos de contadores y las reglas de umbral para equipos en una prueba de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analizar los resultados de pruebas de carga con el analizador de pruebas de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
