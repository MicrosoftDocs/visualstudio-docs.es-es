---
title: "CA1809: Evitar el exceso de variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1809: Evitar el exceso de variables locales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|Identificador de comprobación|CA1809|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un miembro contiene más de 64 variables locales, algunas de las cuales podrían ser generadas por el compilador.  
  
## Descripción de la regla  
 Una optimización de rendimiento común es almacenar un valor en un registro del procesador en lugar de en la memoria, lo que se denomina *registrar* el valor.  Common Language Runtime considera hasta 64 variables locales para su registro.  Las variables no registradas se colocan en la pila y deben moverse a un registro antes de su manipulación.  Para permitir que todas las variables locales se registren, limite el número de variables locales a 64.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, refactorice la implementación de modo que utilice 64 variables locales como máximo.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla o deshabilitar la regla si el rendimiento no es importante.  
  
## Reglas relacionadas  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)