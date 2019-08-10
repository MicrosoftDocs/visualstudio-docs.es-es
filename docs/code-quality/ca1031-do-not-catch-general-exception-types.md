---
title: 'CA1031: No capturar los tipos de excepción general'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7b1610d07e5e38632056df237d284b40b6f101c6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922905"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|Identificador de comprobación|CA1031|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Una excepción general <xref:System.Exception?displayProperty=fullName> como o <xref:System.SystemException?displayProperty=fullName> se detecta en una `catch` instrucción `catch()` , o se utiliza una cláusula catch general como.

## <a name="rule-description"></a>Descripción de la regla
No se deben capturar excepciones generales.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, detecte una excepción más específica o vuelva a producir la excepción general como última instrucción `catch` del bloque.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. La detección de tipos de excepción generales puede ocultar problemas en tiempo de ejecución del usuario de la biblioteca y puede dificultar la depuración.

> [!NOTE]
> A partir de la .NET Framework 4, el Common Language Runtime (CLR) ya no proporciona excepciones de estado dañadas que se producen en el sistema operativo y el código administrado, como [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]infracciones de acceso en, para que los controle el código administrado. Si desea compilar una aplicación en el .NET Framework 4 o versiones posteriores y mantener el control de las excepciones de estado dañadas, puede <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> aplicar el atributo al método que controla la excepción de estado dañado.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla y un tipo que implementa correctamente el `catch` bloque.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2200: Volver a iniciar para conservar los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)