---
title: "CA1009: Declare los controladores de evento correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1009: Declare los controladores de evento correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|Identificador de comprobación|CA1009|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un delegado que controla un evento público o protegido no tiene la firma, el tipo de valor devuelto o los nombres de parámetro correctos.  
  
## Descripción de la regla  
 Los métodos de control de eventos toman dos parámetros.  El primero es de tipo <xref:System.Object?displayProperty=fullName> y se denomina 'sender'.  Éste es el objeto que provocó el evento.  El segundo parámetro es de tipo <xref:System.EventArgs?displayProperty=fullName> y se denomina 'e'.  Estos son los datos están asociados a este evento.  Por ejemplo, si se provoca el evento cuando se abre un archivo, los datos de evento contienen normalmente el nombre del archivo.  
  
 Los métodos de control de eventos no deben devolver un valor.  En el lenguaje de programación C\#, esto lo indica el tipo de valor devuelto `void`.  Un controlador de eventos puede invocar varios métodos en varios objetos.  Si los métodos pudieran devolver un valor, se devolverían varios valores por cada evento y solo estaría disponible el valor del último método invocado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija la firma, tipo de valor devuelto o los nombres de parámetro del delegado.  Para obtener información detallada, vea los siguientes temas:  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra un delegado que es adecuado para el control de errores.  Los métodos que puede invocar este controlador de eventos cumplen la firma especificada en las Instrucciones de diseño.  `AlarmEventHandler` es el nombre de tipo del delegado.  `AlarmEventArgs` deriva de la clase base para los datos de evento, <xref:System.EventArgs>, y retiene los datos de evento de alarma.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Reglas relacionadas  
 [CA2109: Revisar los controladores de eventos visibles](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## Vea también  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Eventos y delegados](http://msdn.microsoft.com/es-es/d98fd58b-fa4f-4598-8378-addf4355a115)