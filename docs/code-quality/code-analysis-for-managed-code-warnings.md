---
title: Análisis de código de las advertencias de código administrado
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8238de0760f300b6fa418a5e3eb47eac3db77272
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509021"
---
# <a name="net-code-analysis-rules"></a>Reglas de análisis de código de .NET
La herramienta de análisis de código administrado proporciona advertencias que indican las infracciones de las reglas de bibliotecas de código administrado. Las advertencias se organizan en áreas de reglas como diseño, localización, rendimiento y seguridad. Cada advertencia implica una infracción de una regla de análisis de código administrado. En esta sección se proporcionan información detallada y ejemplos de cada advertencia de análisis de código administrado.

 En la tabla siguiente se muestra el tipo de información que se proporciona para cada advertencia.

|Elemento|Descripción|
|----------|-----------------|
|Tipo|TypeName de la regla.|
|Identificador de comprobación|Identificador único de la regla. CheckId y Categoría se usan para la supresión en el código fuente de una advertencia.|
|Category|Categoría de la advertencia.|
|Cambio importante|Indica si la corrección para una infracción de la regla es un cambio problemático. Se entiende por cambio problemático que un ensamblado que tenga una dependencia en el destino que produjo la infracción no se vuelva a compilar con la nueva versión modificada o genere un error en tiempo de ejecución debido al cambio. Cuando hay disponibles varias correcciones y al menos una corrección es un cambio importante y no hay una solución, se especifican "Breaking" y "non-breaking".|
|Causa|El código administrado específico que provoca que la regla genere una advertencia.|
|Descripción|Describe los problemas que están detrás de la advertencia.|
|Cómo corregir infracciones|Explica cómo cambiar el código fuente para cumplir la regla y evitar que se genere una advertencia.|
|Cuándo suprimir advertencias|Describe cuándo es seguro suprimir una advertencia de la regla.|
|Código de ejemplo|Ejemplos que infringen la regla y ejemplos corregidos que cumplen la regla.|
|Advertencias relacionadas|Advertencias relacionadas.|

## <a name="in-this-section"></a>En esta sección

|Category|Descripción|
|-|-|
|[Reglas por identificador](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Muestra todas las reglas por el|
|[Diseñar reglas](../code-quality/design-warnings.md)|Reglas que admiten el diseño correcto de la biblioteca como se especifica en las instrucciones de diseño de .NET.|
|[Reglas de documentación](../code-quality/documentation-warnings.md)|Reglas que admiten el diseño de biblioteca bien documentado a través del uso correcto de los comentarios de documentación XML.|
|[Reglas de globalización](../code-quality/globalization-warnings.md)|Reglas que admiten aplicaciones y bibliotecas de uso internacional.|
|[Reglas de mantenimiento](../code-quality/maintainability-warnings.md)|Reglas que admiten el mantenimiento de bibliotecas y aplicaciones.|
|[Reglas de nomenclatura](../code-quality/naming-warnings.md)|Reglas que admiten el cumplimiento de las convenciones de nomenclatura de las instrucciones de diseño de .NET.|
|[Reglas de rendimiento](../code-quality/performance-warnings.md)|Reglas que admiten aplicaciones y bibliotecas de alto rendimiento.|
|[Reglas de portabilidad y de interoperabilidad](../code-quality/interoperability-warnings.md)|Reglas que admiten la portabilidad en diferentes plataformas e interacción con clientes COM.|
|[Publicar reglas](../code-quality/publish-warnings.md)|Reglas que admiten la publicación adecuada de aplicaciones .NET.|
|[Reglas de confiabilidad](../code-quality/reliability-warnings.md)|Reglas que admiten la confiabilidad de bibliotecas y aplicaciones, como la corrección del uso de la memoria y el subproceso.|
|[Reglas de seguridad](../code-quality/security-warnings.md)|Reglas que admiten bibliotecas y aplicaciones más seguras.|
|[Reglas de uso](../code-quality/usage-warnings.md)|Reglas que admiten el uso adecuado de .NET.|
