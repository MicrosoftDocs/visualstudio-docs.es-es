---
title: 'CA2114: La seguridad del método debería ser un supraconjunto del tipo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d2fc6fb60dd837dd93de1db2758ee0e2c216850
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914957"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La seguridad del método debería ser un supraconjunto del tipo
|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|Identificador de comprobación|CA2114|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene seguridad declarativa y uno de sus métodos dispone de seguridad declarativa para la misma acción de seguridad y la acción de seguridad no es [peticiones de vínculo](/dotnet/framework/misc/link-demands), y los permisos comprobados por el tipo no son un subconjunto de los permisos comprobados por el método.

## <a name="rule-description"></a>Descripción de la regla
 Un método no debe tener tanto un seguridad declarativa de nivel de método y de tipo para la misma acción. No se combinan las dos comprobaciones; se aplica solo a la demanda de nivel de método. Por ejemplo, si un tipo solicita permiso `X`, y uno de sus métodos solicita permiso `Y`, código no tiene que tener el permiso `X` para ejecutar el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise el código para asegurarse de que ambas acciones son necesarias. Si ambas acciones se necesitan, asegúrese de que la acción de nivel de método incluye la seguridad especificada en el nivel de tipo. Por ejemplo, si el tipo solicita permiso `X`, y su método también debe solicitar permiso `Y`, el método debe solicitar explícitamente `X` y `Y`.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el método no necesita la seguridad especificada por el tipo. Sin embargo, esto no es un escenario común y podría indicar una necesidad de revisar cuidadosamente el diseño.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se usa permisos de entorno para demostrar los peligros de infringir esta regla. En este ejemplo, el código de la aplicación crea una instancia del tipo protegido antes de denegar el permiso necesario para el tipo. En un escenario de amenazas del mundo real, la aplicación necesitaría otra manera de obtener una instancia del objeto.

 En el ejemplo siguiente, la biblioteca solicita permiso de escritura para un tipo y permiso de lectura para un método.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example"></a>Ejemplo
 El código de aplicación siguiente muestra la vulnerabilidad de la biblioteca llamando al método aunque no cumple el requisito de seguridad de nivel de tipo.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

 Este ejemplo produce el siguiente resultado:

 **[Todos los permisos] Información personal: 16/6/1964 12:00:00 A.M.**
 **[ningún permiso de escritura (exigido por tipo)] Información Personal: 16/6/1964 12:00:00 A.M.**
 **[ya No leer (permiso solicitado por método]) no se pudo obtener acceso a información personal: error en la solicitud.**
## <a name="see-also"></a>Vea también
 [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines) [las peticiones de vínculo](/dotnet/framework/misc/link-demands) [datos y modelado](/dotnet/framework/data/index)