---
title: Detener depuración en curso (cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.stopnow
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4fc4b72987be726ab06aeb92a0e3eec2a338949e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684947"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Detener depuración en curso (cuadro de diálogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este cuadro de diálogo aparece cuando el depurador intenta detener una sesión de depuración y este proceso tarda cierto tiempo. En general, una sesión de depuración se detiene rápidamente y no aparece este cuadro de diálogo. Sin embargo, a veces se tarda más tiempo en desasociar todos los procesos que se están depurando. Si detener la sesión tarda más de unos segundos (o si se produce un error al desasociar), aparece este cuadro de diálogo. Si esto sucede con frecuencia, puede que se deba a un problema interno y convendría ponerse en contacto con los Servicios de soporte técnico.  
  
 Puede esperar a que los procesos se desasocien y desaparezca este cuadro de diálogo, o utilizar el botón **Detener ahora** para forzar la finalización inmediata.  
  
 **Detener ahora**  
 Haga clic en este botón para detener la sesión de depuración inmediatamente. El uso de **Stop Now**finalizará en lugar de desasociar los procesos que se están depurando. Si está depurando procesos del sistema y utiliza **Detener ahora** para finalizarlos podrían producirse efectos inesperados y no deseados.  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Desasociar programas](https://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
