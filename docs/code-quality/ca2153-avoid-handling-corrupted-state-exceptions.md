---
title: Regla de análisis de código CA2153 para las excepciones de estado dañado
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0179a9609907adc07dc6d8a085eb9a2a0c38c065
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253222"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar el control de excepciones de estado dañadas

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|Identificador de comprobación|CA2153|
|Categoría|Microsoft.Security|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Las [excepciones de estado dañadas (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indican que hay daños en la memoria en el proceso. Detectar estos problemas y evitar el bloqueo del proceso puede provocar vulnerabilidades de seguridad si un atacante puede colocar una vulnerabilidad de seguridad en la región de memoria dañada.

## <a name="rule-description"></a>Descripción de la regla

CSE indica que el estado de un proceso se ha dañado y el sistema no lo ha detectado. En el escenario de estado dañado, un controlador general solo detecta la excepción si se marca el método con el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atributo. De forma predeterminada, [Common Language Runtime (CLR)](/dotnet/standard/clr) no invoca controladores catch para CSE.

La opción más segura consiste en permitir que el proceso se bloquee sin detectar estos tipos de excepciones. Incluso el código de registro puede permitir a los atacantes aprovechar errores de memoria dañados.

Esta advertencia se desencadena cuando se detectan CSE con un controlador general que detecta todas las excepciones, por ejemplo `catch (System.Exception e)` , `catch` o sin ningún parámetro de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para resolver esta advertencia, realice una de las acciones siguientes:

- Quite el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Esto revierte al comportamiento predeterminado en tiempo de ejecución, donde las CSE no se pasan a los controladores Catch.

- Quite el controlador catch general y use controladores que capturen tipos de excepción específicos. Esto puede incluir CSE, suponiendo que el código del controlador puede controlarlos de forma segura (poco frecuente).

- Vuelva a iniciar el CSE en el controlador Catch, que pasa la excepción al autor de la llamada y debe dar como resultado el final del proceso en ejecución.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

### <a name="violation"></a>Infracción

El pseudocódigo siguiente muestra el patrón que detecta esta regla.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>Solución 1: quitar el atributo

Al quitar <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> el atributo se garantiza que el método no controla las excepciones de estado dañado.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>Solución 2: detección de excepciones específicas

Quite el controlador catch general y detecte solo los tipos determinados de excepción.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>Solución 3: reinicio

Vuelva a producir la excepción.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```