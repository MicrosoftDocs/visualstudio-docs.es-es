---
title: 'CA1063: Implemente IDisposable correctamente | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94d13514800bac80723031c6bba7920d28ac83e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877301"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implemente IDisposable correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|Identificador de comprobación|CA1063|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 `IDisposable` no se implementa correctamente. Algunas de las razones para este problema son las siguientes:

- IDisposable se implementa de nuevo en la clase.

- Finalizar se vuelve a reemplazar.

- Se invalida a Dispose.

- Dispose() no es público, sellado o denominado Dispose.

- Dispose (bool) no está protegido, virtual o sin sellar.

- En tipos no sellados, Dispose() debe llamar a Dispose (true).

- Para tipos no sellados, la implementación Finalize no llama a uno o ambos Dispose (bool) o el finalizador de la clase de caso.

  Infracción de cualquiera de estos patrones desencadenará esta advertencia.

  Cada tipo IDisposable de raíz no sellada debe proporcionar su propio método Dispose (bool) void virtual protegido. Dispose() debe llamar a Dispose (true) y Finalize debe llamar a Dispose (false). Si va a crear un tipo IDisposable de raíz no sellada, debe definir Dispose (bool) y llamarlo. Para obtener más información, consulte [limpiar recursos no administrados](http://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) en el [instrucciones de diseño de Framework](http://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) sección de la documentación de .NET Framework.

## <a name="rule-description"></a>Descripción de la regla
 Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Examine el código y determinar cuál de las siguientes resoluciones corregirá esta infracción.

-   Quite IDisposable de la lista de interfaces implementadas por {0} e invalidar la implementación de Dispose de clase base en su lugar.

-   Quite el finalizador del tipo {0}, invalide Dispose (bool disposing) y coloque la lógica de finalización en la ruta de acceso del código donde 'disposing' es false.

-   Quitar {0}, invalide Dispose (bool disposing) y coloque la lógica de dispose en la ruta de acceso del código donde 'disposing' es true.

-   Asegúrese de que {0} está declarado como público y sellado.

-   Cambiar el nombre {0} a 'Dispose' y asegúrese de que se declara como public y sealed.

-   Asegúrese de que {0} se declaró como protegido, virtual y no sellados.

-   Modificar {0} para que llame a Dispose (true), a continuación, llama a GC. SuppressFinalize en la instancia del objeto actual ('this' o 'Me' en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) y, a continuación, se devuelve.

-   Modificar {0} para que se llama a Dispose (false) y, a continuación, se devuelve.

-   Si está escribiendo una clase IDisposable de raíz no sellada, asegúrese de que la implementación de IDisposable sigue el patrón descrito anteriormente en esta sección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo
 El pseudocódigo siguiente proporciona un ejemplo general de cómo se debe implementar Dispose (bool) en una clase que utiliza managed y recursos nativos.

```
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



