---
title: 'CA1009: declare los controladores de eventos correctamente | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547893"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Declarar los controladores de evento correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|Identificador de comprobación|CA1009|
|Category|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un delegado que controla un evento público o protegido no tiene la firma, el tipo de valor devuelto o los nombres de parámetro correctos.

## <a name="rule-description"></a>Descripción de la regla
 Los métodos de control de eventos toman dos parámetros. El primero es de tipo <xref:System.Object?displayProperty=fullName> y se denomina ' Sender '. Éste es el objeto que provocó el evento. El segundo parámetro es de tipo <xref:System.EventArgs?displayProperty=fullName> y se denomina ' e '. Estos son los datos están asociados a este evento. Por ejemplo, si el evento se genera cada vez que se abre un archivo, los datos del evento normalmente contienen el nombre del archivo.

 Los métodos de controlador de eventos no deben devolver un valor. En el lenguaje de programación C#, esto se indica mediante el tipo de valor devuelto `void` . Un controlador de eventos puede invocar varios métodos en varios objetos. Si se permite que los métodos devuelvan un valor, se producirán varios valores devueltos para cada evento y solo estará disponible el valor del último método que se invocó.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija la firma, el tipo de valor devuelto o los nombres de parámetro del delegado. Para obtener más información, vea el ejemplo siguiente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un delegado adecuado para controlar eventos. Los métodos que puede invocar este controlador de eventos cumplen con la firma que se especifica en las instrucciones de diseño. `AlarmEventHandler`es el nombre de tipo del delegado. `AlarmEventArgs`deriva de la clase base para los datos de evento, <xref:System.EventArgs> y contiene los datos de eventos de alarma.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Consulte también
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: eventos y delegados](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
