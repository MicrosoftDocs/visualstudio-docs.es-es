---
title: 'CA2114: la seguridad del método debe ser un superconjunto de tipo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1adc8f610644d736bc4546d8299457ba0234a1d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658670"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La seguridad del método debería ser un supraconjunto del tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|Identificador de comprobación|CA2114|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene seguridad declarativa y uno de sus métodos tiene seguridad declarativa para la misma acción de seguridad, y la acción de seguridad no es [peticiones de vínculo](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ni [peticiones de herencia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), y los permisos comprobados por el tipo no son un subconjunto del permisos comprobados por el método.

## <a name="rule-description"></a>Descripción de la regla
 Un método no debe tener una seguridad declarativa de nivel de método y de nivel de tipo para la misma acción. Las dos comprobaciones no se combinan; solo se aplica la demanda de nivel de método. Por ejemplo, si un tipo solicita permiso `X` y uno de sus métodos exige el permiso `Y`, el código no tiene que tener permiso `X` para ejecutar el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise el código para asegurarse de que se requieren ambas acciones. Si se requieren ambas acciones, asegúrese de que la acción de nivel de método incluye la seguridad especificada en el nivel de tipo. Por ejemplo, si el tipo solicita permiso `X` y su método también debe exigir el permiso `Y`, el método debe solicitar explícitamente `X` y `Y`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el método no requiere la seguridad especificada por el tipo. Sin embargo, esto no es un escenario normal y podría indicar una necesidad de una revisión cuidadosa del diseño.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usan permisos de entorno para mostrar los peligros de infringir esta regla. En este ejemplo, el código de aplicación crea una instancia del tipo protegido antes de denegar el permiso requerido por el tipo. En un escenario de amenazas real, la aplicación requeriría otra manera de obtener una instancia del objeto.

 En el ejemplo siguiente, la biblioteca solicita permiso de escritura para un tipo y permiso de lectura para un método.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Ejemplo
 El siguiente código de aplicación muestra la vulnerabilidad de la biblioteca llamando al método aunque no cumple el requisito de seguridad de nivel de tipo.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **[Todos los permisos] información personal: 6/16/1964 12:00:00 am** 
 **[sin permiso de escritura (solicitado por tipo)] información personal: 6/16/1964 12:00:00 AM** 
 **[ningún permiso de lectura (solicitado por el método)] no se pudo obtener acceso a la personal información: error en la solicitud.**
## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) el vínculo [peticiones de herencia](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [requiere](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
