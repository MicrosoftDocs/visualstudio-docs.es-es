---
title: 'CA1415: Declare los elementos P / Invoke correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5fa1473d96d8b74b07497ef72a0a92bcf80e1fe3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994901"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declarar elementos P/Invoke correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|Identificador de comprobación|CA1415|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|No problemático: si el valor de P/Invoke que declara el parámetro no puede verse fuera del ensamblado. Problemático: si P/Invoke que declara el parámetro puede verse fuera del ensamblado.|

## <a name="cause"></a>Motivo
 Una plataforma de invocación de método se ha declarado incorrectamente.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando el `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Actualmente, esta regla busca declaraciones de métodos que tienen como destino las funciones de Win32 que tienen un puntero a un parámetro de estructura OVERLAPPED de invocación de plataforma y el parámetro administrado correspondiente no es un puntero a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estructura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, debe declarar correctamente la plataforma de invocación de método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los métodos que infringen la regla y que cumplen la regla de invocación de plataforma.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Vea también
 [Interoperating with Unmanaged Code](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) (Interoperar con código no administrado)
