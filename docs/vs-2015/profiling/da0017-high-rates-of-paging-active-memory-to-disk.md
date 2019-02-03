---
title: 'DA0017: Alta frecuencia de paginación de memoria activa en el disco | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 136a8489ed3eac621543cb40b004052c2c9d3324
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803493"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Alta frecuencia de paginación de memoria activa en el disco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id. de regla | DA0017 |  
| Categoría | Memoria y paginación |  
| Método de generación de perfiles | Todos los |  
| Mensaje | Se está produciendo una tasa alta de paginación de memoria activa en el disco. Puede que la aplicación esté enlazada a memoria.  
| Tipo de regla | Información |  
  
 Al generar perfiles mediante los métodos de muestreo, memoria de .NET o contención de recursos, debe reunir al menos 10 ejemplos para activar esta regla.  
  
## <a name="cause"></a>Motivo  
 Los datos de rendimiento del sistema que se recopilaron en la ejecución de generación de perfiles indican que se ha producido una tasa alta de memoria paginada activa hacia y desde el disco durante la ejecución de generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento de la aplicación y la capacidad de respuesta. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación.  
  
## <a name="rule-description"></a>Descripción de la regla  
  
> [!NOTE]
>  Esta regla informativa se desencadena cuando los niveles de paginación de memoria activa alcanzan una cantidad significativa. Cuando se produce un nivel extremadamente alto de paginación, se desencadena la regla de advertencia [DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md).  
  
 La paginación excesiva en el disco puede deberse a una escasez de memoria física. Si las operaciones de paginación dominan el uso del disco físico en que reside el archivo de paginación, podrían ralentizar otras operaciones de disco orientadas a aplicaciones en el mismo disco.  
  
 A menudo, las páginas se leen desde el disco o se escriben en el disco en operaciones de paginación masivas. El número de páginas de salida por segundo es a menudo mucho mayor que el número de páginas escritas por segundo, por ejemplo. Esto se debe a que las páginas de salida por segundo también incluyen páginas de datos cambiados de la caché de archivos de sistema. Sin embargo, no siempre es fácil determinar qué proceso es directamente responsable de la paginación ni por qué.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Haga doble clic en el mensaje de la ventana Lista de errores para navegar a la vista [Marcas](../profiling/marks-view.md). Busque la columna **Memory\Pages/sec**. Determine si hay fases concretas de ejecución del programa en que la actividad de E/S de paginación sea mayor que en otras.  
  
 Si se están recopilando datos de perfil para una aplicación ASP.NET en un escenario de prueba de carga, intente volver a ejecutar la prueba de carga en un equipo configurado con memoria física adicional (o RAM).  
  
 Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos y evite las API que utilizan mucha memoria, como String.Concat y String.Substring.
