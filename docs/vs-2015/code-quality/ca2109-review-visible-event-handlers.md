---
title: 'CA2109: Revisar los controladores de eventos visibles | Microsoft Docs'
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
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42699d257aaf42c68830bed958458fb92b67e1f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182668"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Revisar los controladores de eventos visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|Identificador de comprobación|CA2109|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Se detectó un método de control de eventos público o protegido.

## <a name="rule-description"></a>Descripción de la regla
 Un método visible externamente de control de eventos presenta un problema de seguridad que requiere la revisión.

 No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario. Un controlador de eventos, un tipo de delegado que invoca el método expuesto puede agregarse a cualquier evento siempre que coincidan las firmas de controlador de eventos. Eventos potencialmente se pueden generar cualquier código y con frecuencia son generados por código de plena confianza del sistema en respuesta a las acciones del usuario como hacer clic en un botón. Agregar una comprobación de seguridad a un método de control de eventos no evita que código registrar un controlador de eventos que se invoca el método.

 Una demanda no puede proteger de forma confiable un método invocado por un controlador de eventos. Ayuda de las solicitudes de seguridad proteger el código de los llamadores de confianza mediante el examen de los llamadores situados en la pila de llamadas. El código que agrega un controlador de eventos a un evento no es necesariamente presente en la pila de llamadas cuando se ejecutan los métodos del controlador de eventos. Por lo tanto, la pila de llamadas podría haber sólo llamadores de plena confianza cuando se invoca el método de controlador de eventos. Esto hace que las demandas realizadas por el método de controlador de eventos se realice correctamente. Además, se puede declarar el permiso exigido cuando se invoca el método. Por estas razones, sólo puede evaluarse el riesgo de no corregir una infracción de esta regla después de revisar el método de control de eventos. Cuando revise el código, tenga en cuenta lo siguiente:

-   ¿El controlador de eventos lleva a cabo ninguna operación peligrosa o explotable, como validar los permisos o suprimir el permiso de código no administrado?

-   ¿Cuáles son las amenazas de seguridad a y desde el código porque se puede ejecutar en cualquier momento con sólo altamente llamadores en la pila de confianza?

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, revise el método y evaluar las siguientes:

-   ¿Puede hacer que el método de control de eventos no públicos?

-   ¿Puede mover toda la funcionalidad peligrosa fuera el controlador de eventos?

-   ¿Si se impone una petición de seguridad, esto se puede realizar en alguna otra manera?

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de revisar cuidadosamente la seguridad para asegurarse de que el código no supongan una amenaza de seguridad.

## <a name="example"></a>Ejemplo
 El código siguiente muestra un método de control de eventos que se puede usar incorrectamente por código malintencionado.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Peticiones de seguridad](http://msdn.microsoft.com/en-us/324c14f8-54ff-494d-9fd1-bfd20962c8ba)



