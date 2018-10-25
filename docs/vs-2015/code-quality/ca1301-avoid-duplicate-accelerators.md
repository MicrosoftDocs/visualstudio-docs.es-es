---
title: 'CA1301: Evitar aceleradores duplicados | Microsoft Docs'
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
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 92c5baefff76626a42553d6ba5380fd07448b109
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886660"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar aceleradores duplicados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|Identificador de comprobación|CA1301|
|Categoría|Microsoft.Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Extiende un tipo <xref:System.Windows.Forms.Control?displayProperty=fullName> y contiene dos o más controles de nivel superior que tienen claves de acceso idénticas que se almacenan en un archivo de recursos.

## <a name="rule-description"></a>Descripción de la regla
 Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen las teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso. El usuario no pueda obtener acceso al control deseado mediante el uso de la clave de acceso y puede habilitarse un control diferente al que está diseñado.

 La implementación actual de esta regla omite los elementos de menú. Sin embargo, los elementos de menú en el mismo submenú no deberían tener teclas de acceso idénticas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, definir teclas de acceso único para todos los controles.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un formulario mínimo que contiene dos controles que tienen claves de acceso idénticas. Las claves se almacenan en un archivo de recursos que no se muestra; Sin embargo, sus valores se mostrarán en la comentada out `checkBox.Text` líneas. El comportamiento de aceleradores duplicados puede examinarse intercambiando el `checkBox.Text` líneas con sus homólogos comentadas. Sin embargo, en este caso, el ejemplo no generará una advertencia de la regla.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos en aplicaciones de escritorio](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



