---
title: 'CA2114: Seguridad del método debe ser un supraconjunto del tipo | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9e0024ae6db5af3f1cf23c07fe29fbac8e4827d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997727"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La seguridad del método debe ser un supraconjunto del tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|Identificador de comprobación|CA2114|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene seguridad declarativa y uno de sus métodos tiene seguridad declarativa para la misma acción de seguridad y la acción de seguridad no es [peticiones de vínculo](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) o [peticiones de herencias](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9)y los permisos comprueba el tipo no son un subconjunto de permisos comprobados por el método.

## <a name="rule-description"></a>Descripción de la regla
 Un método no debe tener tanto un seguridad declarativa de nivel de método y el nivel de tipo para la misma acción. No se combinan las dos comprobaciones; se aplica solo a la demanda de nivel de método. Por ejemplo, si un tipo solicita permiso `X`, y uno de sus métodos solicita permiso `Y`, código no tiene que tener el permiso `X` para ejecutar el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise el código para asegurarse de que ambas acciones son necesarias. Si se requieren ambas acciones, debe asegurarse de que la acción de nivel de método incluye la seguridad especificada en el nivel de tipo. Por ejemplo, si el tipo solicita permiso `X`, y su método también debe solicitar permiso `Y`, debe solicitar explícitamente el método `X` y `Y`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el método no requiere la seguridad especificada por el tipo. Sin embargo, esto no es un escenario normal y podría indicar una necesidad de revisar cuidadosamente el diseño.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente utiliza los permisos de entorno para demostrar los peligros de infringir esta regla. En este ejemplo, el código de la aplicación crea una instancia del tipo protegido antes de denegar el permiso necesario para el tipo. En un escenario de amenazas del mundo real, la aplicación necesitaría otra manera de obtener una instancia del objeto.

 En el ejemplo siguiente, la biblioteca solicita permiso de escritura para un tipo y permiso de lectura para un método.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Ejemplo
 El siguiente código de aplicación muestra la vulnerabilidad de la biblioteca, aunque no cumple el requisito de seguridad de nivel de tipo llamando al método.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Este ejemplo produce el siguiente resultado:

 **[Todos los permisos] Información personal: 16/6/1964 12:00:00 A.M.**
 **[no tiene permiso de escritura (exigido por tipo)] Información Personal: 16/6/1964 12:00:00 A.M.**
 **[ningún permiso de lectura (exigido por método)] no pudo acceder a información personal: Error en la solicitud.**
## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [peticiones de herencias](http://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [peticiones de vínculos](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [datos y modelado](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
