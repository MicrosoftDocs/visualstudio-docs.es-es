---
title: 'CA1303: No pasar literales como adaptados parámetros | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1af1edcd86d73687e24619d7e998fe304f9b5787
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303: No pasar literales como parámetros localizados
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|Identificador de comprobación|CA1303|  
|Categoría|Microsoft.Globalization|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Un método pasa una literal de cadena como parámetro a un constructor o método en el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] biblioteca de clases y esa cadena debería ser localizable.  
  
 Esta advertencia se produce si una cadena literal se pasa como un valor a un parámetro o una propiedad y uno o varios de los casos siguientes son verdadera:  
  
-   El <xref:System.ComponentModel.LocalizableAttribute> del parámetro o la propiedad está establecido en true.  
  
-   El nombre de parámetro o la propiedad contiene "Text", "Mensaje" o "Título".  
  
-   El nombre del parámetro de cadena que se pasa a un método Console.Write o Console.WriteLine es "value" o "format".  
  
## <a name="rule-description"></a>Descripción de la regla  
 Literales de cadena que se incrustan en el código fuente son difíciles de localizar.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, reemplace el literal de cadena con una cadena recuperada mediante una instancia de la <xref:System.Resources.ResourceManager> clase.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si no se puede adaptar la biblioteca de código, o si la cadena no se expone al usuario final o a los desarrolladores que utilizan la biblioteca de código.  
  
 Los usuarios pueden eliminar ruido de los métodos que no se debe pasar cadenas localizadas cambiando el parámetro o la propiedad con nombre o marcando estos elementos como condicionales.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un método que produce una excepción cuando cualquiera de sus dos argumentos están fuera del intervalo. Para el primer argumento, el constructor de la excepción se pasa una cadena literal que infringe esta regla. Para el segundo argumento, se pasa al constructor correctamente una cadena recuperada mediante un <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 [Recursos de aplicaciones de escritorio](/dotnet/framework/resources/index)