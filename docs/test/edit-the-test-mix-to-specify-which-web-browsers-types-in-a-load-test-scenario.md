---
title: Combinación de pruebas de exploradores para pruebas de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, web browser types
- load tests, scenarios
- load tests, adding browsers
- load tests, removing browsers
ms.assetid: 47f981d9-3038-45cc-a486-82b9daf9a9a1
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: be0bd036c907f852028f6a9cccc798742e624184
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario"></a>Editar la combinación de pruebas para especificar tipos de exploradores web en un escenario de prueba de carga

La *combinación de exploradores* le ofrece una forma más realista de simular la carga en un escenario de prueba de carga. La carga se genera utilizando una combinación heterogénea de exploradores web, en lugar de uno solo. Se crea una aproximación más parecida a los exploradores web que se utilizarán con sus aplicaciones.

 Una combinación de exploradores especifica la probabilidad de que un usuario virtual ejecute un tipo de explorador web determinado en un escenario de prueba de carga. Durante la creación de una prueba de carga, puede ser conveniente simular que la carga se genera con varios exploradores web. Cuando se agrega un tipo de explorador web a la combinación desde el conjunto de exploradores web suministrado, se agrega un conjunto de encabezados asociados al explorador seleccionado a cada solicitud HTTP enviada por una prueba de rendimiento web.

 La combinación de exploradores funciona como otras opciones de combinación. Se asocia un tipo de explorador web de forma aleatoria a un usuario virtual, basándose en la combinación de exploradores web. Las pruebas de ese usuario se ejecutan en un explorador web determinado, en función de la probabilidad especificada en la combinación.

 Después de especificar una combinación de exploradores web, puede agregarle y quitarle tipos de exploradores. También puede cambiar la distribución de la combinación de exploradores utilizando el control de combinación. El control de combinación permite ajustar con facilidad la distribución de exploradores en un escenario.

## <a name="adding-new-browsers-to-a-scenario"></a>Agregar nuevos exploradores a un escenario

### <a name="to-add-new-browsers-to-a-scenario"></a>Para agregar nuevos exploradores a un escenario

1.  Cuando vaya a especificar la combinación de exploradores para un escenario, elija **Agregar**.

     Se agregará una nueva entrada de explorador a la cuadrícula.

    > [!NOTE]
    > Para mostrar el cuadro de diálogo **Editar combinación de exploradores**, haga clic con el botón derecho en un escenario existente y, luego, elija **Editar combinación de exploradores**.

2.  En la columna **Tipo de explorador**, elija la flecha que corresponde a la nueva entrada y elija el tipo de explorador deseado.

3.  (Opcional) Ajuste el control de combinación para especificar la distribución de pruebas.

4.  Cuando haya terminado de agregar exploradores, elija **Aceptar**.

##  <a name="EditingTestMixSpecifyBrowserRemovingBrowserTypes"></a> Quitar exploradores de un escenario

### <a name="to-remove-browsers-from-a-scenario"></a>Para quitar exploradores de un escenario

1.  Abra una prueba de carga.

2.  Haga clic con el botón derecho en el escenario del que quiere quitar un explorador y, luego, elija **Editar combinación de exploradores**.

     Se abre el cuadro de diálogo **Editar combinación de exploradores**.

3.  Seleccione el explorador en la cuadrícula y, luego, elija **Quitar**.

4.  (Opcional) Ajuste el control de combinación para especificar la distribución de pruebas.

5.  Cuando haya terminado de quitar exploradores, elija **Aceptar**.

## <a name="about-the-mix-control"></a>Control de combinación

 El control de combinación permite ajustar el porcentaje de carga que se distribuye entre las pruebas, tipos de exploradores o tipos de redes en un escenario de prueba de carga. Para ajustar los valores de porcentajes, tiene que mover los controles deslizantes. Una combinación de exploradores especifica la probabilidad de que un usuario virtual ejecute un tipo de explorador determinado en un escenario de prueba de carga.

 Al mover un control deslizante, cambian los valores de porcentaje de todos los elementos disponibles. Si tiene más de dos elementos, la cantidad que agregue o quite se distribuirá uniformemente entre los demás elementos. Es posible reemplazar este comportamiento. Si activa la casilla de la columna de bloqueo de un elemento determinado, bloqueará el valor de porcentaje especificado para dicho elemento. Entonces, cuando mueva un control deslizante, la cantidad que agregue o quite sólo se aplicará a los elementos desbloqueados restantes.

 El botón **Distribuir** se usa para asignar los valores de porcentaje de forma equitativa entre todos los elementos. Por ejemplo, si tiene tres elementos, al elegir **Distribuir**, los valores de porcentaje se establecen en 34, 33 y 33.

> [!WARNING]
> El botón **Distribuir** reemplaza a cualquier elemento que esté bloqueado.

 También es posible escribir directamente los valores de porcentaje en la columna **%**, en lugar de usar los controles deslizantes. Si escribe un valor de porcentaje directamente, los demás elementos no se ajustarán automáticamente.

> [!NOTE]
> Los controles deslizantes se deshabilitan cuando el total no suma un 100 % o cuando los valores de porcentaje especificados en la columna **%** son decimales.

 Si escribe los valores de porcentajes manualmente, debe asegurarse de que la suma de todos los elementos sea 100 %. Al guardar una combinación, si la suma no es igual al 100 %, se le solicitará que acepte los valores de porcentajes tal y como están o que vuelva a ajustarlos. Si decide aceptarlos tal y como están, se prorratearán al 100%.  Por ejemplo, si tiene dos elementos y los establece manualmente en un 80% y un 40%, el primer elemento se establecerá en un 66,67% (80 dividido entre 120) y el segundo elemento se establecerá en un 33,33% (40 dividido entre 120).

## <a name="see-also"></a>Vea también

- [Edición de escenarios de prueba de carga](../test/edit-load-test-scenarios.md)