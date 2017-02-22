---
title: "CA1722: Los identificadores no deber&#237;an tener el prefijo incorrecto | Microsoft Docs"
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
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1722: Los identificadores no deber&#237;an tener el prefijo incorrecto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|Identificador de comprobación|CA1722|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un identificador tiene un prefijo incorrecto.  
  
## Descripción de la regla  
 Por convención, sólo ciertos elementos de programación tienen nombres que comienzan con un prefijo concreto.  
  
 Los nombres de tipo no tienen un prefijo concreto y no se deben prefijar con una 'C'.  Esta regla crea un informe sobre las infracciones para los nombres de tipo como 'CMyClass' y no crea un informe sobre las infracciones para los nombres de tipo como 'Cache'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Quite el prefijo del identificador.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Reglas relacionadas  
 [CA1715: Los identificadores deberían tener el prefijo correcto](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)