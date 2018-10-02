---
title: Vista Líneas | Microsoft Docs
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
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 975b5e7386b69e17366c48e2c7dab7c974c49689
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581791"
---
# <a name="lines-view"></a>Vista Líneas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [vista líneas](https://docs.microsoft.com/visualstudio/profiling/lines-view).  
  
La vista Líneas está disponible solo para los datos del generador de perfiles recopilados mediante el método de muestreo. La vista no está disponible para los datos recopilados mediante instrumentación.  
  
 Para los datos de perfil de muestreo, la vista Líneas identifica las instrucciones de una función que se estaba ejecutando directamente cuando se recopiló la muestra. Para los datos de memoria. NET, la vista Líneas identifica las instrucciones que asignan memoria.  
  
 En un archivo de origen, una instrucción puede abarcar más de una línea y una sola línea puede incluir más de una instrucción.  
  
 Una instrucción se identifica mediante lo siguiente:  
  
-   El archivo de código fuente que contiene la instrucción de la función.  
  
-   La función que contiene la instrucción.  
  
-   La línea de origen donde se inicia la instrucción.  
  
-   El carácter en la línea de origen donde se inicia la instrucción.  
  
-   La línea de origen donde finaliza la instrucción.  
  
-   El carácter en la línea de origen donde finaliza la instrucción.  
  
## <a name="see-also"></a>Vea también  
 [Vista Líneas](../profiling/lines-view-sampling-data.md)   
 [Vista Líneas: muestreo](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Vista Líneas](../profiling/lines-view-contention-data.md)



