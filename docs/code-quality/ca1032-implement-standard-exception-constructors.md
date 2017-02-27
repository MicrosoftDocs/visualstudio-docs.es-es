---
title: "CA1032: Implementar constructores de excepci&#243;n est&#225;ndar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1032: Implementar constructores de excepci&#243;n est&#225;ndar
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|Identificador de comprobación|CA1032|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo extiende <xref:System.Exception?displayProperty=fullName> y no declara todos los constructores necesarios.  
  
## Descripción de la regla  
 Los tipos de excepción deben implementar los constructores siguientes:  
  
-   public NewException\(\)  
  
-   public NewException\(string\)  
  
-   public NewException\(string, Exception\)  
  
-   protected o private NewException\(SerializationInfo, StreamingContext\)  
  
 El error al proporcionar el conjunto completo de constructores puede dificultar el control correcto de las excepciones.  Por ejemplo, el constructor que tiene la firma `NewException(string, Exception)` se utiliza para crear excepciones producidas por otras excepciones.  Sin este constructor no se puede crear ni producir una instancia de la excepción personalizada que contenga una excepción interna \(anidada\), que es lo que el código administrado debe hacer en esta situación.  Los primeros tres constructores de excepción son públicos por convención.  El cuarto constructor está protegido en clases no selladas y es privado en clases selladas.  Para obtener más información, vea [CA2229: Implementar constructores de serialización](../code-quality/ca2229-implement-serialization-constructors.md)  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue los constructores que faltan a la excepción y asegúrese de que tienen la accesibilidad correcta.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si la infracción se ha provocado usando un nivel de acceso diferente al de los constructores públicos.  
  
## Ejemplo  
 El ejemplo siguiente contiene un tipo de excepción que infringe esta regla y otro que se implementa correctamente.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]