---
title: 'CA2137: Los métodos transparentes deben contener solo IL comprobable | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f686bcc82dc76a1c08417140a7f5d422651fb61d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293603"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Los métodos transparentes deben contener solo IL que se pueda comprobar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|Identificador de comprobación|CA2137|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método contiene código que no se puede comprobar o devuelve un tipo por referencia.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla se desencadena en los intentos del código transparente en seguridad de ejecutar MSIL no comprobable (Lenguaje intermedio de Microsoft). Sin embargo, la regla no contiene un comprobador de IL completo y, en su lugar, utiliza la heurística para detectar la mayoría de las infracciones de comprobación MSIL.

 Para estar seguro de que el código solo contiene MSIL comprobable, ejecute [Peverify.exe (herramienta PEVerify)](http://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) en el ensamblado. Ejecutar PEVerify con la **/ transparente** opción que limita la salida a sólo puede comprobar los métodos transparentes que provocaría un error. Si la / opción transparente no se utiliza, PEVerify también comprueba los métodos críticos que pueden contener código no comprobable.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, marque el método con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> de atributo o quite el código no comprobable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El método en este ejemplo usa código no comprobable y se debe marcar con el <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> atributo.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]



