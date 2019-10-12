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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163069"
---
# <a name="portability-warnings"></a>advertencias de portabilidad
Las advertencias de portabilidad admiten la portabilidad en diferentes sistemas operativos.

## <a name="in-this-section"></a>En esta sección

|Regla|Descripción|
|----------|-----------------|
|[CA1900: Los campos de tipo de valor deben ser portátiles @ no__t-0|Esta regla comprueba que las estructuras que se declaran mediante un atributo de diseño explícito se alinearán correctamente cuando se calculen las referencias a código no administrado en sistemas operativos de 64 bits.|
|[CA1901: Las declaraciones P/Invoke deben ser portables @ no__t-0|Esta regla evalúa el tamaño de cada parámetro y el valor devuelto de P/Invoke, y comprueba que su tamaño es correcto cuando se calculan las referencias a código no administrado en sistemas operativos de 32 y 64 bits.|
|[CA1903: Usar solo la API del marco de destino @ no__t-0|Un miembro o tipo utiliza un miembro o tipo que se introdujo en un Service Pack no incluido junto con la versión de .NET Framework de destino del proyecto.|
