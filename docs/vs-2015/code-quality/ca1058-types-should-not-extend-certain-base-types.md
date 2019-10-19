---
title: 'CA1058: los tipos no deben extender determinados tipos base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9a4663fe3bc09b27bad9eeec05e325f07a3de6f3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603066"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|Identificador de comprobación|CA1058|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente extiende algunos tipos base. Actualmente, esta regla notifica los tipos que se derivan de los siguientes tipos:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 En [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versión 1, se recomienda derivar nuevas excepciones de <xref:System.ApplicationException>. La recomendación ha cambiado y las nuevas excepciones deben derivarse de <xref:System.Exception?displayProperty=fullName> o de una de sus subclases en el espacio de nombres <xref:System>.

 No cree una subclase de <xref:System.Xml.XmlDocument> si desea crear una vista XML de un modelo de objetos o un origen de datos subyacente.

### <a name="non-generic-collections"></a>Colecciones no genéricas
 Use y/o extienda colecciones genéricas siempre que sea posible. No extienda colecciones no genéricas en el código, a menos que la haya enviado anteriormente.

 **Ejemplos de uso incorrecto**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Ejemplos de uso correcto**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, derive el tipo de un tipo base diferente o una colección genérica.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla para infracciones sobre <xref:System.ApplicationException>. Es seguro suprimir una advertencia de esta regla para las infracciones de <xref:System.Xml.XmlDocument>. Es seguro suprimir una advertencia sobre una colección no genérica si el código se liberó previamente.
