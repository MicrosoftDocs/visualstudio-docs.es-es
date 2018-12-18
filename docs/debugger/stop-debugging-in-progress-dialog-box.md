---
title: Detener la depuración en el cuadro de diálogo de progreso | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 3a6e13967cc18fae8d837cc71ea8a91c60f2b1bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281200"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Detener depuración en curso (cuadro de diálogo)
Este cuadro de diálogo aparece cuando el depurador intenta detener una sesión de depuración y este proceso tarda cierto tiempo. En general, una sesión de depuración se detiene rápidamente y no aparece este cuadro de diálogo. Sin embargo, a veces se tarda más tiempo en desasociar todos los procesos que se están depurando. Si detener la sesión tarda más de unos segundos (o si se produce un error al desasociar), aparece este cuadro de diálogo. Si esto sucede con frecuencia, puede que se deba a un problema interno y convendría ponerse en contacto con los Servicios de soporte técnico.  
  
 Puede esperar de los procesos se desasocien y desaparezca este cuadro de diálogo, o usar el **detener ahora** botón para forzar la finalización inmediata.  
  
 **Detener ahora**  
 Haga clic en este botón para detener la sesión de depuración inmediatamente. Uso de **detener ahora** finalizará en lugar de separar los procesos que se está depurados. Si está depurando procesos del sistema, terminar los procesos con **detener ahora** puede tener efectos inesperados y no deseados.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Desasociar programas](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))