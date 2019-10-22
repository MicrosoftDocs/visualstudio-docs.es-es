---
title: 'CA1063: implemente IDisposable correctamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fe2982ab9e1b3951583b268eadb44c97c8e4805
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663631"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: Implemente IDisposable correctamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|Identificador de comprobación|CA1063|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 `IDisposable` no se ha implementado correctamente. A continuación se enumeran algunas de las razones para este problema:

- IDisposable se vuelve a implementar en la clase.

- Finalize se vuelve a reemplazar.

- Dispose se invalida.

- Dispose () no es público, sellado o Dispose con nombre.

- Dispose (bool) no está protegido, virtual o no sellado.

- En los tipos no sellados, Dispose () debe llamar a Dispose (true).

- En el caso de los tipos no sellados, la implementación de finalización no llama a ni a Dispose (bool) o al finalizador de la clase Case.

  Una infracción de cualquiera de estos patrones desencadenará esta advertencia.

  Cada tipo IDisposable de raíz no sellado debe proporcionar su propio método protegido virtual void Dispose (bool). Dispose () debe llamar a Dispose (true) y Finalize debe llamar a Dispose (false). Si va a crear un tipo IDisposable raíz no sellado, debe definir Dispose (bool) y llamarlo. Para obtener más información, vea [limpiar recursos no administrados](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) en la sección [directrices de diseño del marco](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) de la documentación de .NET Framework.

## <a name="rule-description"></a>Descripción de la regla
 Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Examine el código y Determine cuál de las siguientes soluciones corregirá esta infracción.

- Quite IDisposable de la lista de interfaces implementadas por {0} e invalide la implementación de Dispose de clase base en su lugar.

- Quite el finalizador del tipo {0}, invalide Dispose (bool disposing) y coloque la lógica de finalización en la ruta de acceso del código donde "disposing" es false.

- Quite {0}, invalide Dispose (bool disposing) y coloque la lógica de Dispose en la ruta de código donde ' disposing ' es true.

- Asegúrese de que {0} se declara como Public y Sealed.

- Cambie el nombre de {0} a ' Dispose ' y asegúrese de que se declara como público y sellado.

- Asegúrese de que {0} se declara como protegido, virtual y sin sellar.

- Modifique {0} para que llame a Dispose (true) y, a continuación, llame a GC. SuppressFinalize en la instancia de objeto actual (' this ' o ' me ' en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) y, a continuación, devuelve.

- Modifique {0} para que llame a Dispose (false) y, a continuación, devuelva.

- Si está escribiendo una clase IDisposable raíz no sellada, asegúrese de que la implementación de IDisposable siga el patrón descrito anteriormente en esta sección.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo
 El siguiente pseudocódigo proporciona un ejemplo general de cómo se debe implementar Dispose (bool) en una clase que use recursos administrados y nativos.

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
