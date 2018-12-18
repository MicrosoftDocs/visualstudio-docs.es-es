---
title: 'CA1001: Los tipos que poseen campos descartables deben ser descartables | Microsoft Docs'
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
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a4bde7f20d1e7c93aec7a4a1a3abf44c21659b6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176454"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001: Los tipos que poseen campos descartables deben ser descartables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|Identificador de comprobación|CA1001|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Non-problemático: si el tipo no es visible fuera del ensamblado.<br /><br /> Importante: si el tipo es visible fuera del ensamblado.|  
  
## <a name="cause"></a>Motivo  
 Una clase declara e implementa un campo de instancia que es un <xref:System.IDisposable?displayProperty=fullName> tipo y la clase no implementa <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una clase implementa la <xref:System.IDisposable> interfaz para desechar recursos no administrados que posee. Un campo de instancia que es un <xref:System.IDisposable> tipo indica que el campo posee un recurso no administrado. Una clase que declara un <xref:System.IDisposable> campo indirectamente posee un recurso no administrado y debería implementar el <xref:System.IDisposable> interfaz. Si la clase no posee directamente los recursos no administrados, no debe implementar un finalizador.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente <xref:System.IDisposable> y desde el <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> llamada al método el <xref:System.IDisposable.Dispose%2A> método del campo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra una clase que infringe la regla y una clase que cumple la regla mediante la implementación <xref:System.IDisposable>. La clase no implementa un finalizador porque la clase posee directamente ningún recurso no administrado.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2213: Aplique Dispose a los campos a los que se pueda](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Los tipos descartables deben declarar el finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Los métodos Dispose deben llamar al método Dispose de la clase base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Los tipos que poseen recursos nativos deben ser descartables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

