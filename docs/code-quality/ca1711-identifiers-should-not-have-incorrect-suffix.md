---
title: "CA1711: Los identificadores no deber&#237;an tener el sufijo incorrecto | Microsoft Docs"
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
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: Los identificadores no deber&#237;an tener el sufijo incorrecto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|Identificador de comprobación|CA1711|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un identificador tiene un sufijo incorrecto.  
  
## Descripción de la regla  
 Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos.  Otros nombres de tipo no deben utilizar estos sufijos reservados.  
  
 En la tabla siguiente se muestran los sufijos reservados y los tipos base e interfaces a los que se asocian.  
  
|Sufijo|Tipo base\/Interfaz|  
|------------|-------------------------|  
|Atributo|<xref:System.Attribute?displayProperty=fullName>|  
|Collection|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Delegado del controlador de eventos.|  
|Excepción|<xref:System.Exception?displayProperty=fullName>|  
|Permiso|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Cola|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Pila|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Además, **no** se deben usar los sufijos siguientes:  
  
-   Delegate  
  
-   Enum  
  
-   Impl: use 'Core' en su lugar.  
  
-   Ex o un sufijo similar para distinguir de una versión anterior del mismo tipo  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Quite el sufijo del nombre de tipo.  
  
## Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla a menos que el sufijo no tenga un significado ambiguo en el dominio de aplicación.  
  
## Reglas relacionadas  
 [CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## Vea también  
 [Atributos](../Topic/Attributes1.md)   
 [Eventos y delegados](http://msdn.microsoft.com/es-es/d98fd58b-fa4f-4598-8378-addf4355a115)