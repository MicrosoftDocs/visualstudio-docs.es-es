---
title: 'CA1009: Declare los controladores de eventos correctamente | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6191676f94300dfbfafcb8ceb6b0874a8e5b558a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Declare los controladores de evento correctamente
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|Identificador de comprobación|CA1009|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Un delegado que controla un evento público o protegido no tiene la firma correcta, devuelve el tipo o los nombres de parámetros.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Los métodos de control de eventos toman dos parámetros. El primero es de tipo <xref:System.Object?displayProperty=fullName> y se denomina 'sender'. Éste es el objeto que provocó el evento. El segundo parámetro es de tipo <xref:System.EventArgs?displayProperty=fullName> y se denomina 'e'. Estos son los datos están asociados a este evento. Por ejemplo, si el evento se desencadena cuando se abre un archivo, los datos del evento normalmente contienen el nombre del archivo.  
  
 Métodos de controlador de eventos no deben devolver un valor. En el lenguaje de programación C#, esto se indica mediante el tipo de valor devuelto `void`. Un controlador de eventos puede invocar varios métodos en varios objetos. Si los métodos pueden devolver un valor, se produciría varios valores devueltos para cada evento, y solo el valor del último método invocado estaría disponible.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija la firma, el tipo de valor devuelto o los nombres de parámetro del delegado. Para obtener más información, vea el ejemplo siguiente.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra a un delegado que es adecuado para controlar los eventos. Los métodos que pueden invocarse mediante este controlador de eventos cumplen con la firma que se especifica en las instrucciones de diseño. `AlarmEventHandler`es el nombre de tipo del delegado. `AlarmEventArgs`se deriva de la clase base de datos de eventos, <xref:System.EventArgs>, y contiene datos del evento de alarma.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Controlar y provocar eventos](/dotnet/standard/events/index)  