---
title: Detenga la depuración en el cuadro de diálogo de progreso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35e97e6a7f2b9eddb5694956633bc5bd79d8e426
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Detener depuración en curso (cuadro de diálogo)
Este cuadro de diálogo aparece cuando el depurador intenta detener una sesión de depuración y este proceso tarda cierto tiempo. En general, una sesión de depuración se detiene rápidamente y no aparece este cuadro de diálogo. Sin embargo, a veces se tarda más tiempo en desasociar todos los procesos que se están depurando. Si detener la sesión tarda más de unos segundos (o si se produce un error al desasociar), aparece este cuadro de diálogo. Si esto sucede con frecuencia, puede que se deba a un problema interno y convendría ponerse en contacto con los Servicios de soporte técnico.  
  
 Puede esperar los procesos se desasocien y desaparezca este cuadro de diálogo, o utilizar el **detener ahora** botón para forzar la finalización inmediata.  
  
 **¿Desea detener ahora**  
 Haga clic en este botón para detener la sesión de depuración inmediatamente. Usar **detener ahora** terminarán en lugar de separar los procesos que se está depurados. Si está depurando procesos del sistema, terminar los procesos con **detener ahora** puede tener efectos inesperados y no deseados.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Desasociar programas](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)