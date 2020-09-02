---
title: Análisis de código para advertencias de código administrado | Microsoft Docs
ms.date: 08/31/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: mikadumont
ms.author: midumont
manager: wpickett
ms.openlocfilehash: e689d137e071096d096e117ef3b79df405a060ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285754"
---
# <a name="net-code-analysis-rules"></a>Reglas de análisis de código de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta de análisis de código administrado proporciona advertencias que indican las infracciones de las reglas de bibliotecas de código administrado. Las advertencias se organizan en áreas de reglas como diseño, localización, rendimiento y seguridad. Cada advertencia implica una infracción de una regla de análisis de código administrado. En esta sección se proporcionan información detallada y ejemplos de cada advertencia de análisis de código administrado.

 En la tabla siguiente se muestra el tipo de información que se proporciona para cada advertencia.

|Elemento|Descripción|
|----------|-----------------|
|Tipo|TypeName de la regla.|
|Identificador de comprobación|Identificador único de la regla. CheckId y Categoría se usan para la supresión en el código fuente de una advertencia.|
|Category|Categoría de la advertencia.|
|Cambio problemático|Indica si la corrección para una infracción de la regla es un cambio problemático. Se entiende por cambio problemático que un ensamblado que tenga una dependencia en el destino que produjo la infracción no se vuelva a compilar con la nueva versión modificada o genere un error en tiempo de ejecución debido al cambio. Cuando hay disponibles varias correcciones y al menos una es un cambio problemático y otra no, se especifican "Problemático" y "No problemático".|
|Causa|El código administrado específico que provoca que la regla genere una advertencia.|
|Descripción|Describe los problemas que están detrás de la advertencia.|
|Cómo corregir infracciones|Explica cómo cambiar el código fuente para cumplir la regla y evitar que se genere una advertencia.|
|Cuándo suprimir advertencias|Describe cuándo es seguro suprimir una advertencia de la regla.|
|Código de ejemplo|Ejemplos que infringen la regla y ejemplos corregidos que cumplen la regla.|
|Advertencias relacionadas|Advertencias relacionadas.|

## <a name="in-this-section"></a>En esta sección

|Elemento|Value|
|-|-|
|[ADVERTENCIAS por CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Lista de advertencias por CheckId|
|[Advertencias de criptografía](../code-quality/cryptography-warnings.md)|Advertencias compatibles con bibliotecas y aplicaciones más seguras mediante el uso correcto de criptografía.|
|[Advertencias de diseño](../code-quality/design-warnings.md)|Advertencias compatibles con el diseño correcto de la biblioteca según lo especificado en las directrices de diseño de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Advertencias de globalización](../code-quality/globalization-warnings.md)|Advertencias compatibles con las aplicaciones y bibliotecas de uso internacional.|
|[Advertencias de interoperabilidad](../code-quality/interoperability-warnings.md)|Advertencias compatibles con la interacción con clientes COM.|
|[Advertencias de mantenimiento](../code-quality/maintainability-warnings.md)|Advertencias compatibles con el mantenimiento de bibliotecas y aplicaciones.|
|[Advertencias de movilidad](../code-quality/mobility-warnings.md)|Advertencias compatibles con el uso eficiente de energía.|
|[Advertencias de nomenclatura](../code-quality/naming-warnings.md)|Advertencias compatibles con el cumplimiento de las convenciones de nomenclatura de la directrices de diseño de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Advertencias de rendimiento](../code-quality/performance-warnings.md)|Advertencias compatibles con las aplicaciones y bibliotecas de alto rendimiento.|
|[Advertencias de portabilidad](../code-quality/portability-warnings.md)|Advertencias compatibles con la portabilidad en diferentes plataformas.|
|[Advertencias de confiabilidad](../code-quality/reliability-warnings.md)|Advertencias compatibles con la confiabilidad de bibliotecas y aplicaciones, como el uso correcto de memorias y subprocesos.|
|[Advertencias de seguridad](../code-quality/security-warnings.md)|Advertencias compatibles con bibliotecas y aplicaciones más seguras.|
|[Advertencias de uso](../code-quality/usage-warnings.md)|Advertencias compatibles con el uso adecuado de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Errores que se producen si la directiva de análisis de código no se cumple en el momento de la inserción en el repositorio.|
