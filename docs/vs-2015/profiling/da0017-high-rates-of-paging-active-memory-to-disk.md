---
title: 'DA0017: Alta frecuencia de paginación de memoria activa en el disco | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28aae50c9b9655c57128e7efad0ee921d54f30cf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567243"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Tasas altas de memoria paginada activa en disco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DA0017: tasas altas de paginación de memoria activa en el disco](https://docs.microsoft.com/visualstudio/profiling/da0017-high-rates-of-paging-active-memory-to-disk).  
  
Id. de regla | DA0017 |  
| Categoría | Memoria y paginación |  
| Método de generación de perfiles | Todos los |  
| Mensaje | Se está produciendo una tasa alta de paginación de memoria activa en el disco. La aplicación puede estar enlazada a memoria. |  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema que se recopilaron en la ejecución de generación de perfiles indican que se ha producido una tasa alta de memoria paginada activa hacia y desde el disco durante la ejecución de generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento de la aplicación y la capacidad de respuesta. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación.  
  
## <a name="rule-description"></a>Descripción de la regla  
  
> [!NOTE]
>  Esta regla informativa se desencadena cuando los niveles de paginación de memoria activa alcanzan una cantidad significativa. Cuando se produce un nivel extremadamente alto de paginación, se desencadena en su lugar la regla de advertencia [DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md).  
  
 La paginación excesiva en el disco puede deberse a una escasez de memoria física. Si las operaciones de paginación dominan el uso del disco físico en que reside el archivo de paginación, podrían ralentizar otras operaciones de disco orientadas a aplicaciones en el mismo disco.  
  
 A menudo, las páginas se leen desde el disco o se escriben en el disco en operaciones de paginación masivas. El número de páginas de salida por segundo es a menudo mucho mayor que el número de páginas escritas por segundo, por ejemplo. Esto se debe a que las páginas de salida por segundo también incluyen páginas de datos cambiados de la caché de archivos de sistema. Sin embargo, no siempre es fácil determinar qué proceso es directamente responsable de la paginación ni por qué.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md). Busque la columna **Memory\Pages/sec**. Determine si hay fases concretas de ejecución del programa en que la actividad de E/S de paginación sea mayor que en otras.  
  
 Si se están recopilando datos de perfil para una aplicación ASP.NET en un escenario de prueba de carga, intente volver a ejecutar la prueba de carga en un equipo configurado con memoria física adicional (o RAM).  
  
 Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos y evite las API que utilizan mucha memoria, como String.Concat y String.Substring.



