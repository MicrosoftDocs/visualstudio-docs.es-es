---
title: 'CA2109: Revisar los controladores de eventos visibles'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf11564e7420231ac6ab65c6dc00762bb4077ef2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Revisar los controladores de eventos visibles
|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|Identificador de comprobación|CA2109|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Se detectó un método de control de eventos público o protegido.

## <a name="rule-description"></a>Descripción de la regla
 Un método de control de eventos visible externamente presenta un problema de seguridad que requiere revisión.

 No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario. Un controlador de eventos, un tipo de delegado que invoca al método expuesto puede agregarse a cualquier evento siempre que coincidan las firmas de controlador y del evento. Eventos potencialmente pueden proceder de cualquier código y con frecuencia se generan por código de plena confianza del sistema en respuesta a las acciones del usuario como hacer clic en un botón. Agregar una comprobación de seguridad a un método de control de eventos impedir que código registrar un controlador de eventos que invoca el método.

 Una petición no puede proteger de forma confiable un método invocado por un controlador de eventos. Seguridad solicita ayuda proteger el código de los llamadores no confiables mediante el examen de los llamadores en la pila de llamadas. Código que agrega un controlador de eventos a un evento no es necesariamente presente en la pila de llamadas cuando los métodos del controlador de eventos se ejecutan. Por lo tanto, la pila de llamadas podría haber sólo llamadores de plena confianza cuando se invoca el método de controlador de eventos. Esto hace que las peticiones realizadas por el método de controlador de eventos sea correcta. Además, se puede declarar el permiso solicitado cuando se invoca el método. Por estas razones, el riesgo de no corregir una infracción de esta regla solo se evalúa después de revisar el método de control de eventos. Al revisar el código, tenga en cuenta lo siguiente:

-   ¿El controlador de eventos lleva a cabo ninguna operación peligrosa o explotable, como los permisos de aserción o suprimir el permiso de código no administrado?

-   ¿Cuáles son las amenazas de seguridad a y desde el código ya que se puede ejecutar en cualquier momento con sólo alta llamadores en la pila de confianza?

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, revise el método y evalúe lo siguiente:

-   ¿Puede hacer que el método de control de eventos no públicos?

-   ¿Puede mover toda la funcionalidad peligrosa fuera el controlador de eventos?

-   ¿Si se impone una petición de seguridad, esto se puede lograr en alguna otra manera?

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de una revisión cuidadosa de la seguridad para asegurarse de que el código no supongan una amenaza de seguridad.

## <a name="example"></a>Ejemplo
 El código siguiente muestra un método de control de eventos que se puede emplear mal por código malintencionado.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
