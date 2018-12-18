---
title: 'Cómo: Recopilar datos de muestreo en el nivel de línea | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, line-level sampling
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 21ef50736e00bd835b4e1bc88530d2aaef30ee82
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767545"
---
# <a name="how-to-collect-line-level-sampling-data"></a>Cómo: Recopilar datos de muestreo en el nivel de línea
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El muestreo en el nivel de línea es la capacidad del generador de perfiles para determinar en qué punto del código de una función de uso intensivo del procesador, como una función con muestras muy exclusivas, el procesador tiene que dedicar más tiempo.  
  
## <a name="overview"></a>Información general  
 Para el muestreo en el nivel de línea, el generador de perfiles recorre la pila de llamadas del programa a intervalos establecidos y agrega los resultados. Estos resultados muestran qué instrucciones ejecutaba el procesador cuando se tomaron las muestras. Después se analizan los datos recopilados sobre muestras exclusivas para identificar las líneas de código y el puntero de instrucción (IP).  
  
 El muestreo en el nivel de línea funciona para código administrado y nativo. Los informes de rendimiento que muestran estos datos incluyen la vista Líneas y la vista Módulos.  
  
 La información de inicio y fin de caracteres no está disponible para el código nativo. Para las instrucciones multilínea, la información de inicio de línea no está disponible para código nativo, solo está disponible la información de final de línea.  
  
### <a name="available-data"></a>Datos disponibles  
 Los datos de muestreo en el nivel de la línea disponibles incluyen la siguiente información:  
  
- Nombre de la función.  
  
- Dirección de la función.  
  
- Inicio de línea: número de línea del código muestreado.  
  
- Línea final: número de la línea final del código fuente. Este suele ser el mismo que los datos de "Inicio de línea", excepto cuando una sola instrucción de programa abarca varias líneas de código fuente.  
  
- Inicio de carácter: columna inicial de la muestra agregada. Generalmente es 0, salvo cuando una sola línea contiene varias instrucciones de programa.  
  
- Final de carácter: columna final de la muestra agregada.  
  
- Dirección IP: dirección donde se tomó la muestra agregada (solo para la vista IP).  
  
  En la vista **Módulos**, si una función tiene estadísticas de nivel de línea, las estadísticas se anidan bajo cada función. Además, se presentan las estadísticas de nivel de IP anidadas bajo cada línea.  
  
### <a name="turn-off-line-level-sampling-for-managed-code"></a>Desactivar el muestreo en el nivel de línea para código administrado  
 De forma predeterminada, el muestreo en el nivel de línea está activado. Puede desactivar la recolección de datos en el nivel de línea de código administrado mediante uno de los siguientes procedimientos:  
  
-   Antes de la generación de perfiles, escriba **VSPerfCLREnv /samplelineoff**. Esto afecta a aplicaciones y servicios.  
  
     o  
  
-   Al iniciar una aplicación, escriba **VSPerfCmd /lineoff \<other arguments>**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Analizar datos de herramientas de rendimiento](../profiling/analyzing-performance-tools-data.md)



