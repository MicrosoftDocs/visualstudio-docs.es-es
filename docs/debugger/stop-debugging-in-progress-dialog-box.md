---
title: "Detener depuraci&#243;n en curso (Cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Detener depuración en curso (cuadro de diálogo)"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Detener depuraci&#243;n en curso (Cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando el depurador intenta detener una sesión de depuración y este proceso tarda cierto tiempo.  En general, una sesión de depuración se detiene rápidamente y no aparece este cuadro de diálogo.  Sin embargo, a veces se tarda más tiempo en desasociar todos los procesos que se están depurando.  Si detener la sesión tarda más de unos segundos \(o si se produce un error al desasociar\), aparece este cuadro de diálogo.  Si esto sucede con frecuencia, puede que se deba a un problema interno y convendría ponerse en contacto con los Servicios de soporte técnico.  
  
 Puede esperar a que los procesos se desasocien y desaparezca este cuadro de diálogo, o utilizar el botón **Detener ahora** para forzar la finalización inmediata.  
  
 **Detener ahora**  
 Haga clic en este botón para detener la sesión de depuración inmediatamente.  Si utiliza **Detener ahora**, finalizará el proceso que se está depurando, en lugar de desasociarlo.  Si está depurando procesos del sistema y utiliza **Detener ahora** para finalizarlos podrían producirse efectos inesperados y no deseados.  
  
## Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/es-es/f2c756c2-8079-474b-94c2-01c19a141a01)