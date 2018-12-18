---
title: 'CA1058: Los tipos no deben ampliar ciertos tipos base | Microsoft Docs'
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
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a4ffbe3b359f2c58f8e301b9176981a2037c17f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912440"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|Identificador de comprobación|CA1058|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente extiende algunos tipos base. Actualmente, esta regla notifica los tipos que derivan de los siguientes tipos:

-   <xref:System.ApplicationException?displayProperty=fullName>

-   <xref:System.Xml.XmlDocument?displayProperty=fullName>

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.Queue?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

-   <xref:System.Collections.SortedList?displayProperty=fullName>

-   <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Descripción de la regla
 Para [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versión 1, se recomienda derivar nuevas excepciones de <xref:System.ApplicationException>. La recomendación ha cambiado y deben derivar nuevas excepciones <xref:System.Exception?displayProperty=fullName> o uno de sus subclases en el <xref:System> espacio de nombres.

 No cree una subclase de <xref:System.Xml.XmlDocument> si desea crear una vista XML de un origen de datos o modelo de objeto subyacente.

### <a name="non-generic-collections"></a>Colecciones no genéricas
 Usar o ampliar las colecciones genéricas, siempre que sea posible. No se extienden colecciones no genéricas en el código, a menos que envió previamente.

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
 No suprima una advertencia de esta regla para las infracciones sobre <xref:System.ApplicationException>. Es seguro suprimir una advertencia de esta regla para las infracciones sobre <xref:System.Xml.XmlDocument>. Es seguro suprimir una advertencia sobre una colección no genérica si previamente se liberó el código.



