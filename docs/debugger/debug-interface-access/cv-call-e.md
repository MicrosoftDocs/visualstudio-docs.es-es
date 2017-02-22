---
title: "CV_call_e | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CV_call_e (enumeración)"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica la convención de llamada para una función.  
  
> [!NOTE]
>  Solo los valores de enumeración más comunes se documentan aquí.  La enumeración completa está disponible en el archivo de encabezado cvconst.h.  
  
## Sintaxis  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elementos \(Elements\)  
 CV\_CALL\_NEAR\_C  
 Especifica una convención de llamada mediante de derecha a izquierda una inserción de cierre.  La función de llamada borra la pila.  
  
 CV\_CALL\_NEAR\_FAST  
 Especifica una convención de llamada mediante una inserción de izquierda a derecha próxima con los registros.  La función llamada utiliza la suma de bytes de parámetro para borrar la pila.  
  
 CV\_CALL\_NEAR\_STD  
 Especifica una convención de llamada mediante una llamada estándar próxima \(de derecha a izquierda inserción\).  
  
 CV\_CALL\_NEAR\_SYS  
 Especifica una convención de llamada mediante una llamada al sistema de cierre.  
  
 CV\_CALL\_THISCALL  
 Especifica una convención de llamada mediante la llamada a `this` \(puntero de`this` pasado en el registro\).  
  
 CV\_CALL\_CLRCALL  
 Especifica una convención de llamada que utiliza Common Language Runtime \(CLR\) \(también conocido como convención de llamada de código administrado\).  
  
## Comentarios  
 Los valores de esta enumeración son devueltos por una llamada al método de [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## Requisitos  
 encabezado: cvconst.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)