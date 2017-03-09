---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finaliza un intervalo de captura que se inició con `BeginCapture`.  
  
## Sintaxis  
  
```cpp  
void EndCapture();  
```  
  
## Comentarios  
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw.  Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos.  El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.  
  
 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos; es decir, debe haber llamado a [Init](../debugger/init.md) a través de una instancia de la clase `VsgDbg` antes de llamar a `BeginCapture` o `EndCapture`.  
  
## Vea también  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)