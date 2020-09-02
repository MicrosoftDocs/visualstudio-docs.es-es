---
title: 'CA1415: declare las invocaciones de P correctamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547854"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declare los elementos P/Invoke correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|Identificador de comprobación|CA1415|
|Category|Microsoft. Interoperability|
|Cambio problemático|No problemático: Si la P/Invoke que declara el parámetro no se puede considerar fuera del ensamblado. Interrumpir: Si la P/Invoke que declara el parámetro puede verse fuera del ensamblado.|

## <a name="cause"></a>Causa
 No se ha declarado correctamente un método de invocación de plataforma.

## <a name="rule-description"></a>Descripción de la regla
 Un método de invocación de plataforma tiene acceso al código no administrado y se define mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Actualmente, esta regla busca declaraciones de método de invocación de plataforma que tienen como destino funciones de Win32 que tienen un puntero a un parámetro de estructura superpuesto y el parámetro administrado correspondiente no es un puntero a una <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estructura.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, declare correctamente el método de invocación de plataforma.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran métodos de invocación de plataforma que infringen la regla y satisfacen la regla.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Consulte también
 [Interoperating with Unmanaged Code](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) (Interoperar con código no administrado)
