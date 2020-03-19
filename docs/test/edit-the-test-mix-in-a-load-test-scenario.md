---
title: Combinación de pruebas para un escenario de pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, adding tests
- test mix
- load tests, test mix
- load tests, removing tests
ms.assetid: 303e1d70-5d98-424a-b51e-e0898e16d3f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a52d660140416ce829493a733171cfcf64ebbe4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595935"
---
# <a name="edit-the-test-mix-to-specify-which-web-performance-unit-and-coded-ui-tests-to-include-in-a-load-test-scenario"></a>Edición de la combinación de pruebas para especificar qué pruebas de rendimiento web, unitarias y automatizadas de IU incluir en un escenario de prueba de carga

La *combinación de pruebas* de un escenario es un grupo de la selección de pruebas unitarias y de rendimiento web contenidas en el escenario y su distribución dentro de este. La distribución es una configuración que puede especificar de la probabilidad de que una prueba sea seleccionada por un explorador determinado durante la ejecución de una prueba de carga.

Después de agregar un conjunto de pruebas a una prueba de carga, la *combinación de pruebas* funciona como otras opciones de combinación. Un usuario virtual selecciona de forma aleatoria una prueba, basándose en la probabilidad que se haya especificado en la combinación. Por ejemplo, si tiene dos pruebas, cada una al 50% en la combinación, un nuevo usuario virtual elegirá ejecutar la primera aproximadamente la mitad del tiempo. En una combinación 50/50, si una prueba es larga y otra es corta, más carga procede de la prueba larga.

Las pruebas que agregue a la combinación puede quitarlas posteriormente. También puede cambiar la distribución de la combinación de pruebas utilizando el control de combinación. El control de combinación permite ajustar con facilidad la distribución de pruebas en un escenario.

> [!NOTE]
> La distribución es una medida de la probabilidad de que un usuario virtual seleccione una prueba determinada durante una ejecución de la prueba de carga. La distribución se expresa como un porcentaje. Por lo tanto, la suma de los números de distribución de todas las pruebas incluidas en un escenario es 100. Por ejemplo, si un escenario contiene solo una prueba, la distribución para esa prueba es 100%.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="add-new-tests-to-a-test-mix-in-an-existing-scenario"></a>Agregar pruebas nuevas a una combinación de pruebas en un escenario existente

Al crear un nuevo escenario mediante el **Asistente para prueba de carga nueva**, puede especificar las pruebas unitarias y de rendimiento web para agregar a la combinación de pruebas del nuevo escenario.

Puede agregar más pruebas unitarias y de rendimiento web a la combinación de pruebas del escenario con el **Editor de pruebas de carga**.

![Agregar una prueba a una prueba de carga existente](../test/media/ltest_addingtests.png)

### <a name="to-add-more-tests-to-an-existing-scenario"></a>Para agregar más pruebas a un escenario existente

1. Abra una prueba de carga.

2. En el **Editor de pruebas de carga**, haga clic con el botón derecho en un escenario existente y, a continuación, elija **Agregar pruebas**.

     Aparecerá el cuadro de diálogo **Agregar pruebas**. Todas las pruebas de rendimiento web, unitarias y automatizadas de IU de la solución que aún no estén en el escenario estarán disponibles para agregarse.

3. En el panel **Pruebas disponibles**, seleccione las pruebas de rendimiento web, unitarias y automatizadas de IU que desee agregar. Elija la flecha derecha para agregar las pruebas al panel **Pruebas seleccionadas**.

4. Cuando haya terminado de agregar pruebas, elija **Aceptar**.

     Las pruebas se agregan a la combinación de pruebas. Automáticamente, se asigna una nueva distribución a las pruebas de la combinación de pruebas.

5. (Opcional) Ajuste el control de combinación para especificar la distribución de pruebas. Para más información, consulte [Control de combinaciones](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

## <a name="remove-tests-from-a-scenario"></a>Eliminación de pruebas de un escenario
![Quitar una prueba de una prueba de carga existente](../test/media/ltest_removetest.png)

### <a name="to-remove-tests-from-a-scenario"></a>Para quitar pruebas de un escenario

1. Abra una prueba de carga.

2. En el **Editor de pruebas de carga**, en el árbol de pruebas de carga, haga clic con el botón derecho en el escenario del que desea quitar una prueba y seleccione **Editar combinación de pruebas**. Aparecerá el cuadro de diálogo **Editar combinación de pruebas**.

3. Seleccione la prueba de rendimiento web, la prueba unitaria o la prueba automatizada de IU en la cuadrícula y, a continuación, elija **Quitar**.

    > [!NOTE]
    > Después de quitar la prueba, ajuste la combinación de pruebas según la distribución que prefiera.

4. Cuando haya terminado de quitar pruebas, elija **Aceptar**.

## <a name="EditingTestMixAboutMixControl"></a> Control de combinación
El control de combinación permite ajustar el porcentaje de carga que se distribuye entre las pruebas, tipos de exploradores o tipos de redes en un escenario de prueba de carga. Para ajustar los valores de porcentajes, tiene que mover los controles deslizantes. Al ajustar la combinación para pruebas se especifica la probabilidad de que un supuesto usuario ejecute una prueba concreta en un escenario de prueba de carga.

Al mover un control deslizante, cambian los valores de porcentaje de todos los elementos disponibles. Si tiene más de dos elementos, la cantidad que agregue o quite se distribuirá uniformemente entre los demás elementos. Es posible reemplazar este comportamiento. Si activa la casilla de la columna de bloqueo de un elemento determinado, bloqueará el valor de porcentaje especificado para dicho elemento. Entonces, cuando mueva un control deslizante, la cantidad que agregue o quite sólo se aplicará a los elementos desbloqueados restantes.

El botón **Distribuir** se utiliza para asignar porcentajes equitativos entre todos los elementos. Por ejemplo, si tiene tres elementos, al elegir **Distribuir**, los valores de porcentaje se establecen en 34, 33 y 33.

> [!WARNING]
> El botón **Distribuir** reemplaza a cualquier elemento que esté bloqueado.

También es posible escribir directamente los valores de porcentaje en la columna **%** , en lugar de usar los controles deslizantes. Si escribe un valor de porcentaje directamente, los demás elementos no se ajustarán automáticamente.

> [!NOTE]
> Los controles deslizantes se deshabilitan cuando el total no suma un 100 % o cuando los valores de porcentaje especificados en la columna **%** son decimales.

Si escribe los valores de porcentajes manualmente, debe asegurarse de que la suma de todos los elementos sea 100 %. Al guardar una combinación, si la suma no es igual al 100 %, se le solicitará que acepte los valores de porcentajes tal y como están o que vuelva a ajustarlos. Si decide aceptarlos tal y como están, se prorratearán al 100%.  Por ejemplo, si tiene dos elementos y los establece manualmente en un 80% y un 40%, el primer elemento se establecerá en un 66,67% (80 dividido entre 120) y el segundo elemento se establecerá en un 33,33% (40 dividido entre 120).

## <a name="see-also"></a>Vea también

- [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md)
