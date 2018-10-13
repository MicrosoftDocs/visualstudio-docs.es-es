---
title: Determinar qué llamada genera el error cuando se llama a una función varias veces | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60e01816d6b123c95b8bab07189710869d0193f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180991"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Determinar qué llamada genera el error cuando se llama a una función varias veces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descripción del problema  
 El programa presenta un error en una llamada a una cierta función, `CnvtV`. El programa probablemente llama a esa función unas doscientas veces antes del error. Si se define un punto de interrupción en `CnvtV`, el programa se detiene en todas las llamadas a esa función, pero no es eso lo que se pretende. No se sabe qué condiciones hacen que la llamada produzca un error, de modo que no se puede establecer un punto de interrupción condicional. ¿Qué puedo hacer?  
  
## <a name="solution"></a>Soluciones  
 Puede establecer un punto de interrupción en la función con el **recuento de visitas** campo a un valor tan alto que no se puede alcanzar. En este caso, porque la función `CnvtV` se invoca unas doscientas veces, puede establecer **recuento de visitas** 1000 o más. A continuación, ejecute el programa y espere a que se produzca el error de la llamada. Cuando lo haga, abra la ventana Puntos de interrupción y examine la lista de puntos de interrupción. El punto de interrupción definido sobre `CnvtV` aparece seguido del número de llamadas y el número de iteraciones restantes:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Ahora sabe que la función produjo un error en la llamada nº 101. Si restablece el punto de interrupción con un número de llamadas de 101 y ejecuta el programa otra vez, éste se detiene en la llamada a `CnvtV` que causó el error.  
  
## <a name="see-also"></a>Vea también  
 [Preguntas frecuentes sobre depuración de código nativo](../debugger/debugging-native-code-faqs.md)   
 [Establecer puntos de interrupción](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)



