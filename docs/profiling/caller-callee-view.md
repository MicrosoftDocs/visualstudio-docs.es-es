---
title: Vista Llamador y destinatario | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a6a994f5ff564860ac753787eebd293a8e2fa9c0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889738"
---
# <a name="callercallee-view"></a>Llamador y destinatario (vista)
La vista Llamador y destinatario muestra información de generación de perfiles para una función seleccionada y sus funciones primarias y secundarias. La vista Llamador y destinatario contiene tres cuadrículas:

 **Función actual** se muestra en la cuadrícula central e incluye información sobre la generación de perfiles para la función seleccionada. Los valores incluyen todas las llamadas a la función que se recopilaron en la ejecución de generación de perfiles.

 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior e incluye el número de los valores de la función seleccionada (actual) generados por llamadas de la función de llamador (primaria).

 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior e incluye información de generación de perfiles para las funciones de destinatario (secundarias) de la función seleccionada cuando la función actual llamó a la función secundaria.

 Las columnas que están disponibles en la vista Llamador y destinatario dependen del método de generación de perfiles (muestreo o instrumentación) utilizado para recopilar los datos y de si los datos de memoria de .NET se recopilaron en la ejecución de generación de perfiles.

 En la parte central de la vista Informes, puede hacer doble clic en cualquiera de las funciones que se enumeran en las otras dos partes de la vista para seleccionar una función diferente para que sea la función actual. La vista Informes se actualiza automáticamente para reflejar los cambios.

 Puede ordenar los datos si hace clic en los nombres de las columnas. Se pueden agregar columnas adicionales a la vista Llamador y destinatario. Para más información, vea [Cómo: Personalizar una pestaña integrada](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Vea también
- [Vista Llamador y destinatario: datos de muestreo](../profiling/caller-callee-view-sampling-data.md)
- [Vista Llamador y destinatario: datos de instrumentación](../profiling/caller-callee-view-instrumentation-data.md)
- [Vista Llamador y destinatario: datos de instrumentación de memoria de .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Vista Llamador y destinatario: datos de muestreo de memoria de .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Vista Llamador y destinatario: datos de contención](../profiling/caller-callee-view-contention-data.md)
