---
title: 'CA1716: Los identificadores no deben coincidir con palabras clave'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47bbb39cadb6a092f71ebd7b3907f34fcc2782ce
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842048"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: Los identificadores no deben coincidir con palabras clave

|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|Identificador de comprobación|CA1716|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

El nombre de un espacio de nombres, tipo, o virtual o miembro de interfaz que coincida con una palabra clave reservada en un lenguaje de programación.

De forma predeterminada, esta regla solo se examina visible externamente espacios de nombres, tipos y miembros, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Los identificadores para los espacios de nombres, tipos y virtual y los miembros de interfaz no deberían coincidir con palabras clave definidas por los lenguajes que tienen como destino common language runtime. Según el idioma que se usa y la palabra clave, las ambigüedades y errores del compilador pueden dificultar la biblioteca usar.

Esta regla comprueba las palabras clave en los idiomas siguientes:

- Visual Basic
- C#
- C++/CLI

Comparación entre mayúsculas y minúsculas se utiliza para las palabras clave de Visual Basic, y se usa la comparación distingue mayúsculas de minúsculas para los demás idiomas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Seleccione un nombre que no aparece en la lista de palabras clave.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Puede suprimir una advertencia de esta regla si está convencido de que el identificador de no confundir a los usuarios de la API, y que la biblioteca se puede usar en todos los idiomas disponibles en. NET.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1716.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (convenciones de nomenclatura). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).