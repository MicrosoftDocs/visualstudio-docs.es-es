---
title: "CA2124: Incluir cl&#225;usulas Finally vulnerables en un bloque Try externo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2124: Incluir cl&#225;usulas Finally vulnerables en un bloque Try externo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|Identificador de comprobación|CA2124|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No|  
  
## Motivo  
 En las versiones 1.0 y 1.1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], un método público o protegido contiene un bloque `try`\/`catch`\/`finally`.  El bloque `finally` restablece el estado de seguridad y no se agrega a un bloque `finally`.  
  
## Descripción de la regla  
 Esta regla busca bloques `try`\/`finally` en el código diseñados para las versiones 1.0 y 1.1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que podrían ser vulnerables a los filtros de excepciones malintencionados presentes en la pila de llamadas.  Si las operaciones reservadas como la suplantación aparecen en bloques try, y se produce una excepción, el filtro puede ejecutarse antes que el bloque `finally`.  Para obtener un ejemplo de suplantación, esto significa que el filtro se ejecutaría como un usuario suplantado.  Los filtros actualmente sólo pueden implementarse en Visual Basic.  
  
> [!WARNING]
>  **Nota** En versiones 2.0 y posteriores de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], el runtime protege automáticamente un bloque `try`\/`catch`\/ `finally` de los filtros de excepciones malintencionados, si el reinicio se produce directamente dentro del método que contiene el bloque de excepción.  
  
## Cómo corregir infracciones  
 Coloque el bloque `try`\/`finally` liberado en un bloque try externo.  Vea el ejemplo que sigue.  Esto obliga al bloque `finally` a ejecutarse antes que el código del filtro.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo de seudocódigo  
  
### Descripción  
 El pseudocódigo siguiente muestra el modelo detectado por esta regla.  
  
### Código  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## Ejemplo  
 El pseudocódigo siguiente muestra el modelo que puede utilizarse para proteger el código y cumplir esta regla.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```