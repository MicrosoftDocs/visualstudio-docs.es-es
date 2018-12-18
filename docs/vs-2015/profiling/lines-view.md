---
title: Vista Líneas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 829db9b1f8e4826ea9761a4433e6ee1adaab49e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749977"
---
# <a name="lines-view"></a>Vista Líneas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



