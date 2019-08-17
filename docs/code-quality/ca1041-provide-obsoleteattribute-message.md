---
title: 'CA1041: Proporcionar un mensaje ObsoleteAttribute'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a0545503b80e2f256593012e06cdf7ccd8b3b5b1
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547629"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|Identificador de comprobación|CA1041|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa

Un tipo o miembro se marca con un <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que no tiene la <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propiedad especificada.

De forma predeterminada, esta regla solo examina los tipos y miembros visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

<xref:System.ObsoleteAttribute>se utiliza para marcar los tipos y miembros de biblioteca en desuso. Los consumidores de la biblioteca deben evitar el uso de cualquier tipo o miembro que esté marcado como obsoleto. Esto se debe a que es posible que no se admita y finalmente se quitará de las versiones posteriores de la biblioteca. Cuando <xref:System.ObsoleteAttribute> se compila un tipo o un miembro marcado mediante, se <xref:System.ObsoleteAttribute.Message%2A> muestra la propiedad del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Generalmente, esta información incluye el tiempo que los diseñadores de biblioteca y el reemplazo preferido usarán el tipo o miembro obsoleto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, agregue `message` el parámetro <xref:System.ObsoleteAttribute> al constructor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima una advertencia de esta regla porque la <xref:System.ObsoleteAttribute.Message%2A> propiedad proporciona información crítica sobre el tipo o miembro obsoleto.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1041.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un miembro obsoleto que tiene un <xref:System.ObsoleteAttribute>declarado correctamente.

[!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
[!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
[!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Vea también

- <xref:System.ObsoleteAttribute?displayProperty=fullName>