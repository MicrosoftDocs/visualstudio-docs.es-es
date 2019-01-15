---
title: Detener la depuración en el cuadro de diálogo de progreso | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 3abce02ba1804ff619a7d0f24da35747c2f9ff91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883138"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Detener depuración en curso (cuadro de diálogo)
Este cuadro de diálogo aparece cuando el depurador intenta detener una sesión de depuración y este proceso tarda cierto tiempo. En general, una sesión de depuración se detiene rápidamente y no aparece este cuadro de diálogo. Sin embargo, a veces se tarda más tiempo en desasociar todos los procesos que se están depurando. Si detener la sesión tarda más de unos segundos (o si se produce un error al desasociar), aparece este cuadro de diálogo. Si esto sucede con frecuencia, puede que se deba a un problema interno y convendría ponerse en contacto con los Servicios de soporte técnico.  
  
 Puede esperar a que los procesos se desasocien y desaparezca este cuadro de diálogo, o utilizar el botón **Detener ahora** para forzar la finalización inmediata.  
  
 **Detener ahora**  
 Haga clic en este botón para detener la sesión de depuración inmediatamente. Uso de **detener ahora** finalizará en lugar de separar los procesos que se está depurados. Si está depurando procesos del sistema y utiliza **Detener ahora** para finalizarlos podrían producirse efectos inesperados y no deseados.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Desasociar programas](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))