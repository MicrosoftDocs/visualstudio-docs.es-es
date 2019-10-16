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
ms.openlocfilehash: e157feb9b054cd6082f77c4f86277c35ddb02c34
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349134"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|Identificador de comprobación|CA1031|
|Categoría|Microsoft. Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se detecta en una instrucción @no__t 2, o bien se utiliza una cláusula catch general como `catch()`.

## <a name="rule-description"></a>Descripción de la regla
No se deben capturar excepciones generales.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, detecte una excepción más específica o vuelva a producir la excepción general como última instrucción del bloque `catch`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. La detección de tipos de excepción generales puede ocultar problemas en tiempo de ejecución del usuario de la biblioteca y puede dificultar la depuración.

> [!NOTE]
> A partir de la .NET Framework 4, el Common Language Runtime (CLR) ya no proporciona excepciones de estado dañadas que se producen en el sistema operativo y el código administrado, como infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], para que los controle el código administrado. Si desea compilar una aplicación en el .NET Framework 4 o versiones posteriores y mantener el control de las excepciones de estado dañadas, puede aplicar el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> al método que controla la excepción de estado dañado.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe esta regla y un tipo que implementa correctamente el bloque `catch`.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200.md)