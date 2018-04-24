---
title: 'CA1711: Los identificadores no deberían tener el sufijo incorrecto'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13160a8056c8fb4ec824d84c132fe87a7b565f27
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Los identificadores no deberían tener el sufijo incorrecto
|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|Identificador de comprobación|CA1711|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un identificador tiene un sufijo incorrecto.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, los nombres de tipos que extienden determinados tipos base o que implementan algunas interfaces, o tipos derivados de estos tipos, deben terminar con unos sufijos reservados específicos. Otros nombres de tipo no deben utilizar estos sufijos reservados.

 En la tabla siguiente se muestran los sufijos reservados y los tipos base e interfaces a los que se asocian.

|Sufijo|Tipo base/Interfaz|
|------------|--------------------------|
|Atributo|<xref:System.Attribute?displayProperty=fullName>|
|Colección|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Delegado del controlador de eventos.|
|Excepción|<xref:System.Exception?displayProperty=fullName>|
|Permiso|<xref:System.Security.IPermission?displayProperty=fullName>|
|Cola|<xref:System.Collections.Queue?displayProperty=fullName>|
|Pila|<xref:System.Collections.Stack?displayProperty=fullName>|
|Secuencia|<xref:System.IO.Stream?displayProperty=fullName>|

 Además, los siguientes sufijos deben **no** usarse:

-   delegado

-   Enum

-   Impl: use 'Core' en su lugar.

-   Ex o un sufijo similar para distinguir de una versión anterior del mismo tipo

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Quite el sufijo del nombre de tipo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que el sufijo no tenga un significado ambiguo en el dominio de aplicación.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Vea también
 [Atributos](/dotnet/standard/design-guidelines/attributes) [control y provocar eventos](/dotnet/standard/events/index)