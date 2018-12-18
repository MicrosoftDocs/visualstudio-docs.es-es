---
title: 'CA1710: Los identificadores deberían tener el sufijo correcto | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2256e3f20dfdb4ddb8efa28d7ecdd203a139bcc5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940169"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Los identificadores deberían tener el sufijo correcto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|Identificador de comprobación|CA1710|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un identificador no tiene el sufijo correcto.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, los nombres de tipos que extienden determinados tipos bases o que implementan algunas interfaces, o tipos derivados de estos tipos, tienen un sufijo que está asociado con el tipo base o interfaz.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

 En la tabla siguiente se enumera los tipos bases e interfaces que tienen asociados los sufijos.

|Tipo base/Interfaz|Sufijo|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Excepción|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Colección|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Colección|
|<xref:System.Collections.Queue?displayProperty=fullName>|Colección o una cola|
|<xref:System.Collections.Stack?displayProperty=fullName>|Colección o pila|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Colección|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Colección o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Secuencia|
|<xref:System.Security.IPermission?displayProperty=fullName>|Permiso|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condición|
|Un delegado de controlador de eventos.|EventHandler|

 Los tipos que implementan <xref:System.Collections.ICollection> y son un tipo de estructura de datos generalizado, como un diccionario, una pila o una cola, se permiten los nombres que proporcionan información significativa sobre el uso previsto del tipo.

 Los tipos que implementan <xref:System.Collections.ICollection> y son una colección de elementos específicos tienen nombres que terminan con la palabra 'Collection'. Por ejemplo, una colección de <xref:System.Collections.Queue> objetos tendría el nombre "QueueCollection". El sufijo 'Collection' significa que se pueden enumerar los miembros de la colección utilizando el `foreach` (`For Each` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) instrucción.

 Los tipos que implementan <xref:System.Collections.IDictionary> tienen nombres que terminan con la palabra "Diccionario", incluso si el tipo también implementa <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>. Las convenciones de nomenclatura de sufijo 'Collection' y 'Diccionario' permiten que los usuarios distinguir entre los siguientes dos modelos de enumeración.

 Tipos con el sufijo 'Collection' siguen este patrón de enumeración.

```
foreach(SomeType x in SomeCollection) { }
```

 Los tipos con el sufijo "Diccionario de" siguen este patrón de enumeración.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Un <xref:System.Data.DataSet> objeto consta de una colección de <xref:System.Data.DataTable> objetos, que consisten en colecciones de <xref:System.Data.DataColumn?displayProperty=fullName> y <xref:System.Data.DataRow?displayProperty=fullName> objetos, entre otros. Estas colecciones implementan <xref:System.Collections.ICollection> a través de la base de <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> clase.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre del tipo tiene el sufijo con el término correcto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia al utilizar el sufijo 'Collection' Si el tipo es una estructura de datos generalizada que podría extenderse o que va a contener un conjunto arbitrario de elementos diversos. En este caso, un nombre que proporcione información significativa sobre la implementación, rendimiento u otras características de la estructura de datos podría tener sentido (por ejemplo, BinaryTree). En casos donde el tipo representa una colección de un tipo específico (por ejemplo, StringCollection), no suprima una advertencia de esta regla porque el sufijo indica que el tipo se puede enumerar mediante el uso de un `foreach` instrucción.

 Para otros sufijos, no suprima una advertencia de esta regla. El sufijo permite el uso previsto sea evidente desde el nombre de tipo.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Vea también
 [Atributos](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: delegados y eventos](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



