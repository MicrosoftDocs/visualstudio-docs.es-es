---
title: "CA1823: Evitar los campos privados no utilizados | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823: Evitar los campos privados no utilizados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|Identificador de comprobación|CA1823|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Se crea un informe de esta regla cuando existe un campo privado en su código pero no lo utiliza ninguna ruta de acceso de código.  
  
## Descripción de la regla  
 Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el campo o agregue el código que lo utiliza.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  
  
## Reglas relacionadas  
 [CA1812: Evitar las clases internas sin instancia](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)