---
title: Vista Marcas | Microsoft Docs
description: Obtenga más información sobre cómo se muestran en la vista Marcas los eventos de ETW y muestreo que se insertaron en la aplicación.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b5b7eedaf7aac4a22ca10580395e085243f831ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851977"
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

## <a name="see-also"></a>Consulte también
- [Información general sobre el informe de rendimiento](../profiling/performance-report-overview.md)
- [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; Control de recolección de datos (ventana)](/previous-versions/bb385767(v=vs.110))