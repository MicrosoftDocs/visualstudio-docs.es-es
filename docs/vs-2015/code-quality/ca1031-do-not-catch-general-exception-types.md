---
title: 'CA1031: no se detectan los tipos de excepción general | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542407"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: No capturar los tipos de excepción general
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|Identificador de comprobación|CA1031|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Una excepción general como <xref:System.Exception?displayProperty=fullName> o <xref:System.SystemException?displayProperty=fullName> se detecta en una `catch` instrucción, o se utiliza una cláusula catch general como `catch()` .

## <a name="rule-description"></a>Descripción de la regla
 No se deben capturar excepciones generales.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, detecte una excepción más específica o vuelva a producir la excepción general como última instrucción del `catch` bloque.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. La detección de tipos de excepción generales puede ocultar problemas en tiempo de ejecución del usuario de la biblioteca y puede dificultar la depuración.

> [!NOTE]
> A partir de [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , el Common Language Runtime (CLR) ya no proporciona excepciones de estado dañadas que se producen en el sistema operativo y el código administrado, como infracciones de acceso en [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] , para que los controle el código administrado. Si desea compilar una aplicación en [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] o versiones posteriores y mantener el control de las excepciones de estado dañado, puede aplicar el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo al método que controla la excepción de estado dañado.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo que infringe esta regla y un tipo que implementa correctamente el `catch` bloque.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2200: Reiniciar para mantener los detalles de la pila](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
