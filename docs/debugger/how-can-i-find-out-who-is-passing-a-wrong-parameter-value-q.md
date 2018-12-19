---
title: Averiguar quién está pasando un valor de parámetro erróneo | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164ca15cfc508b952ccfe2f986892c0801fd1539
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059371"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Cómo averiguar quién está pasando un valor de parámetro erróneo
## <a name="problem-description"></a>Descripción del problema  
 Una de las funciones recibe un valor de parámetro erróneo. La llamada a esta función se realiza desde múltiples lugares. ¿Cómo puedo averiguar qué llamada está pasando el valor erróneo?  
  
## <a name="solution"></a>Soluciones  
  
#### <a name="to-resolve-this-problem"></a>Para solucionar este problema  
  
1.  Establezca un punto de interrupción de ubicación al principio de la función.  
  
2.  Haga clic con el botón derecho en el punto de interrupción y seleccione **Condición**.  
  
3.  En el cuadro de diálogo **Condición del punto de interrupción**, active la casilla **Condición**. Consulte [avanzada de puntos de interrupción](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Escriba una expresión, como `Var==3`, en el cuadro de texto, donde `Var` es el nombre del parámetro que contiene el valor no válido, y `3` es el valor no válido que se le ha pasado.  
  
5.  Seleccione el botón de radio **es True** y haga clic en el botón **Aceptar**.  
  
6.  Ejecute el programa otra vez. El punto de interrupción hace que el programa se detenga al principio de la función cuando el parámetro `Var` sea `3`.  
  
7.  Utilice la ventana Pila de llamadas para detectar la función que realizó la llamada y navegar hasta su código fuente. Para obtener más información, vea [Cómo: usar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Puntos de interrupción](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)