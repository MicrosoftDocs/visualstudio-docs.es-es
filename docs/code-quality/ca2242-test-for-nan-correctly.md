---
title: "CA2242: Prueba para NaN correcta | Microsoft Docs"
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
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2242: Prueba para NaN correcta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|Identificador de comprobación|CA2242|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Una expresión prueba un valor con <xref:System.Single.Nan?displayProperty=fullName> o <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.Double.NaN?displayProperty=fullName>, que representa un valor no numérico, se obtiene cuando una operación aritmética no está definida.  Cualquier expresión que pruebe la igualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `false`.  Cualquier expresión que pruebe la desigualdad entre un valor y <xref:System.Double.NaN?displayProperty=fullName> siempre devuelve `true`.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla y determinar con precisión si un valor representa <xref:System.Double.NaN?displayProperty=fullName>, utilice <xref:System.Single.IsNan%2A?displayProperty=fullName> o <xref:System.Double.IsNan%2A?displayProperty=fullName> para probar el valor.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente se muestran dos expresiones que prueban incorrectamente un valor con <xref:System.Double.NaN?displayProperty=fullName> y una expresión que utiliza correctamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para probar el valor.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]