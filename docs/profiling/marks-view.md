---
title: Vista Marcas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: badb2266e47fcbf0bb20c5fd6fd2f7f25a167997
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639991"
---
# <a name="marks-view"></a>Vista Marcas
En la vista Marcas se muestran eventos ETW y de muestreo que se insertaron en la aplicación.

 Las marcas predeterminadas rellenadas en el informe etiquetan el inicio y el final del programa.

 Los datos de los contadores de Windows de las marcas generadas automáticamente también se presentan en esta vista. Para obtener más información, vea [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md).

 Para crear un filtro entre dos marcas, seleccione las marcas, haga clic con el botón derecho y, a continuación, haga clic en la opción **Agregar filtro por Marcas** o **Agregar filtro por Marca de tiempo**.

 En la tabla siguiente se proporcionan las definiciones de las columnas disponibles en la vista Marcas.

 **Id. de marca** Identificador único de la marca de generación de perfiles.

 **Nombre de marca** Nombre del evento.

 **Marca de tiempo** Tiempo desde el comienzo de la generación de perfiles hasta el momento en que se registra el evento.

 Datos del contador de rendimiento de Windows Cuando se recopilan los datos del contador de rendimiento de Windows, los valores se muestran en una columna que tiene el nombre del contador.

## <a name="see-also"></a>Vea también
- [Información general sobre el informe de rendimiento](../profiling/performance-report-overview.md)
- [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; Control de recolección de datos (ventana)](https://msdn.microsoft.com/98d740d8-459f-4605-bf04-fb17aafaaa8f)