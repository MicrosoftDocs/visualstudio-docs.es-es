---
title: 'CA2137: los métodos transparentes deben contener solo IL que se pueda comprobar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6219acde1f62c946e08325f4764dc49dde461d2f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546580"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|Identificador de comprobación|CA2137|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un método contiene código que no se puede comprobar o devuelve un tipo por referencia.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MSIL no comprobable (Lenguaje intermedio de Microsoft). Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL.

 Para asegurarse de que el código solo contiene MSIL comprobable, ejecute [Peverify.exe (herramienta peverify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) en el ensamblado. Ejecute PEVerify con la opción **/transparent** , que limita la salida a solo los métodos transparentes no comprobables, lo que produciría un error. Si no se usa la opción/Transparent, PEVerify también comprueba los métodos críticos que pueden contener código no comprobable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método con <xref:System.Security.SecurityCriticalAttribute> el <xref:System.Security.SecuritySafeCriticalAttribute> atributo o o quite el código no comprobable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El método en este ejemplo utiliza código no comprobable y debe marcarse con el <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atributo o.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
