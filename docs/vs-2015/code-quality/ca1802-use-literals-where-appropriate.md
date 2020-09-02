---
title: 'CA1802: Use los literales cuando corresponda | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dc8019c97d3c561000f1c6a8d083bee6253face3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544409"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizar literales cuando sea apropiado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|Identificador de comprobación|CA1802|
|Category|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un campo se declara `static` y `readonly` ( `Shared` y `ReadOnly` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), y se inicializa con un valor que se calcula en tiempo de compilación.

## <a name="rule-description"></a>Descripción de la regla
 El valor de un `static``readonly` campo se calcula en tiempo de ejecución cuando se llama al constructor estático del tipo declarativo. Si el `static``readonly` campo se inicializa cuando se declara y no se declara explícitamente un constructor estático, el compilador emite un constructor estático para inicializar el campo.

 El valor de un `const` campo se calcula en tiempo de compilación y se almacena en los metadatos, lo que aumenta el rendimiento en tiempo de ejecución cuando se compara con un `static``readonly` campo.

 Dado que el valor asignado al campo de destino es calculable en tiempo de compilación, cambie la declaración a un `const` campo para que el valor se calcule en tiempo de compilación en lugar de en tiempo de ejecución.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace `static` los `readonly` modificadores y por el `const` modificador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla o deshabilitar la regla si no le preocupa el rendimiento.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un tipo, `UseReadOnly` , que infringe la regla y un tipo, `UseConstant` , que cumple la regla.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
