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
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545397"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|Identificador de comprobación|CA1058|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
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
 En el caso de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versión 1, se recomienda derivar nuevas excepciones de <xref:System.ApplicationException> . La recomendación ha cambiado y las nuevas excepciones deben derivarse de <xref:System.Exception?displayProperty=fullName> o de una de sus subclases en el <xref:System> espacio de nombres.

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
 No suprima una advertencia de esta regla para infracciones sobre <xref:System.ApplicationException> . Es seguro suprimir una advertencia de esta regla para infracciones sobre <xref:System.Xml.XmlDocument> . Es seguro suprimir una advertencia sobre una colección no genérica si el código se liberó previamente.
