---
title: 'CA1301: Evitar aceleradores duplicados | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b9e2855827fb0befe69dafe08981b10a12d0700
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitar aceleradores duplicados
|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|Identificador de comprobación|CA1301|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo extiende <xref:System.Windows.Forms.Control?displayProperty=fullName> y contiene dos o más controles de nivel superior que tienen teclas de acceso idénticas que se almacenan en un archivo de recursos.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Una tecla de acceso, también denominada acelerador, permite el acceso mediante teclado a un control utilizando la tecla ALT. Cuando varios controles tienen las teclas de acceso duplicadas, no se define correctamente el comportamiento de la tecla de acceso. El usuario no podría tener acceso al control deseado mediante el uso de la clave de acceso y puede que esté habilitado un control diferente del que está diseñado.  
  
 La implementación actual de esta regla omite los elementos de menú. Sin embargo, los elementos de menú en el mismo submenú no deberían tener teclas de acceso idénticas.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, definir teclas de acceso únicas para todos los controles.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un formulario mínimo que contiene dos controles que tienen teclas de acceso idénticas. Las claves se almacenan en un archivo de recursos, que no se muestra; Sin embargo, sus valores se mostrarán en el marcado como comentario fuera `checkBox.Text` líneas. El comportamiento de aceleradores duplicados puede examinarse intercambiando las `checkBox.Text` líneas con sus homólogos comentados. Sin embargo, en este caso, el ejemplo no generará una advertencia de la regla.  
  
 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index)