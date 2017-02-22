---
title: "CA1044: Las propiedades no deben ser de solo escritura | Microsoft Docs"
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
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1044: Las propiedades no deben ser de solo escritura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|Identificador de comprobación|CA1044|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 La propiedad pública o protegida tiene un descriptor de acceso set pero no tiene un descriptor de acceso get.  
  
## Descripción de la regla  
 Los descriptores de acceso get proporcionan acceso de lectura a una propiedad y los de acceso set, de escritura.  Aunque es aceptable y a menudo necesario tener una propiedad de solo lectura, las directrices de diseño prohíben el uso de propiedades de solo escritura.  Esto es porque permitir que un usuario establezca un valor y a continuación impedir que el usuario vea el valor no proporciona ninguna seguridad.  Además, sin acceso de lectura, no se puede ver el estado de los objetos compartidos, lo que limita su utilidad.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue un descriptor de acceso get a la propiedad.  O bien, si el comportamiento de una propiedad de sólo escritura es necesario, piense en convertirla en un método.  
  
## Cuándo suprimir advertencias  
 Se recomienda que no suprima ninguna advertencia de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente, la propiedad `BadClassWithWriteOnlyProperty` se establece con la propiedad de solo escritura.  `GoodClassWithReadWriteProperty` contiene el código corregido.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]