---
title: Al llamar a eventos del depurador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="calling-debugger-events"></a>Eventos del depurador que realiza la llamada
Se producen eventos en las sesiones de depuración en un orden específico.  
  
## <a name="discussion"></a>Explicación  
 Para entender el modelo de llamadas entre el motor de depuración (Alemania) y el Administrador de sesión de depuración (SDM), el siguiente ejemplo representa el orden de llamada de los eventos que se producen en una sesión de depuración típica:  
  
1.  [Adjuntar y separar a un programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Iniciar el depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Finalizar un programa](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Crear un punto de interrupción](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Cuando se enlaza un punto de interrupción o pase a ser sin enlazar](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Errores de punto de interrupción](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Alcanzar un punto de interrupción](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Eliminar un punto de interrupción](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [ENTRAR en modo de interrupción](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Ejecución paso a paso en modo de interrupción](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Evaluación de expresiones en el modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Control de excepciones](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)