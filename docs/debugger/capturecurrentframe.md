---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Captura el resto del fotograma actual en el archivo de registro de gráficos.  
  
## Sintaxis  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Comentarios  
 Si hay otra captura en curso actualmente, como una captura que inició la función `BeginCapture`, esa captura se completa y se registra en el registro de gráficos como un fotograma distinto.  Inmediatamente después, el diagnóstico de gráficos empieza a capturar el resto del fotograma actual, que también se registra como un fotograma distinto.  El final del fotograma actual se marca mediante una llamada de presentación.  
  
 Para capturar un fotograma, debe preparar la aplicación para capturar y grabar información de gráficos; es decir, debe haber llamado a [Init](../debugger/init.md) a través de una instancia de la clase `VsgDbg` antes de llamar a `CaptureCurrentFrame`.  
  
## Vea también  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)