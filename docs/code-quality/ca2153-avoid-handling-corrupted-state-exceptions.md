---
title: Reglas de análisis de código CA2153 para excepciones de estado dañadas
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542162"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar el control de excepciones de estado dañadas

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|Identificador de comprobación|CA2153|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

[Excepciones de estado dañadas (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indican que la memoria dañada en el proceso. Detectar estos problemas y evitar el bloqueo del proceso puede provocar vulnerabilidades de seguridad si un atacante puede colocar una vulnerabilidad de seguridad en la región de memoria dañada.

## <a name="rule-description"></a>Descripción de la regla

CSE indica que el estado de un proceso se ha dañado y el sistema no lo ha detectado. En el escenario de estado dañado, un controlador general solo detecta la excepción si marca el método con el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> atributo. De forma predeterminada, el [Common Language Runtime (CLR)](/dotnet/standard/clr) no invoca controladores catch de CSE.

La opción más segura es permitir el bloqueo del proceso sin detectar estos tipos de excepciones. Incluso el registro del código puede permitir que los atacantes aprovechar errores de memoria dañada.

Esta advertencia se desencadena cuando se detectan CSE con un controlador general que detecta todas las excepciones, por ejemplo, `catch (System.Exception e)` o `catch` con ningún parámetro de excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para resolver esta advertencia, realice una de las siguientes acciones:

- Quite el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Esto revierte el comportamiento de tiempo de ejecución predeterminado en el que las CSE no se pasan a los controladores catch.

- Quite el controlador catch general y use controladores que capturen tipos de excepción específicos. Esto puede incluir CSE, suponiendo que el código del controlador puede controlarlas de manera segura (poco frecuente).

- Vuelva a producir el CSE en el controlador catch, que pasa la excepción al autor de llamada y debe tener como resultado la finalización del proceso de ejecución.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

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

Quitar el <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atributo garantiza que las excepciones de estado dañado no administradas por el método.

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

### <a name="solution-2---catch-specific-exceptions"></a>Solución 2: detectar excepciones específicas

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

### <a name="solution-3---rethrow"></a>Solución 3: rethrow

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