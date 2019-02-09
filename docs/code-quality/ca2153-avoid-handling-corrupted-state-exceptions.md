---
title: 'CA2153: Evitar el control de excepciones de estado dañadas'
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3e8253936c406a3f84304337b818e0f28f1036f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950908"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar el control de excepciones de estado dañadas

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|Identificador de comprobación|CA2153|
|Categoría|Microsoft.Security|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Las[excepciones de estado dañado (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) indican que la memoria está dañada en el proceso. Detectar estos problemas y evitar el bloqueo del proceso puede provocar vulnerabilidades de seguridad si un atacante puede colocar una vulnerabilidad de seguridad en la región de memoria dañada.

## <a name="rule-description"></a>Descripción de la regla

CSE indica que el estado de un proceso se ha dañado y el sistema no lo ha detectado. En el escenario de estado dañado, un controlador general solo detecta la excepción si se marca el método con el atributo `HandleProcessCorruptedStateExceptions` correcto. De forma predeterminada, [Common Language Runtime (CLR)](/dotnet/standard/clr) no invocará controladores catch de CSE.

Permitir el bloqueo del proceso sin detectar estos tipos de excepciones es la opción más segura, ya que incluso el registro del código puede permitir a los atacantes aprovechar errores de memoria dañada.

Esta advertencia se desencadena cuando se detectan CSE con un controlador general que detecta todas las excepciones, como catch (excepción) o catch (sin especificación de excepción).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para resolver esta advertencia, realice una de las siguientes acciones:

- Quite el atributo `HandleProcessCorruptedStateExceptions`. Esto revierte el comportamiento de tiempo de ejecución predeterminado en el que las CSE no se pasan a los controladores catch.

- Quite el controlador catch general y use controladores que capturen tipos de excepción específicos. Esto puede incluir CSE suponiendo que el código del controlador puede controlarlas de manera segura (poco frecuente).

- Vuelva a producir el CSE en el controlador catch, lo que garantiza la excepción se pasa al autor de llamada y dará como resultado la finalización del proceso de ejecución.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

### <a name="violation"></a>Infracción

El pseudocódigo siguiente muestra el patrón que detecta esta regla.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method to handle and log CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
    }
}
```

### <a name="solution-1"></a>Solución 1

Quitar el atributo HandleProcessCorruptedExceptions garantiza que las excepciones no se controlarán.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-2"></a>Solución 2

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
        // Handle error.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error.
    }
}
```

### <a name="solution-3"></a>Solución 3

Vuelva a producir la excepción.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error.
        throw;
    }
}
```