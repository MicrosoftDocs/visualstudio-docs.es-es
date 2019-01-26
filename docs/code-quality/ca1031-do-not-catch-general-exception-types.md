---
title: 'CA1031: No capturar los tipos de excepción general'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2602d8eb59fe5f716139adbca664566aed6c594b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038570"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|Identificador de comprobación|CA1031|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se captura en un `catch` instrucción o una cláusula catch general como `catch()` se utiliza.

## <a name="rule-description"></a>Descripción de la regla
 No se deben capturar excepciones generales.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, detectar una excepción más específica o vuelva a producir la excepción general como la última instrucción del `catch` bloque.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Detectar tipos de excepción general se pueden ocultar problemas en tiempo de ejecución de usuario de la biblioteca y puede dificultar la depuración.

> [!NOTE]
> A partir de la [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], common language runtime (CLR) ya no entrega excepciones de estado dañado que se producen en el sistema operativo y el código administrado, como las infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], controlarse en código administrado. Si desea compilar una aplicación en el [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] o versiones posteriores y mantener el control de excepciones de estado dañado, puede aplicar el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al método que controla la excepción de estado dañado.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe esta regla y un tipo que implementa correctamente el `catch` bloque.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)