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
ms.openlocfilehash: f1b2c5b447d796ddd2098a6500b6094478fcd8b9
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842008"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implementar IDisposable correctamente

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|Identificador de comprobación|CA1063|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

El <xref:System.IDisposable?displayProperty=nameWithType> interfaz no se implementa correctamente. Posibles razones para esto incluyen:

- <xref:System.IDisposable> se vuelva a implementar en la clase.

- Finalizar se reoverridden.

- Dispose() se reemplaza.

- No es público, el método Dispose() [sealed](/dotnet/csharp/language-reference/keywords/sealed), o con nombre **Dispose**.

- Dispose (bool) no está protegido, virtual o sin sellar.

- En tipos no sellados, Dispose() debe llamar a Dispose (true).

- Para tipos no sellados, la implementación Finalize no llama a uno o ambos Dispose (bool) o el finalizador de la clase base.

Infracción de cualquiera de estos patrones desencadena la advertencia CA1063.

Cada tipo no sellado que declara e implementa el <xref:System.IDisposable> interfaz debe proporcionar su propio `protected virtual void Dispose(bool)` método. `Dispose()` debe llamar a `Dipose(true)`, y el finalizador debe llamar a `Dispose(false)`. Si crea un tipo no sellado que declara e implementa el <xref:System.IDisposable> interfaz, debe definir `Dispose(bool)` y llamarlo. Para obtener más información, consulte [limpiar recursos no administrados (Guía de. NET)](/dotnet/standard/garbage-collection/unmanaged) y [patrón Dispose](/dotnet/standard/design-guidelines/dispose-pattern).

De forma predeterminada, esta regla busca solo en tipos visibles externamente, pero se trata de [configurable](#configurability).

## <a name="rule-description"></a>Descripción de la regla

Todos los <xref:System.IDisposable> tipos deben implementar la [patrón Dispose](/dotnet/standard/design-guidelines/dispose-pattern) correctamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Examine el código y determinar cuál de las siguientes resoluciones corregirá esta infracción:

- Quitar <xref:System.IDisposable> en la lista de interfaces que se implementan por su tipo y anular la implementación de Dispose de clase base en su lugar.

- Quite el finalizador del tipo, invalide Dispose (bool disposing) y coloque la lógica de finalización en la ruta de acceso del código donde 'disposing' es false.

- Reemplace Dispose (bool disposing) y coloque la lógica de dispose en la ruta de acceso del código donde 'disposing' es true.

- Asegúrese de que Dispose() se ha declarado como público y [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Cambiar el nombre del método dispose para **Dispose** y asegúrese de que se declara como público y [sealed](/dotnet/csharp/language-reference/keywords/sealed).

- Asegúrese de que Dispose (bool) se declara como protegido, virtual y no sellados.

- Modificar Dispose() para que llame a Dispose (true), a continuación, llama a <xref:System.GC.SuppressFinalize%2A> en la instancia del objeto actual (`this`, o `Me` en Visual Basic) y, a continuación, se devuelve.

- Modifique el finalizador para que se llama a Dispose (false) y, a continuación, se devuelve.

- Si crea un tipo no sellado que declara e implementa el <xref:System.IDisposable> interfaz, asegúrese de que la implementación de <xref:System.IDisposable> sigue el patrón descrito anteriormente en esta sección.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="configurability"></a>Capacidad de configuración

Si ejecuta esta regla de [analizadores de FxCop](install-fxcop-analyzers.md) (y no a través de análisis de código estático), puede configurar qué partes de su código base para ejecutar esta regla en, en función de su accesibilidad. Por ejemplo, para especificar que debe ejecutarse la regla sólo con respecto a la superficie de API no públicos, agregue el siguiente par clave-valor a un archivo .editorconfig en el proyecto:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Puede configurar esta opción para simplemente esta regla, para todas las reglas o para todas las reglas de esta categoría (diseño). Para obtener más información, consulte [analizadores de FxCop configurar](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

El pseudocódigo siguiente proporciona un ejemplo general de cómo se debe implementar Dispose (bool) en una clase que utiliza managed y recursos nativos.

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

- [(Instrucciones de diseño de framework) del patrón de Dispose](/dotnet/standard/design-guidelines/dispose-pattern)
- [Limpiar recursos no administrados (Guía de. NET)](/dotnet/standard/garbage-collection/unmanaged)