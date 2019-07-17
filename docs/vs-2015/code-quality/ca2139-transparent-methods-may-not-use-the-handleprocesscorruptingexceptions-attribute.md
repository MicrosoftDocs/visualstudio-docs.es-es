---
title: 'CA2139: Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a05813d01a05c02455d43e74029251e96e4e4580
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154281"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|Identificador de comprobación|CA2139|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método transparente se marca con el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla desencadena cualquier método que sea transparente e intenta controlar una excepción de daño mediante el uso de proceso el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo. Una excepción de daño de proceso es una clasificación CLR versión 4.0 de excepciones tales <xref:System.AccessViolationException>. El atributo HandleProcessCorruptedStateExceptionsAttribute solo lo pueden utilizar los métodos críticos para la seguridad, y se omitirá si se aplica a un método transparente. Para controlar las excepciones de daño de proceso, este método debe ser crítico para la seguridad o crítico para la seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo o marque el método con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En este ejemplo, un método transparente está marcado con el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> de atributo y se producirá un error de la regla. También debe marcarse con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
