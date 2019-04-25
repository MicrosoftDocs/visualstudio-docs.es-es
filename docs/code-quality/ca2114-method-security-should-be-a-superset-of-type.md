---
title: 'CA2114: La seguridad del método debe ser un supraconjunto del tipo'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 623416e557759ace1ad6403ef8ef977df01da39e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911135"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114: La seguridad del método debe ser un supraconjunto del tipo

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|Identificador de comprobación|CA2114|
|Categoría|Microsoft.Security|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo tiene seguridad declarativa y uno de sus métodos tiene seguridad declarativa para la misma acción de seguridad y la acción de seguridad no es [peticiones de vínculo](/dotnet/framework/misc/link-demands), y los permisos comprobados por el tipo no son un subconjunto de los permisos comprueba el método.

## <a name="rule-description"></a>Descripción de la regla
 Un método no debe tener tanto un seguridad declarativa de nivel de método y el nivel de tipo para la misma acción. No se combinan las dos comprobaciones; se aplica solo a la demanda de nivel de método. Por ejemplo, si un tipo solicita permiso `X`, y uno de sus métodos solicita permiso `Y`, código no tiene que tener el permiso `X` para ejecutar el método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Revise el código para asegurarse de que ambas acciones son necesarias. Si se requieren ambas acciones, debe asegurarse de que la acción de nivel de método incluye la seguridad especificada en el nivel de tipo. Por ejemplo, si el tipo solicita permiso `X`, y su método también debe solicitar permiso `Y`, debe solicitar explícitamente el método `X` y `Y`.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el método no requiere la seguridad especificada por el tipo. Sin embargo, esto no es un escenario normal y podría indicar una necesidad de revisar cuidadosamente el diseño.

## <a name="example-1"></a>Ejemplo 1

El ejemplo siguiente utiliza los permisos de entorno para demostrar los peligros de infringir esta regla. En este ejemplo, el código de la aplicación crea una instancia del tipo protegido antes de denegar el permiso necesario para el tipo. En un escenario de amenazas del mundo real, la aplicación necesitaría otra manera de obtener una instancia del objeto.

En el ejemplo siguiente, la biblioteca solicita permiso de escritura para un tipo y permiso de lectura para un método.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Ejemplo 2

El siguiente código de aplicación muestra la vulnerabilidad de la biblioteca, aunque no cumple el requisito de seguridad de nivel de tipo llamando al método.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Este ejemplo produce el siguiente resultado:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Vea también

- [Instrucciones de codificación segura](/dotnet/standard/security/secure-coding-guidelines)
- [Peticiones de vínculo](/dotnet/framework/misc/link-demands)
- [Datos y modelado](/dotnet/framework/data/index)