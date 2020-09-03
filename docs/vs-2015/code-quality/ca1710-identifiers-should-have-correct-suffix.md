---
title: 'CA1710: los identificadores deberían tener el sufijo correcto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543993"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Los identificadores deben tener un sufijo correcto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|Identificador de comprobación|CA1710|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un identificador no tiene el sufijo correcto.

## <a name="rule-description"></a>Descripción de la regla
 Por Convención, los nombres de tipos que extienden determinados tipos base o que implementan determinadas interfaces, o tipos derivados de estos tipos, tienen un sufijo que está asociado con el tipo base o la interfaz.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

 En la tabla siguiente se enumeran los tipos base y las interfaces que tienen sufijos asociados.

|Tipo base/Interfaz|Sufijo|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Excepción|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Colección|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Diccionario|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Colección|
|<xref:System.Collections.Queue?displayProperty=fullName>|Colección o cola|
|<xref:System.Collections.Stack?displayProperty=fullName>|Colección o pila|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Colección|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Diccionario|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Colección o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Transmitir|
|<xref:System.Security.IPermission?displayProperty=fullName>|Permiso|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condición|
|Delegado de controlador de eventos.|EventHandler|

 Los tipos que implementan <xref:System.Collections.ICollection> y son un tipo generalizado de estructura de datos, como un diccionario, una pila o una cola, son nombres permitidos que proporcionan información significativa sobre el uso previsto del tipo.

 Los tipos que implementan <xref:System.Collections.ICollection> y son una colección de elementos específicos tienen nombres que terminan con la palabra ' Collection '. Por ejemplo, una colección de <xref:System.Collections.Queue> objetos tendría el nombre "QueueCollection". El sufijo ' Collection ' indica que los miembros de la colección se pueden enumerar mediante la `foreach` `For Each` instrucción (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

 Los tipos que implementan <xref:System.Collections.IDictionary> tienen nombres que terminan con la palabra ' Dictionary ' incluso si el tipo también implementa <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection> . Las convenciones de nomenclatura de los sufijos ' Collection ' y ' Dictionary ' permiten a los usuarios distinguir entre los dos patrones de enumeración siguientes.

 Los tipos con el sufijo ' Collection ' siguen este patrón de enumeración.

```
foreach(SomeType x in SomeCollection) { }
```

 Los tipos con el sufijo ' Dictionary ' siguen este patrón de enumeración.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Un <xref:System.Data.DataSet> objeto consta de una colección de <xref:System.Data.DataTable> objetos, que se componen de colecciones de <xref:System.Data.DataColumn?displayProperty=fullName> <xref:System.Data.DataRow?displayProperty=fullName> objetos y, entre otros. Estas colecciones se implementan <xref:System.Collections.ICollection> a través de la <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> clase base.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre del tipo para que tenga como sufijo el término correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia para usar el sufijo ' Collection ' si el tipo es una estructura de datos generalizada que podría extenderse o que contendrá un conjunto arbitrario de diversos elementos. En este caso, un nombre que proporcione información significativa sobre la implementación, el rendimiento u otras características de la estructura de datos podría tener sentido (por ejemplo, BinaryTree). En los casos en los que el tipo representa una colección de un tipo específico (por ejemplo, StringCollection), no suprima una advertencia de esta regla porque el sufijo indica que el tipo se puede enumerar mediante una `foreach` instrucción.

 En el caso de otros sufijos, no suprima una advertencia de esta regla. El sufijo permite que el uso previsto sea evidente a partir del nombre de tipo.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1711: Los identificadores no deben tener un sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Consulte también
 [Attributes](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: eventos y delegados](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
