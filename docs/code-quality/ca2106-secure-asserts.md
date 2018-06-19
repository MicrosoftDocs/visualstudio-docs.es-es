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
ms.openlocfilehash: 5863f4d8ca4db47f7e537f0b1abc5eb280434c80
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916804"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Asegurar aserciones
|||
|-|-|
|TypeName|SecureAsserts|
|Identificador de comprobación|CA2106|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.

## <a name="rule-description"></a>Descripción de la regla
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código. Un recorrido de pila de seguridad se detiene cuando se impone un permiso de seguridad. Si valida un permiso sin realizar ninguna comprobación en el llamador, el autor de la llamada podría ejecutar código indirectamente mediante el uso de sus permisos. Las aserciones sin comprobaciones de seguridad están permitidas sólo cuando esté seguro de que la aserción no se puede usar de manera perjudicial. Una aserción es inofensiva si el código que se llama es inocuo o los usuarios no pueden pasar información arbitraria al código que llama.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue una demanda de seguridad para el método o su tipo declarativo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad.

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)