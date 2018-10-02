---
title: Definir una directiva de bloqueo para crear segmentos de solo lectura
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6567be5a82d4b344b3850a1a66e0b5b23f1b8f9d
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859099"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definir una directiva de bloqueo para crear segmentos de solo lectura
La API de inmutabilidad del SDK de modelado y visualización de Visual Studio permite que un programa bloquear la totalidad o parte de un modelo de lenguaje específico de dominio (DSL) para que se pueden leer pero no cambia. Podría usar esta opción de solo lectura, por ejemplo, para que un usuario puede pedir a sus compañeros para anotar y revisar un modelo DSL pero puede no puedan cambiar el original.

 Además, como autor de un DSL, puede definir un *directiva de bloqueo.* Una directiva de bloqueo define los bloqueos que son obligatorios, no se permite o permitidos. Por ejemplo, cuando se publica un DSL, puede animar a los desarrolladores de terceros para ampliarlo con nuevos comandos. Pero también podría usar una directiva de bloqueo para impedir que modificar el estado de solo lectura de las partes especificadas del modelo.

> [!NOTE]
>  Una directiva de bloqueo puede evitarse mediante la reflexión. Proporciona un límite claro para los desarrolladores de terceros, pero no proporcionan una gran seguridad.

 Más información y ejemplos están disponibles en Visual Studio [SDK de visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) sitio Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Establecer y obtener bloqueos
 Puede establecer los bloqueos en el almacén, en una partición o en un elemento individual. Por ejemplo, esta instrucción impedirá que un elemento de modelo que se va a eliminar y también impedirá que sus propiedades que se va a cambiar:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Otros valores de bloqueo se pueden usar para impedir cambios en las relaciones, la creación del elemento, movimiento entre particiones y volver a ordenación vínculos en un rol.

 Los bloqueos se aplican tanto a código de programa a las acciones del usuario. Si el código de programa intenta realizar un cambio, un `InvalidOperationException` se iniciará. Se omiten los bloqueos en una operación de deshacer o rehacer.

 Puede detectar si un elemento tiene un ningún bloqueo en un conjunto determinado mediante el uso de `IsLocked(Locks)` y puede obtener el conjunto actual de bloqueos en un elemento mediante `GetLocks()`.

 Puede establecer un bloqueo sin utilizar una transacción. La base de datos de bloqueo no forma parte de la tienda. Si establece un bloqueo en respuesta a un cambio de un valor en el almacén, por ejemplo en OnValueChanged, debe permitir los cambios que forman parte de una operación de deshacer.

 Estos métodos son métodos de extensión que se definen en el <xref:Microsoft.VisualStudio.Modeling.Immutability> espacio de nombres.

### <a name="locks-on-partitions-and-stores"></a>Bloqueos en las particiones y almacenes
 Los bloqueos también pueden aplicarse a las particiones y el almacén. Un bloqueo que se establece en una partición se aplica a todos los elementos de la partición. Por lo tanto, por ejemplo, la siguiente instrucción impedirá todos los elementos de una partición que se va a eliminar, con independencia de los Estados de sus propios bloqueos. No obstante, otros bloqueos como `Locks.Property` puede establecerse en elementos individuales:

```csharp
partition.SetLocks(Locks.Delete);
```

 Un bloqueo que se establece en el Store se aplica a todos sus elementos, independientemente de la configuración de dicho bloqueo en las particiones y los elementos.

### <a name="using-locks"></a>Usar bloqueos
 Puede usar bloqueos para implementar esquemas como los ejemplos siguientes:

-   No permitir cambios en todos los elementos y relaciones, excepto aquellos que representan los comentarios. Esto permite a los usuarios anotar un modelo sin cambiarlo.

-   No permitir cambios en la partición predeterminada, pero permitir que los cambios en la partición de diagrama. El usuario puede reorganizar el diagrama, pero no puede modificar el modelo subyacente.

-   No permitir cambios en el Store excepto para un grupo de usuarios que están registrados en una base de datos independiente. Para otros usuarios, el diagrama de modelo son de solo lectura.

-   No permitir cambios en el modelo si se establece una propiedad booleana del diagrama en true. Proporcione un comando de menú para cambiar esa propiedad. Esto ayuda a garantizar que los usuarios que no hagan cambios accidentalmente.

-   No permitir la adición y eliminación de elementos y relaciones de determinadas clases, pero permitir que los cambios de propiedad. Esto proporciona a los usuarios un formulario fijo en el que pueden rellenar las propiedades.

## <a name="lock-values"></a>Valores de bloqueo
 Los bloqueos se pueden establecer en Store, partición o ModelElement individual. Bloqueos es un `Flags` enumeración: puede combinar sus valores mediante '&#124;'.

-   Bloqueos de un objeto ModelElement siempre incluyen los bloqueos de su partición.

-   Bloqueos de una partición siempre incluyen los bloqueos de la Store.

 No se puede establecer un bloqueo en una partición o almacenar y al mismo tiempo, deshabilite el bloqueo en un elemento individual.

|Valor|Lo que significa que si `IsLocked(Value)` es true|
|-----------|------------------------------------------|
|Ninguna|Sin restricción.|
|Property|No se puede cambiar las propiedades de dominio de elementos. Esto no es aplicable a las propiedades que se generan mediante la función de una clase de dominio en una relación.|
|Add|No se puede crear nuevos elementos y vínculos en una partición o almacenar.<br /><br /> No se aplica a `ModelElement`.|
|Mover|Elemento no puede moverse entre las particiones si `element.IsLocked(Move)` es true, o si `targetPartition.IsLocked(Move)` es true.|
|Eliminar|No se puede eliminar un elemento si este bloqueo se establece en el propio elemento, o en cualquiera de los elementos a la que podría propagar la eliminación, como las formas y elementos incrustados.<br /><br /> Puede usar `element.CanDelete()` para detectar si se puede eliminar un elemento.|
|Volver a ordenar|No se puede cambiar el orden de vínculos en un encargado de rol.|
|Encargado de rol|No se puede cambiar el conjunto de vínculos que se obtienen en este elemento. Por ejemplo, no se puede incrustar elementos nuevos en este elemento. Esto no afecta a los vínculos para que este elemento es el destino.<br /><br /> Si este elemento es un vínculo, su origen y destino no se ven afectados.|
|Todas|Operación OR bit a bit de los demás valores.|

## <a name="locking-policies"></a>Directivas de bloqueos
 Como autor de un DSL, puede definir un *directiva de bloqueo*. Una directiva de bloqueo modera la operación de SetLocks(), por lo que puede impedir que los bloqueos específicos que se va a establecer o exigir que se deben establecer bloqueos específicos. Normalmente, usaría una directiva de bloqueo para impedir que los usuarios o a los desarrolladores de cometen accidentalmente el uso previsto de un DSL, de la misma manera que puede declarar una variable `private`.

 También puede usar una directiva de bloqueo para establecer bloqueos en todos los elementos dependientes en el tipo del elemento. Esto es porque `SetLocks(Locks.None)` siempre se llama cuando un elemento en primer lugar se crea o se deserializan desde el archivo.

 Sin embargo, no se puede usar una directiva para variar los bloqueos en un elemento durante su vida. Para lograr este efecto, debe utilizar llamadas a `SetLocks()`.

 Para definir una directiva de bloqueo, tendrá que:

-   Cree una clase que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

-   Agregar esta clase a los servicios que están disponibles a través de DocData de su DSL.

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

 Estos métodos se invocan cuando se realiza una llamada a `SetLocks()` en Store, partición o ModelElement. En cada método, se proporcionan con un conjunto de bloqueos propuesto. Puede devolver el conjunto de propuestas, o puede agregar y sustraer bloqueos.

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

 Para asegurarse de que los usuarios siempre pueden eliminar elementos, incluso si llama otro código `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Para no permitir cambios en todas las propiedades de todos los elementos de MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Para que la directiva esté disponible como un servicio
 En su `DslPackage` del proyecto, agregue un nuevo archivo que contiene código que es similar al siguiente:

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
