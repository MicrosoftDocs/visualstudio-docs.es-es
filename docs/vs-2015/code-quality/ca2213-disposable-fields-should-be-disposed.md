---
title: 'CA2213: Los campos desechables deben desechar | Microsoft Docs'
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
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4e59dd35ab1f787dcaada5448443e35efc1f6c9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910509"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Aplique Dispose a los campos a los que se pueda
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|Identificador de comprobación|CA2213|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara campos que son de tipos que también implementan <xref:System.IDisposable>. El <xref:System.IDisposable.Dispose%2A> no se llama al método del campo el <xref:System.IDisposable.Dispose%2A> método del tipo declarativo.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo es responsable de eliminar todos sus recursos no administrados; Esto se logra implementando <xref:System.IDisposable>. Esta regla comprueba si un tipo desechable `T` declara un campo `F` que es una instancia de un tipo desechable `FT`. Para cada campo `F`, la regla intenta buscar una llamada a `FT.Dispose`. La regla busca los métodos llamados por `T.Dispose`y un nivel inferior (los métodos llamados por los métodos llamados por `FT.Dispose`).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, llame a <xref:System.IDisposable.Dispose%2A> en los campos que son de tipos que implementan <xref:System.IDisposable> si usted es responsable de asignar y liberar los recursos no administrados mantenidos por el campo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si no es su responsabilidad para liberar los recursos mantenidos por el campo, o si la llamada a <xref:System.IDisposable.Dispose%2A> se produce en un nivel más profundo que realiza la llamada a las comprobaciones de la regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeA` que implementa <xref:System.IDisposable> (`FT` en la explicación anterior).

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo `TypeB` que infringe esta regla declarando un campo `aFieldOfADisposableType` (`F` en la explicación anterior) como un tipo desechable (`TypeA`) y no se llama a <xref:System.IDisposable.Dispose%2A> en el campo. `TypeB` corresponde a `T` en la explicación anterior.

 [!code-csharp[FxCop.Usage.IDisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableFields/cs/FxCop.Usage.IDisposableFields.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.IDisposable?displayProperty=fullName> [Patrón de Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



