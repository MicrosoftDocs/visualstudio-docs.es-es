---
title: 'CA1415: Declare los elementos P-se invoca correctamente | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b1bacff8f97a27a02ccdf8e6f6047bfd6ad9c90b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Declare los elementos P/Invoke correctamente
|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|Identificador de comprobación|CA1415|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático: si el elemento P/Invoke que declara el parámetro no se pueden ver desde fuera del ensamblado. Problemático: si el elemento P/Invoke que declara el parámetro puede verse fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Método de invocación de plataforma se ha declarado incorrectamente.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Actualmente, esta regla busca declaraciones de método que tienen como destino funciones de Win32 que tienen un puntero a un parámetro de estructura OVERLAPPED de invocación de plataforma y el parámetro administrado correspondiente no es un puntero a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> estructura.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, debe declarar correctamente la plataforma de invocación de método.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra los métodos que infringen la regla y cumplen la regla de invocación de plataforma.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)