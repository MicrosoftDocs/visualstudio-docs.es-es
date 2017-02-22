---
title: "Determinar qu&#233; llamada genera el error cuando se llama a una funci&#243;n varias veces | Microsoft Docs"
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
  - "vs.debug.functions"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "puntos de interrupción, solucionar problemas"
  - "puntos de interrupción condicionales"
  - "errores [depurador], buscar qué llamada a una función genera un error"
  - "errores [depurador], llamadas a funciones"
  - "errores [Visual Studio], llamadas a funciones"
  - "errores"
  - "llamadas a funciones, error"
  - "funciones [depurador]"
  - "recuentos de visitas"
  - "errores de llamada de puntos de interrupción"
  - "Omitir cuenta"
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Determinar qu&#233; llamada genera el error cuando se llama a una funci&#243;n varias veces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descripción del problema  
 El programa presenta un error en una llamada a una cierta función, `CnvtV`.  El programa probablemente llama a esa función unas doscientas veces antes del error.  Si se define un punto de interrupción en `CnvtV`, el programa se detiene en todas las llamadas a esa función, pero no es eso lo que se pretende.  No se sabe qué condiciones hacen que la llamada produzca un error, de modo que no se puede establecer un punto de interrupción condicional.  ¿Qué puedo hacer?  
  
## Soluciones  
 Puede establecer un punto de interrupción en la función con el campo **Número de llamadas** establecido en un valor tan alto que no se pueda alcanzar.  En este caso, como la función `CnvtV` se invoca unas doscientas veces, asigne a **Número de llamadas** un valor de 1000 o superior.  A continuación, ejecute el programa y espere a que se produzca el error de la llamada.  Cuando lo haga, abra la ventana Puntos de interrupción y examine la lista de puntos de interrupción.  El punto de interrupción definido sobre `CnvtV` aparece seguido del número de llamadas y el número de iteraciones restantes:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Ahora sabe que la función produjo un error en la llamada nº 101.  Si restablece el punto de interrupción con un número de llamadas de 101 y ejecuta el programa otra vez, éste se detiene en la llamada a `CnvtV` que causó el error.  
  
## Vea también  
 [Preguntas más frecuentes sobre la depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Setting Breakpoints](http://msdn.microsoft.com/es-es/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)