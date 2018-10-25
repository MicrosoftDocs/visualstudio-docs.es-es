---
title: 'CA2116: Los métodos APTCA deben llamar solo a métodos APTCA | Microsoft Docs'
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
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 766de62f4781dc7ce164155a2090ffabac913a22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819555"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: Los métodos APTCA deben llamar solo a métodos APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|Identificador de comprobación|CA2116|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un método en un ensamblado con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> atributo llama a un método en un ensamblado que no tiene el atributo.

## <a name="rule-description"></a>Descripción de la regla
 De forma predeterminada, los métodos públicos o protegidos en ensamblados con nombres seguros implícitamente están protegidos por un [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) de plena confianza; sólo de plena confianza para los autores de llamadas pueden tener acceso a un ensamblado con nombre seguro. Los ensamblados con nombre seguro marcados con el <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributo (APTCA) no tiene esta protección. El atributo deshabilita la petición de vínculo, lo que el ensamblado puede tener acceso a los llamadores que no tienen plena confianza, como el código que se ejecuta desde una intranet o Internet.

 Cuando el atributo APTCA está presente en un ensamblado de plena confianza y el ensamblado ejecuta código en otro ensamblado que no permite a llamadores parcialmente confiables, es posible un ataque de seguridad. Si dos métodos `M1` y `M2` cumplen las condiciones siguientes, los llamadores malintencionados pueden usar el método `M1` para omitir la petición de vínculo de plena confianza implícita que protege `M2`:

- `M1` ¿se declara un método público en un ensamblado de plena confianza que tiene el atributo APTCA.

- `M1` llama a un método `M2` fuera `M1`del ensamblado.

- `M2`del ensamblado no tiene el atributo APTCA y, por lo tanto, no debe ejecutarse por o en nombre de los llamadores de confianza parcial.

  Un llamador de confianza parcial `X` puede llamar al método `M1`, haciendo que `M1` para llamar a `M2`. Dado que `M2` no tiene el atributo APTCA, su llamador inmediato (`M1`) debe satisfacer una petición de vínculo de plena confianza; `M1` es de plena confianza y, por tanto, supera esta comprobación. El riesgo de seguridad es porque `X` no participa en el cumplimiento de la petición de vínculo que protege `M2` es de confianza. Por lo tanto, los métodos con el atributo APTCA no deben llamar a métodos que no tienen el atributo.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Si el atributo APCTA es necesario, use una petición para proteger el método que llama en el ensamblado de plena confianza. Los permisos exactos demanda dependerá de la funcionalidad expuesta por el método. Si es posible, proteja el método con una petición de plena confianza para asegurarse de que la funcionalidad subyacente no se expone a llamadores de confianza parcial. Si esto no es posible, seleccione un conjunto de permisos que protege eficazmente la funcionalidad expuesta. Para obtener más información acerca de las peticiones, consulte [demandas](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Para suprimir una advertencia de esta regla de forma segura, debe asegurarse de que la funcionalidad expuesta por el método no directa o indirectamente permiten que los llamadores tener acceso a información confidencial, operaciones o los recursos que se pueden usar de forma destructiva.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente utiliza dos ensamblados y una aplicación de prueba para ilustrar que esta regla detecta la vulnerabilidad de seguridad. El primer ensamblado no tiene el atributo APTCA y no debe estar accesible a los llamadores de confianza parcial (representado por `M2` en la explicación anterior).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Ejemplo
 El segundo ensamblado es de plena confianza y permite llamadores parcialmente confiables (representado por `M1` en la explicación anterior).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Ejemplo
 La aplicación de prueba (representado por `X` en la explicación anterior) es de confianza parcial.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **La demanda de plena confianza: error en la solicitud. ** 
 **ClassRequiringFullTrust.DoWork llamó.**
## <a name="related-rules"></a>Reglas relacionadas
 [CA2117: Los tipos APTCA solo amplían tipos base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [ensamblados de .NET Framework invocables por código de confianza parcial](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [utilizar parcialmente bibliotecas de código de confianza](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [demandas](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Peticiones de vínculos](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



