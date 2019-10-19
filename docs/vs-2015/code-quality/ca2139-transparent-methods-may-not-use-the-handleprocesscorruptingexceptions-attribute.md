---
title: 'CA2139: los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 821598d7708fa8681f1dbc5fee65978d7498dbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603001"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Los métodos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|Identificador de comprobación|CA2139|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método transparente se marca con el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla desencadena cualquier método que sea transparente e intenta controlar una excepción de daño de proceso mediante el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Una excepción de daño de proceso es una clasificación de excepción de la versión 4,0 de CLR de excepciones como <xref:System.AccessViolationException>. El atributo HandleProcessCorruptedStateExceptionsAttribute solo lo pueden utilizar los métodos críticos para la seguridad, y se omitirá si se aplica a un método transparente. Para controlar las excepciones de daños en el proceso, este método debe ser crítico para la seguridad o crítico para la seguridad.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> o marque el método con el <xref:System.Security.SecurityCriticalAttribute> o el atributo <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En este ejemplo, se marca un método transparente con el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo y se producirá un error en la regla. El método también debe marcarse con el <xref:System.Security.SecurityCriticalAttribute> o el atributo <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
