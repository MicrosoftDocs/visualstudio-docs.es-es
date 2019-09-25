---
title: 'CA1063: Implementar IDisposable correctamente'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8b29c9ed644c223488261333e79f17229bd4b7a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235300"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementar IDisposable correctamente

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|Identificador de comprobación|CA1063|
|Categoría|Microsoft.Design|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

La <xref:System.IDisposable?displayProperty=nameWithType> interfaz no se ha implementado correctamente. Entre los posibles motivos se incluyen:

- <xref:System.IDisposable>se implementa en la clase.

- `Finalize`se reemplaza de nuevo.

- `Dispose()`se reemplaza.

- El `Dispose()` método no es público, [sellado](/dotnet/csharp/language-reference/keywords/sealed)o **Dispose**con nombre.

- `Dispose(bool)`no está protegido, es virtual o no está sellado.

- En los tipos no sellados `Dispose()` , debe `Dispose(true)`llamar a.

- En el caso de los tipos no `Finalize` sellados, la implementación no llama `Dispose(bool)` a ni a ni al finalizador de la clase base.

Una infracción de cualquiera de estos patrones desencadena una advertencia CA1063.

Cada tipo no sellado que declara e implementa la <xref:System.IDisposable> interfaz debe proporcionar su propio `protected virtual void Dispose(bool)` método. `Dispose()`debe llamar `Dispose(true)`a y el finalizador debe llamar `Dispose(false)`a. Si crea un tipo no sellado que declara e implementa la <xref:System.IDisposable> interfaz, debe definirla `Dispose(bool)` y llamarla. Para obtener más información, consulte [limpiar recursos no administrados (Guía de .net)](/dotnet/standard/garbage-collection/unmanaged) y [modelo de Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

De forma predeterminada, esta regla solo examina los tipos visibles externamente, pero esto es [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Todos <xref:System.IDisposable> los tipos deben implementar el [patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern) correctamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Examine el código y Determine cuál de las siguientes soluciones corregirá esta infracción:

- Quite <xref:System.IDisposable> de la lista de interfaces implementadas por el tipo y, en su lugar, invalide la implementación de Dispose de la clase base.

- Quite el finalizador del tipo, invalide Dispose (bool disposing) y coloque la lógica de finalización en la ruta de código donde ' disposing ' es false.

- Invalide Dispose (bool disposing) y coloque la lógica de Dispose en la ruta de código donde ' disposing ' es true.

- Asegúrese de que Dispose () se declara como Public y [Sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Cambie el nombre del método Dispose a **Dispose** y asegúrese de que se declara como Public y [Sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Asegúrese de que Dispose (bool) se declara como Protected, virtual y unsealed.

- Modifique Dispose () para que llame a Dispose (true) y <xref:System.GC.SuppressFinalize%2A> , a continuación, llame a`this`en la `Me` instancia de objeto actual (o en Visual Basic) y, a continuación, devuelva.

- Modifique el finalizador para que llame a Dispose (false) y, a continuación, devuelva.

- Si crea un tipo no sellado que declara e implementa la <xref:System.IDisposable> interfaz, asegúrese de que la implementación de <xref:System.IDisposable> sigue el patrón descrito anteriormente en esta sección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="configurability"></a>Configurabilidad

Si está ejecutando esta regla desde los [analizadores de FxCop](install-fxcop-analyzers.md) (y no con el análisis heredado), puede configurar en qué partes del código base ejecutar esta regla, según su accesibilidad. Por ejemplo, para especificar que la regla se debe ejecutar solo en la superficie de API no pública, agregue el siguiente par clave-valor a un archivo. editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Puede configurar esta opción solo para esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, vea [configurar analizadores de FxCop](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

El siguiente pseudocódigo proporciona un ejemplo general de cómo se debe implementar Dispose (bool) en una clase que use recursos administrados y nativos.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Vea también

- [Patrón Dispose (instrucciones de diseño de marco)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Limpiar recursos no administrados (Guía de .NET)](/dotnet/standard/garbage-collection/unmanaged)