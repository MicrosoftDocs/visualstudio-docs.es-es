---
title: advertencias de portabilidad
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167578"
---
# <a name="portability-warnings"></a>advertencias de portabilidad
Las advertencias de portabilidad admiten la portabilidad en diferentes sistemas operativos.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1900: Los campos de tipo de valor deberían ser portátiles](../code-quality/ca1900.md)|Esta regla comprueba que las estructuras que se declaran mediante un atributo de diseño explícito se alinearán correctamente cuando se calculen las referencias a código no administrado en sistemas operativos de 64 bits.|
|[CA1901: Las declaraciones P/Invoke deben ser portables](../code-quality/ca1901.md)|Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke, y comprueba que su tamaño es correcto cuando se calculan las referencias a código no administrado en sistemas operativos de 32 y 64 bits.|
|[CA1903: Usar solo API de la versión de .NET Framework de destino](../code-quality/ca1903.md)|Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto.|
