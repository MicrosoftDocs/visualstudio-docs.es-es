---
title: 'CA2106: Asegurar aserciones'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5ff16cdce4be04bd076c93763fb6a22d2721675f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551787"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asegurar aserciones

|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método valida un permiso y no realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el llamador, el llamador podría ejecutar código indirectamente mediante el uso de sus permisos. Aserciones sin comprobaciones de seguridad están permitidas si está seguro de que la aserción no se puede usar de manera perjudicial. Una aserción es inofensiva, si el código que se llama es inocuo, o si los usuarios no pueden pasar información arbitraria al código que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregar una petición de seguridad para el método o su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Suprima una advertencia de esta regla solo después de revisar cuidadosamente la seguridad.

## <a name="see-also"></a>Vea también

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)