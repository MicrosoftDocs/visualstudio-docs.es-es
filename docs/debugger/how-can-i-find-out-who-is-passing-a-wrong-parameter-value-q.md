---
title: "C&#243;mo averiguar qui&#233;n est&#225; pasando un valor de par&#225;metro err&#243;neo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depurar [C++], parámetros"
  - "funciones [depurador], detectar valores incorrectos de parámetros"
  - "valores de parámetros, solucionar problemas"
  - "parámetros [depurador]"
  - "pasar parámetros, solucionar problemas de valores incorrectos"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo averiguar qui&#233;n est&#225; pasando un valor de par&#225;metro err&#243;neo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descripción del problema  
 Una de las funciones recibe un valor de parámetro erróneo.  La llamada a esta función se realiza desde múltiples lugares.  ¿Cómo puedo averiguar qué llamada está pasando el valor erróneo?  
  
## Soluciones  
  
#### Para solucionar este problema  
  
1.  Establezca un punto de interrupción de ubicación al principio de la función.  
  
2.  Haga clic con el botón secundario del mouse en el punto de interrupción y seleccione **Condición**.  
  
3.  En el cuadro de diálogo **Condición del punto de interrupción**, active la casilla **Condición**.  Vea [Puntos de interrupción avanzados](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Escriba una expresión, como `Var==3`, en el cuadro de texto, donde `Var` es el nombre del parámetro que contiene el valor no válido, y `3` es el valor no válido que se le ha pasado.  
  
5.  Seleccione el botón de radio **es True** y haga clic en el botón **Aceptar**.  
  
6.  Ejecute el programa otra vez.  El punto de interrupción hace que el programa se detenga al principio de la función cuando el parámetro `Var` sea `3`.  
  
7.  Utilice la ventana Pila de llamadas para detectar la función que realizó la llamada y navegar hasta su código fuente.  Para obtener más información, vea [Cómo: Utilizar la ventana Pila de llamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)