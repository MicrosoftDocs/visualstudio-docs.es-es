---
title: 'CA1009: Declare los controladores de evento correctamente | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9f3764e7e7965fb9efe46a8404273de9adde4a34
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62422827"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Declarar los controladores de evento correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|Identificador de comprobación|CA1009|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un delegado que controla un evento público o protegido no tiene la firma correcta, devuelve el tipo o los nombres de parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de control de eventos toman dos parámetros. El primero es de tipo <xref:System.Object?displayProperty=fullName> y se denomina 'sender'. Éste es el objeto que provocó el evento. El segundo parámetro es de tipo <xref:System.EventArgs?displayProperty=fullName> y se denomina 'e'. Estos son los datos están asociados a este evento. Por ejemplo, si el evento se desencadena cuando se abre un archivo, los datos de evento normalmente contienen el nombre del archivo.

 Métodos de controlador de eventos no deben devolver un valor. En el lenguaje de programación C#, esto se indica mediante el tipo de valor devuelto `void`. Un controlador de eventos puede invocar varios métodos en varios objetos. Si se permiten los métodos que devuelven un valor, se produciría varios valores devueltos para cada evento, y solo el valor de este último método se invocó estaría disponible.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la firma, tipo de valor devuelto o los nombres de parámetro del delegado. Para obtener más información, vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra a un delegado que es adecuado para controlar los eventos. Los métodos que pueden invocarse mediante este controlador de eventos cumplen con la firma que se especifica en las instrucciones de diseño. `AlarmEventHandler` es el nombre de tipo del delegado. `AlarmEventArgs` se deriva de la clase base de datos de evento, <xref:System.EventArgs>, y contiene datos de eventos de alarma.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Vea también
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: Eventos y delegados](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
