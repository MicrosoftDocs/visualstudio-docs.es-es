---
title: 'CA2106: Proteger las aserciones'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df19d31abe88c6d12bafc933ba740badb832eb16
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921071"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Proteger las aserciones

|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un método valida un permiso y no realiza ninguna comprobación de seguridad en el autor de la llamada.

## <a name="rule-description"></a>Descripción de la regla
Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el autor de la llamada, el llamador podría ejecutar el código indirectamente mediante sus permisos. Se permiten aserciones sin comprobaciones de seguridad si está seguro de que la aserción no se puede usar de forma dañina. Una aserción es inofensiva si el código al que se llama es inofensivo o si los usuarios no pueden pasar información arbitraria al código al que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue una solicitud de seguridad al método o a su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad.

## <a name="see-also"></a>Vea también

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)