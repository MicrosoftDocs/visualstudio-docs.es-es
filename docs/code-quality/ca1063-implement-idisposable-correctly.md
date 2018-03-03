---
title: 'CA1063: Implemente IDisposable correctamente | Documentos de Microsoft'
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 29a2fbb82fd2795c675bfa249e213488913745a9
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/02/2018
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implemente IDisposable correctamente

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|Identificador de comprobación|CA1063|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo

`IDisposable` no se implementa correctamente. A continuación se enumeran algunas causas de este problema:

- IDisposable se implementa de nuevo en la clase.

- Finalizar se vuelve a reemplazar.

- Se reemplaza Dispose.

- Dispose() no es público, sealed o denominado Dispose.

- Dispose (bool) no está protegido, virtual o no sellado.

- En tipos no sellados, Dispose() debe llamar a Dispose (true).

- Para los tipos no sellados, la implementación de finalización no llama a uno o ambos Dispose (bool) o el finalizador de la clase de caso.

Infracción de cualquiera de estos patrones desencadenará esta advertencia.

Todos los tipos no sellados que declaran e implementa la interfaz IDisposable deben proporcionar su propio método Dispose (bool) void virtual protegido. Dispose() debe llamar a Dispose (true) y Finalize debe llamar a Dispose (false). Si va a crear un tipo no sellado que declara e implementa la interfaz IDisposable, debe definir Dispose (bool) y llamarlo. Para obtener más información, consulte [limpiar recursos no administrados](/dotnet/standard/garbage-collection/unmanaged) en el [directrices de diseño de .NET Framework](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Descripción de la regla

Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Examine el código y determinar cuál de las siguientes resoluciones corregirá esta infracción.

- Quite IDisposable de la lista de interfaces que se implementan en {0} y reemplazar la implementación de Dispose de clase base en su lugar.

- Quite el finalizador del tipo {0}, invalide Dispose (colocación de bool) y coloque la lógica de finalización en la ruta de acceso del código donde 'desechar' es false.

- Quitar {0}, invalide Dispose (colocación de bool) y coloque la lógica de dispose en la ruta de acceso del código donde 'desechar' es true.

- Asegúrese de que {0} se declaró como public y sealed.

- Cambiar el nombre de {0} a 'Dispose' y asegúrese de que se declara como public y sealed.

- Asegúrese de que ese {0} se declara como protegido, virtual y no sellado.

- Modificar {0} para que llama a Dispose (true), a continuación, llame a GC. SuppressFinalize en la instancia del objeto actual ('this' o 'Me' en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) y, a continuación, se devuelve.

- Modificar {0} para que se llama a Dispose (false) y, a continuación, se devuelve.

- Si va a crear un tipo no sellado que declara e implementa la interfaz IDisposable, asegúrese de que la implementación de IDisposable sigue el patrón descrito anteriormente en esta sección.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo

El pseudocódigo siguiente proporciona un ejemplo general de cómo se debe implementar Dispose (bool) en una clase que utiliza administrada y recursos nativos.

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
    // own unmanaged resources itself, but leave the other methods
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