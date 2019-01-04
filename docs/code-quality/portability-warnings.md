---
title: advertencias de portabilidad
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f181411d8379c8583057419c2a31f6b27c9d884
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882460"
---
# <a name="portability-warnings"></a>advertencias de portabilidad
Advertencias de portabilidad compatibles con la portabilidad entre diferentes sistemas operativos.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1900: Campos de tipo de valor deberían ser portátiles](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Esta regla comprueba que las estructuras declaradas mediante un atributo de diseño explícito se alinearán correctamente cuando se calculan las referencias a código no administrado en sistemas operativos de 64 bits.|
|[CA1901: Las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Esta regla se evalúa como el tamaño de cada parámetro y el valor devuelto de P/Invoke y comprueba que su tamaño sea correcto al calcular las referencias a código no administrado en sistemas operativos de 32 bits y 64 bits.|
|[CA1903: Usar solo API de .NET framework de destino](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto.|