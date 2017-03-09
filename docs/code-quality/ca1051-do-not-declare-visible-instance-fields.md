---
title: "CA1051: No declarar campos de instancia visibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: No declarar campos de instancia visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|Identificador de comprobación|CA1051|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo visible externamente tiene un campo de instancia visible externamente.  
  
## Descripción de la regla  
 El uso principal de un campo debe ser como un detalle de implementación.  Los campos debe ser `private` o `internal` y deberían exponerse utilizando las propiedades.  Es tan fácil tener acceso a una propiedad como tener acceso a un campo, y el código de los descriptores de acceso de una propiedad puede cambiar conforme se expanden las características del tipo sin introducir cambios importantes.  Las propiedades que solo devuelven el valor de un campo privado o interno están optimizadas para desempeñarse en conjunto con el campo al que obtienen acceso; y el rendimiento mejora muy poco con el uso de campos visibles externamente en lugar de con propiedades.  
  
 Si es visible externamente hace referencia a `public`, `protected` y a los niveles de accesibilidad `protected internal` \(`Public`, `Protected` y `Protected Friend` en Visual Basic\).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el campo como `private` o `internal` y expóngalo utilizando una propiedad visible externamente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  Los campos externamente visibles no proporcionan ningún beneficio que no esté disponible para las propiedades.  Además, [Link Demands](../Topic/Link%20Demands.md) no puede proteger los campos públicos.  Vea [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra un tipo \(`BadPublicInstanceFields`\) que infringe esta regla.  `GoodPublicInstanceFields` muestra el código corregido.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Reglas relacionadas  
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## Vea también  
 [Link Demands](../Topic/Link%20Demands.md)