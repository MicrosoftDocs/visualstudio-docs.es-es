---
title: "CA1019: Definir descriptores de acceso para los argumentos de atributo | Microsoft Docs"
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
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
helpviewer_keywords: 
  - "CA1019"
  - "DefineAccessorsForAttributeArguments"
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1019: Definir descriptores de acceso para los argumentos de atributo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefineAccessorsForAttributeArguments|  
|Identificador de comprobación|CA1019|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 En el constructor, un atributo define argumentos que no tienen las propiedades correspondientes.  
  
## Descripción de la regla  
 Los atributos pueden definir argumentos obligatorios que deben especificarse al aplicar el atributo a un destino.  Éstos también se denominan argumentos posicionales porque se proporcionan para atribuir constructores como parámetros posicionales.  Para cada argumento obligatorio, el atributo debe proporcionar también una propiedad de sólo lectura correspondiente de modo que el valor del argumento se pueda recuperar en tiempo de ejecución.  Esta regla comprueba que para cada parámetro de constructor se haya definido la propiedad correspondiente.  
  
 Los atributos también pueden definir argumentos opcionales, que también se denominan argumentos con nombre.  Estos argumentos se proporcionan para atribuir constructores por nombre y deben tener una propiedad de lectura\/escritura correspondiente.  
  
 Para los argumentos obligatorios y opcionales, las propiedades correspondientes y los parámetros de constructor deben utilizar el mismo nombre pero diferente grafía con mayúsculas y minúsculas.  Propiedades utilizan el método Pascal de mayúsculas y minúsculas y los parámetros utilizan la convención Camel escribiendo la primera letra de cada palabra en mayúscula.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue una propiedad de sólo lectura para cada parámetro de constructor que no tenga uno.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si no desea que el valor del argumento obligatorio sea recuperable.  
  
## Ejemplo de atributos personalizados  
  
### Descripción  
 El ejemplo siguiente muestra dos atributos que definen un parámetro obligatorio \(posicional\).  Se ha definido incorrectamente la primera implementación del atributo.  La segunda implementación es correcta.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]  
  
## Argumentos posicionales y con nombre  
  
### Descripción  
 Los argumentos posicionales y con nombre aclaran a los usuarios de la biblioteca qué argumentos son obligatorios para el atributo y cuáles son opcionales.  
  
 En el ejemplo siguiente se muestra la implementación de un atributo que tiene tanto argumentos posicionales como con nombre.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]  
  
### Comentarios  
 En el ejemplo siguiente se muestra cómo aplicar el atributo personalizado a dos propiedades.  
  
### Código  
 [!code-cs[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]  
  
## Reglas relacionadas  
 [CA1813: Evitar atributos no sellados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Vea también  
 [Atributos](../Topic/Attributes1.md)