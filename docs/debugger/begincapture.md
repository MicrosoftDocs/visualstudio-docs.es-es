---
title: "BeginCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BeginCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicia un intervalo de captura que finalizará con `EndCapture`.  
  
## Sintaxis  
  
```cpp  
void BeginCapture();  
```  
  
## Comentarios  
 Un intervalo de captura suele abarcar un subconjunto de un fotograma, por ejemplo cuando desea capturar información de gráficos solo sobre algún tipo de llamada a Draw.  Si el intervalo de captura abarca una llamada de presentación, se capturan dos fotogramas de información de gráficos.  El primer fotograma abarca el intervalo entre la llamada a `BeginCapture` y la llamada de presentación; el segundo fotograma abarca el intervalo entre el primer evento de Direct3D después de la llamada de presentación y la llamada a `EndCapture`.  
  
 Para capturar un intervalo, debe preparar la aplicación para capturar y grabar información de gráficos; es decir, debe haber llamado a [Init](../debugger/init.md) a través de una instancia de la clase `VsgDbg` antes de llamar a `BeginCapture` o `EndCapture`.  
  
## Vea también  
 [EndCapture](../debugger/endcapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)