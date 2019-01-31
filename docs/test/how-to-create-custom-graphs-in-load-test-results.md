---
title: Procedimiento para crear gráficos personalizados en los resultados de pruebas de carga
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: 8fd80a4d7cbfeb7cf79ae3dddad9aa1da367fd87
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992781"
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Procedimiento para crear gráficos personalizados en los resultados de pruebas de carga

puede diseñar gráficos que muestren información específica sobre los resultados de pruebas de carga. Los gráficos personalizados se diseñan especificando los contadores de la prueba de carga que se van a mostrar en el gráfico.

Puede realizar el procedimiento siguiente mientras se ejecuta una prueba de carga o cuando termine de ejecutarse.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-load-test-results-graph"></a>Para crear un gráfico de resultados de pruebas de carga personalizado

1.  En la barra de herramientas **Prueba de carga**, elija **Agregar nuevo gráfico**.

     \- o -

     En el **Analizador de pruebas de carga**, haga clic con el botón derecho en el panel **Contadores** o en un gráfico y luego seleccione **Agregar gráfico**.

     Se muestra el cuadro de diálogo **Escribir el nombre del gráfico**.

2.  En **Nombre del gráfico**, escriba un nombre para el gráfico y elija **Aceptar**.

     El nuevo gráfico aparece en el **Analizador de pruebas de carga**. Aparece en el panel de gráfico actualmente seleccionado y reemplaza al gráfico que se mostraba en ese panel.

3.  Personalice el nuevo gráfico agregando contadores. Para obtener más información, vea [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Vea también

- [Analizar los resultados de pruebas de carga en la vista Gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Cómo: Agregar y eliminar contadores de los gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)