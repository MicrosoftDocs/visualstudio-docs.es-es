---
title: Definir una directiva de bloqueo para crear segmentos de solo lectura
description: Obtenga información sobre cómo puede definir una directiva para que un programa bloquee parte o todo un modelo de lenguaje específico de dominio (DSL) para que se pueda leer pero no cambiar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385791"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definir una directiva de bloqueo para crear segmentos de solo lectura
La API de inmutabilidad del SDK de visualización y modelado de Visual Studio permite a un programa bloquear parte o todo un modelo de lenguaje específico de dominio (DSL) para que se pueda leer pero no cambiar. Esta opción de solo lectura podría usarse, por ejemplo, para que un usuario pueda pedir a sus compañeros que anoten y revisen un modelo DSL, pero que no les puedan permitir cambiar el original.

 Además, como autor de un DSL, puede definir una directiva *de bloqueo.* Una directiva de bloqueo define qué bloqueos se permiten, no se permiten o son obligatorios. Por ejemplo, al publicar un DSL, puede animar a los desarrolladores de terceros a ampliarlo con nuevos comandos. Pero también podría usar una directiva de bloqueo para evitar que modifiquen el estado de solo lectura de las partes especificadas del modelo.

> [!NOTE]
> Una directiva de bloqueo se puede eludir mediante reflexión. Proporciona un límite claro para desarrolladores de terceros, pero no proporciona seguridad segura.

 Puede encontrar más información y ejemplos en el sitio web Visual Studio SDK de [visualización y modelado.](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Configuración y obtención de bloqueos
 Puede establecer bloqueos en el almacén, en una partición o en un elemento individual. Por ejemplo, esta instrucción impedirá que se elimine un elemento de modelo y también impedirá que se cambien sus propiedades:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Se pueden usar otros valores de bloqueo para evitar cambios en las relaciones, la creación de elementos, el movimiento entre particiones y la reordenación de vínculos en un rol.

 Los bloqueos se aplican tanto a las acciones del usuario como al código del programa. Si el código del programa intenta realizar un cambio, `InvalidOperationException` se produce una excepción . Los bloqueos se omiten en una operación deshacer o rehacer.

 Puede detectar si un elemento tiene un bloqueo en un conjunto determinado mediante y puede obtener el conjunto actual de `IsLocked(Locks)` bloqueos en un elemento mediante `GetLocks()` .

 Puede establecer un bloqueo sin usar una transacción. La base de datos de bloqueo no forma parte del almacén. Si establece un bloqueo en respuesta a un cambio de un valor en el almacén, por ejemplo, en OnValueChanged, debe permitir los cambios que forman parte de una operación de deshacer.

 Estos métodos son métodos de extensión que se definen en el espacio de <xref:Microsoft.VisualStudio.Modeling.Immutability> nombres .

### <a name="locks-on-partitions-and-stores"></a>Bloqueos en particiones y almacenes
 Los bloqueos también se pueden aplicar a las particiones y al almacén. Un bloqueo que se establece en una partición se aplica a todos los elementos de la partición. Por lo tanto, por ejemplo, la siguiente instrucción impedirá que se eliminen todos los elementos de una partición, independientemente de los estados de sus propios bloqueos. No obstante, otros bloqueos como `Locks.Property` podrían establecerse en elementos individuales:

```csharp
partition.SetLocks(Locks.Delete);
```

 Un bloqueo que se establece en store se aplica a todos sus elementos, independientemente de la configuración de ese bloqueo en las particiones y los elementos.

### <a name="using-locks"></a>Uso de bloqueos
 Puede usar bloqueos para implementar esquemas como los ejemplos siguientes:

- No permitir cambios en todos los elementos y relaciones, excepto los que representan comentarios. Esto permite a los usuarios anotar un modelo sin cambiarlo.

- No permitir cambios en la partición predeterminada, pero permitir cambios en la partición del diagrama. El usuario puede reorganizar el diagrama, pero no puede modificar el modelo subyacente.

- No permitir cambios en store, excepto para un grupo de usuarios registrados en una base de datos independiente. Para otros usuarios, el diagrama y el modelo son de solo lectura.

- No permitir cambios en el modelo si una propiedad booleana del diagrama está establecida en true. Proporcione un comando de menú para cambiar esa propiedad. Esto ayuda a garantizar que los usuarios no realicen cambios accidentalmente.

- No permite la adición y eliminación de elementos y relaciones de clases concretas, pero permite cambios de propiedad. Esto proporciona a los usuarios un formulario fijo en el que pueden rellenar las propiedades.

## <a name="lock-values"></a>Valores de bloqueo
 Los bloqueos se pueden establecer en un elemento Store, Partition o ModelElement individual. Bloqueos es una `Flags` enumeración: puede combinar sus valores mediante "&#124;".

- Los bloqueos de modelelement siempre incluyen los bloqueos de su partición.

- Los bloqueos de una partición siempre incluyen los bloqueos del almacén.

  No se puede establecer un bloqueo en una partición o un almacén y, al mismo tiempo, deshabilitar el bloqueo en un elemento individual.

|Valor|Significado si `IsLocked(Value)` es true|
|-|-|
|Ninguno|Sin restricciones.|
|Propiedad|No se pueden cambiar las propiedades de dominio de los elementos. Esto no se aplica a las propiedades generadas por el rol de una clase de dominio en una relación.|
|Sumar|No se pueden crear nuevos elementos ni vínculos en una partición o un almacén.<br /><br /> No es aplicable a `ModelElement` .|
|Move|El elemento no se puede mover entre particiones `element.IsLocked(Move)` si es true o si es `targetPartition.IsLocked(Move)` true.|
|Eliminar|No se puede eliminar un elemento si este bloqueo se establece en el propio elemento o en cualquiera de los elementos a los que se propagaría la eliminación, como elementos incrustados y formas.<br /><br /> Puede usar `element.CanDelete()` para detectar si se puede eliminar un elemento.|
|Reordenar|No se puede cambiar el orden de los vínculos en un reproductor de roles.|
|RolePlayer|No se puede cambiar el conjunto de vínculos que tienen como origen este elemento. Por ejemplo, los nuevos elementos no se pueden incrustar debajo de este elemento. Esto no afecta a los vínculos para los que este elemento es el destino.<br /><br /> Si este elemento es un vínculo, su origen y destino no se ven afectados.|
|Todo|OR bit a bit de los demás valores.|

## <a name="locking-policies"></a>Directivas de bloqueo
 Como autor de un DSL, puede definir una directiva *de bloqueo*. Una directiva de bloqueo modera el funcionamiento de SetLocks(), para que pueda evitar que se establezcan bloqueos específicos o exige que se establezcan bloqueos específicos. Normalmente, usaría una directiva de bloqueo para desaconsecer a los usuarios o desarrolladores que infringan accidentalmente el uso previsto de un DSL, de la misma manera que se puede declarar una variable `private` .

 También puede usar una directiva de bloqueo para establecer bloqueos en todos los elementos dependientes del tipo del elemento. Esto se debe a `SetLocks(Locks.None)` que siempre se llama a cuando se crea o deserializa un elemento a partir del archivo por primera vez.

 Sin embargo, no puede usar una directiva para variar los bloqueos de un elemento durante su vida útil. Para lograr ese efecto, debe usar llamadas a `SetLocks()` .

 Para definir una directiva de bloqueo, debe:

- Cree una clase que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Agregue esta clase a los servicios que están disponibles a través de DocData del DSL.

### <a name="to-define-a-locking-policy"></a>Para definir una directiva de bloqueo
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> tiene la siguiente definición:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Se llama a estos métodos cuando se realiza una llamada `SetLocks()` a en un elemento Store, Partition o ModelElement. En cada método, se le proporciona un conjunto propuesto de bloqueos. Puede devolver el conjunto propuesto o puede agregar y restar bloqueos.

 Por ejemplo:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Para asegurarse de que los usuarios siempre pueden eliminar elementos, incluso si otros códigos llaman a `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Para no permitir el cambio en todas las propiedades de cada elemento de MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Para que la directiva esté disponible como servicio
 En el `DslPackage` proyecto, agregue un nuevo archivo que contenga código similar al ejemplo siguiente:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
