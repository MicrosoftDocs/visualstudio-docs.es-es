---
title: Llamar a los eventos del depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9682e16c059483d44953ffbe11d8e10e6d46a435
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767509"
---
# <a name="calling-debugger-events"></a>Llamada a eventos del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Se producen eventos en las sesiones de depuración en un orden específico.  
  
## <a name="discussion"></a>Explicación  
 Para entender el patrón de las llamadas entre el motor de depuración (DE) y el Administrador de depuración de la sesión (SDM), el siguiente representa el orden de llamada de los eventos que se producen en una sesión de depuración típica:  
  
1.  [Asociación y desasociación a un programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Iniciar el depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Terminación de un programa](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Creación de un punto de interrupción](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Cuando se enlaza un punto de interrupción o convertirse en no enlazados](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Errores de punto de interrupción](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Alcanzar un punto de interrupción](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Eliminar un punto de interrupción](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Modo de interrupción](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Ejecución paso a paso en modo de interrupción](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Control de excepciones](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)

