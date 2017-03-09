---
title: "CA1018: Marcar atributos con AttributeUsageAttribute | Microsoft Docs"
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
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: Marcar atributos con AttributeUsageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|Identificador de comprobación|CA1018|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El atributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> no está presente en el atributo personalizado.  
  
## Descripción de la regla  
 Cuando define un atributo personalizado, márquelo utilizando <xref:System.AttributeUsageAttribute> para indicar donde se puede aplicar el atributo personalizado en el código fuente.  El significado de un atributo y el uso que se le va a dar determinará sus ubicaciones válidas en código.  Por ejemplo, podría definir un atributo que identifique la persona responsable de mantener y mejorar cada tipo en una biblioteca, y que esa responsabilidad siempre se asigne en el nivel de tipo.  En este caso, los compiladores deberían habilitar el atributo en las clases, enumeraciones e interfaces, pero no deberían habilitarlo en los métodos, eventos o propiedades.  Las directivas organizativas y los procedimientos dictarían si el atributo debe habilitarse en ensamblados.  
  
 La enumeración <xref:System.AttributeTargets?displayProperty=fullName> define los destinos que puede especificar para un atributo personalizado.  Si omite <xref:System.AttributeUsageAttribute>, su atributo personalizado será válido para todos los destinos, tal y como define el valor `All` de la enumeración <xref:System.AttributeTargets>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, especifique los destinos para el atributo utilizando <xref:System.AttributeUsageAttribute>.  Vea el ejemplo siguiente.  
  
## Cuándo suprimir advertencias  
 Se debe corregir una infracción de esta regla en lugar de excluir el mensaje.  Aun cuando el atributo hereda <xref:System.AttributeUsageAttribute>, el atributo debe estar presente para simplificar el mantenimiento del código.  
  
## Ejemplo  
 En el siguiente ejemplo se definen dos atributos.  `BadCodeMaintainerAttribute` omite la instrucción <xref:System.AttributeUsageAttribute> incorrectamente y `GoodCodeMaintainerAttribute` implementa correctamente el atributo que se describe anteriormente en esta sección.  Tenga en cuenta que la regla de diseño [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) requiere la propiedad `DeveloperName` y se incluye para obtener un mejor resultado.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Reglas relacionadas  
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Vea también  
 [Atributos](../Topic/Attributes1.md)