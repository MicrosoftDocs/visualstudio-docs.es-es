---
title: 'CA1301: evitar aceleradores duplicados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 772c9bee3f43c42701bfa460c622f4a225ec59cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539183"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar los aceleradores duplicados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|Identificador de comprobación|CA1301|
|Category|Microsoft. Globalization|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo extiende <xref:System.Windows.Forms.Control?displayProperty=fullName> y contiene dos o más controles de nivel superior que tienen claves de acceso idénticas que se almacenan en un archivo de recursos.

## <a name="rule-description"></a>Descripción de la regla
 Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen las teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso. Es posible que el usuario no pueda tener acceso al control previsto mediante el uso de la tecla de acceso y un control distinto del que está previsto que esté habilitado.

 La implementación actual de esta regla omite los elementos de menú. Sin embargo, los elementos de menú del mismo submenú no deben tener claves de acceso idénticas.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, defina las claves de acceso únicas para todos los controles.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una forma mínima que contiene dos controles que tienen claves de acceso idénticas. Las claves se almacenan en un archivo de recursos, que no se muestra; sin embargo, sus valores aparecen en las líneas comentadas `checkBox.Text` . El comportamiento de los aceleradores duplicados se puede examinar intercambiando las `checkBox.Text` líneas con sus homólogos comentados. Sin embargo, en este caso, el ejemplo no generará una advertencia de la regla.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Recursos de aplicaciones de escritorio](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
