---
title: 'CA2109: revisar los controladores de eventos visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520983"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Revisar los controladores de eventos visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|Identificador de comprobación|CA2109|
|Category|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Se detectó un método de control de eventos público o protegido.

## <a name="rule-description"></a>Descripción de la regla
 Un método de control de eventos visible externamente presenta un problema de seguridad que requiere revisión.

 No se deberían exponer los métodos de control de eventos a menos que sea absolutamente necesario. Se puede Agregar un controlador de eventos, un tipo de delegado, que invoca el método expuesto a cualquier evento, siempre y cuando el controlador y las firmas de eventos coincidan. Los eventos pueden ser generados por cualquier código y se suelen generar mediante código del sistema de plena confianza en respuesta a las acciones del usuario, como hacer clic en un botón. Agregar una comprobación de seguridad a un método de control de eventos no impide que el código registre un controlador de eventos que invoca el método.

 Una demanda no puede proteger de forma confiable un método invocado por un controlador de eventos. Las peticiones de seguridad ayudan a proteger el código de los llamadores que no son de confianza mediante el examen de los llamadores en la pila de llamadas. El código que agrega un controlador de eventos a un evento no está necesariamente presente en la pila de llamadas cuando se ejecutan los métodos del controlador de eventos. Por lo tanto, la pila de llamadas podría tener solo llamadores de plena confianza cuando se invoca el método de controlador de eventos. Esto hace que las peticiones realizadas por el método del controlador de eventos se realicen correctamente. Además, el permiso exigido podría ser imponerse cuando se invoca el método. Por estos motivos, el riesgo de no corregir una infracción de esta regla solo se puede evaluar después de revisar el método de control de eventos. Al revisar el código, tenga en cuenta los siguientes problemas:

- ¿El controlador de eventos realiza cualquier operación peligrosa o explotable, como la aserción de permisos o la supresión de permisos de código no administrado?

- ¿Cuáles son las amenazas de seguridad hacia y desde el código porque puede ejecutarse en cualquier momento solo con llamadores de gran confianza en la pila?

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, revise el método y evalúe lo siguiente:

- ¿Se puede hacer que el método de control de eventos no sea público?

- ¿Puede trasladar toda la funcionalidad peligrosa fuera del controlador de eventos?

- Si se impone una demanda de seguridad, ¿se puede realizar de alguna otra manera?

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de una revisión de seguridad minuciosa para asegurarse de que el código no plantea una amenaza de seguridad.

## <a name="example"></a>Ejemplo
 En el código siguiente se muestra un método de control de eventos que puede ser inutilizable por código malintencionado.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Peticiones de seguridad](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
