---
title: 'CA1058: Los tipos no deben ampliar ciertos tipos base'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d88f08746035792913601b280a0794a9ff50bf2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62795767"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Los tipos no deben ampliar ciertos tipos base

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|Identificador de comprobación|CA1058|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Extiende un tipo uno de los siguientes tipos base:

- <xref:System.ApplicationException?displayProperty=fullName>
- <xref:System.Xml.XmlDocument?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.Queue?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
- <xref:System.Collections.SortedList?displayProperty=fullName>
- <xref:System.Collections.Stack?displayProperty=fullName>

De forma predeterminada, esta regla busca solo en tipos visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Para .NET Framework versión 1, se recomienda derivar nuevas excepciones de <xref:System.ApplicationException>. La recomendación ha cambiado y deben derivar nuevas excepciones <xref:System.Exception?displayProperty=fullName> o uno de sus subclases en el <xref:System> espacio de nombres.

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima una advertencia de esta regla para las infracciones sobre <xref:System.ApplicationException>. Es seguro suprimir una advertencia de esta regla para las infracciones sobre <xref:System.Xml.XmlDocument>. Es seguro suprimir una advertencia sobre una colección no genérica si previamente se liberó el código.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```
dotnet_code_quality.ca1058.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).