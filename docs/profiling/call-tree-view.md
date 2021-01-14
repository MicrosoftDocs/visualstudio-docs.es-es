---
title: Vista Árbol de llamadas | Microsoft Docs
description: Conozca la vista Árbol de llamadas, que muestra las rutas de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386f8e85c02fe73eab9801b3edf79ec0d0b178fc
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150787"
---
# <a name="call-tree-view"></a>Vista Árbol de llamadas
La vista Árbol de llamadas muestra las rutas de acceso de ejecución de funciones que se recorrieron en la aplicación de la que se generaron perfiles. La raíz del árbol es el punto de entrada a la aplicación o el componente. Cada nodo de función muestra todas las funciones a las que ha llamado, así como los datos de rendimiento de esas llamadas a funciones.

 La vista Árbol de llamadas también puede expandir y resaltar la ruta de acceso de ejecución de una función que consumió más tiempo o de la que se han tomado muestras con más frecuencia. Para mostrar la ruta de acceso más exigente, haga clic con el botón derecho en la función y, después, haga clic en **Expandir ruta de acceso activa**.

 Cada proceso en la ejecución de generación de perfiles se muestra como un nodo raíz. Para establecer el nodo de inicio de la vista Árbol de llamadas, haga clic con el botón derecho en el nodo que quiere establecer como nodo de inicio y seleccione **Establecer raíz**.

 Al establecer el nodo raíz, se eliminan todas las demás entradas de la vista, excepto el subárbol del nodo seleccionado. Puede restablecer el nodo raíz en el nodo que estaba viendo. En la ventana de la vista Árbol de llamadas, haga clic con el botón derecho y seleccione **Restablecer raíz**.

 La vista Árbol de llamadas se puede personalizar para agregar o quitar columnas. Haga clic con el botón derecho en la **barra de título del nombre de columna** y seleccione **Agregar o quitar columnas**.

 La vista Árbol de llamadas puede configurarse para la reducción de ruido si se limita la cantidad de datos que se presentan. Gracias a la reducción de ruido, los problemas de rendimiento destacan más en la vista. Cuando los problemas de rendimiento son fáciles de distinguir, el análisis resulta más sencillo. Para más información, vea [Cómo: Configurar la reducción de ruido en las vistas de informes](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Si la reducción de ruido está configurada para mostrar una advertencia cuando se habilita, se mostrará una barra de información en el informe.

 Para obtener más información sobre las definiciones de las columnas de la vista Árbol de llamadas, vea lo siguiente:

- [Vista Árbol de llamadas](../profiling/call-tree-view-sampling-data.md)

- [Vista Árbol de llamadas](../profiling/call-tree-view-instrumentation-data.md)

- [Vista Árbol de llamadas: muestreo](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Vista Árbol de llamadas](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Vea también
- [Vistas de informes de rendimiento](../profiling/performance-report-views.md)
- [Descripción de los valores de datos de instrumentación](../profiling/understanding-instrumentation-data-values.md)
- [Descripción de los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)
