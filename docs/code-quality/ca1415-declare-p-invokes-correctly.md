---
title: "CA1415: Declare los elementos P/Invoke correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
helpviewer_keywords: 
  - "CA1415"
  - "DeclarePInvokesCorrectly"
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1415: Declare los elementos P/Invoke correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|Identificador de comprobación|CA1415|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|No problemático: si la funcionalidad P\/Invoke que declara el parámetro no se puede ver fuera del ensamblado.  Problemático: si la funcionalidad P\/Invoke que declara el parámetro se puede ver fuera del ensamblado.|  
  
## Motivo  
 Se declara un método de invocación de plataforma incorrectamente.  
  
## Descripción de la regla  
 Un método de invocación de plataforma tiene acceso al código no administrado y se define utilizando la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  En la actualidad, esta regla busca declaraciones de método de invocación de plataforma dirigidas a funciones de Win32 que tengan un puntero a un parámetro de estructura OVERLAPPED y el parámetro administrado correspondiente no es un puntero para una estructura <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, debe declarar correctamente el método de invocación de plataforma.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra métodos de invocación de plataforma que infringen y que cumplen la regla.  
  
 [!code-cs[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## Vea también  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)