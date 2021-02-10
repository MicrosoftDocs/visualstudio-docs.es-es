---
title: Definir una directiva de bloqueo para crear segmentos de solo lectura
description: Obtenga información acerca de cómo puede definir una directiva para que un programa bloquee parte de un modelo de lenguaje específico del dominio (DSL), o todo, para que se pueda leer pero no cambiar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aa7590689b4d7acdb7a7ebe501584ed6a8bd41bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935422"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definir una directiva de bloqueo para crear segmentos de solo lectura
La API de inmutabilidad del SDK de visualización y modelado de Visual Studio permite a un programa bloquear parte o todo un modelo de lenguaje específico de dominio (DSL) para que se pueda leer pero no cambiar. Esta opción de solo lectura se puede usar, por ejemplo, para que un usuario pueda pedir a los compañeros que anoten y revisen un modelo DSL, pero que no puedan cambiar el original.

 Además, como autor de un DSL, puede definir una directiva de *bloqueo.* Una directiva de bloqueo define qué bloqueos se permiten, no se permiten o son obligatorios. Por ejemplo, al publicar un DSL, puede animar a los desarrolladores de terceros a que lo extiendan con nuevos comandos. Pero también puede usar una directiva de bloqueo para evitar que modifiquen el estado de solo lectura de las partes especificadas del modelo.

> [!NOTE]
> Se puede eludir una directiva de bloqueo mediante la reflexión. Proporciona un límite claro a los desarrolladores de terceros, pero no proporciona seguridad segura.

 Puede encontrar más información y ejemplos en el sitio web del [SDK de visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) de Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Establecer y obtener bloqueos
 Puede establecer bloqueos en el almacén, en una partición o en un elemento individual. Por ejemplo, esta instrucción impedirá que se elimine un elemento de modelo y también impedirá que se cambien sus propiedades:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Se pueden usar otros valores de bloqueo para evitar cambios en las relaciones, la creación de elementos, el movimiento entre particiones y la reordenación de los vínculos de un rol.

 Los bloqueos se aplican a las acciones del usuario y al código del programa. Si el código de programa intenta realizar un cambio, se `InvalidOperationException` producirá una excepción. Los bloqueos se omiten en una operación de deshacer o rehacer.

 Puede detectar si un elemento tiene un bloqueo any en un conjunto determinado mediante `IsLocked(Locks)` y puede obtener el conjunto actual de bloqueos en un elemento mediante `GetLocks()` .

 Puede establecer un bloqueo sin usar una transacción. La base de datos de bloqueo no forma parte del almacén. Si establece un bloqueo en respuesta a un cambio de un valor en el almacén, por ejemplo, en OnValueChanged, debe permitir cambios que formen parte de una operación de deshacer.

 Estos métodos son métodos de extensión que se definen en el <xref:Microsoft.VisualStudio.Modeling.Immutability> espacio de nombres.

### <a name="locks-on-partitions-and-stores"></a>Bloqueos en particiones y almacenes
 Los bloqueos también se pueden aplicar a las particiones y al almacén. Un bloqueo que se establece en una partición se aplica a todos los elementos de la partición. Por lo tanto, por ejemplo, la siguiente instrucción impedirá que se eliminen todos los elementos de una partición, con independencia de los Estados de sus propios bloqueos. No obstante, se pueden establecer otros bloqueos como `Locks.Property` en elementos individuales:

```csharp
partition.SetLocks(Locks.Delete);
```

 Un bloqueo que se establece en el almacén se aplica a todos sus elementos, independientemente de la configuración de ese bloqueo en las particiones y los elementos.

### <a name="using-locks"></a>Usar bloqueos
 Puede usar bloqueos para implementar esquemas como los ejemplos siguientes:

- No permitir los cambios en todos los elementos y relaciones excepto en los que representan Comentarios. Esto permite a los usuarios anotar un modelo sin cambiarlo.

- No permitir los cambios en la partición predeterminada, pero permitir cambios en la partición del diagrama. El usuario puede reorganizar el diagrama, pero no puede modificar el modelo subyacente.

- No permitir cambios en el almacén, excepto un grupo de usuarios que estén registrados en una base de datos independiente. Para otros usuarios, el diagrama y el modelo son de solo lectura.

- No permitir cambios en el modelo si una propiedad booleana del diagrama está establecida en true. Proporcione un comando de menú para cambiar esa propiedad. Esto ayuda a garantizar que los usuarios no realicen cambios accidentalmente.

- No permitir la adición y eliminación de elementos y relaciones de clases concretas, pero permite cambios en las propiedades. Esto proporciona a los usuarios una forma fija en la que pueden rellenar las propiedades.

## <a name="lock-values"></a>Valores de bloqueo
 Los bloqueos se pueden establecer en un almacén, partición o ModelElement individual. Locks es una `Flags` enumeración: puede combinar sus valores mediante ' &#124; '.

- Los bloqueos de ModelElement siempre incluyen los bloqueos de su partición.

- Los bloqueos de una partición siempre incluyen los bloqueos del almacén.

  No se puede establecer un bloqueo en una partición o un almacén y, al mismo tiempo, deshabilitar el bloqueo en un elemento individual.

|Value|Significado si `IsLocked(Value)` es true|
|-|-|
|None|Sin restricción.|
|Propiedad|No se pueden cambiar las propiedades de dominio de los elementos. Esto no se aplica a las propiedades generadas por el rol de una clase de dominio en una relación.|
|Sumar|No se pueden crear nuevos elementos y vínculos en una partición o almacén.<br /><br /> No es aplicable a `ModelElement` .|
|Move|No se puede desplazar el elemento entre particiones si `element.IsLocked(Move)` es true o si `targetPartition.IsLocked(Move)` es true.|
|Eliminar|No se puede eliminar un elemento si este bloqueo se establece en el propio elemento o en cualquiera de los elementos en los que se propagará la eliminación, como elementos y formas incrustados.<br /><br /> Puede utilizar `element.CanDelete()` para detectar si un elemento se puede eliminar.|
|Reordenar|No se puede cambiar el orden de los vínculos en un roleplayer.|
|RolePlayer|No se puede cambiar el conjunto de vínculos que se encuentran en este elemento. Por ejemplo, los nuevos elementos no se pueden incrustar en este elemento. Esto no afecta a los vínculos para los que este elemento es el destino.<br /><br /> Si este elemento es un vínculo, su origen y destino no se ven afectados.|
|All|OR bit a bit de los demás valores.|

## <a name="locking-policies"></a>Directivas de bloqueo
 Como autor de un DSL, puede definir una directiva de *bloqueo*. Una directiva de bloqueo modera el funcionamiento de SetLocks (), de modo que se puede evitar que se establezcan bloqueos específicos o se exija que se establezcan bloqueos específicos. Normalmente, se usaría una directiva de bloqueo para evitar que los usuarios o desarrolladores infrinjan accidentalmente el uso previsto de un DSL, de la misma manera que se puede declarar una variable `private` .

 También puede usar una directiva de bloqueo para establecer bloqueos en todos los elementos que dependen del tipo del elemento. Esto se debe `SetLocks(Locks.None)` a que siempre se llama a cuando se crea o deserializa un elemento por primera vez desde el archivo.

 Sin embargo, no puede utilizar una directiva para modificar los bloqueos de un elemento durante su vida. Para lograr este efecto, debe utilizar las llamadas a `SetLocks()` .

 Para definir una directiva de bloqueo, tiene que:

- Cree una clase que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Agregue esta clase a los servicios que están disponibles a través del cData de DSL.

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

 Se llama a estos métodos cuando se realiza una llamada a `SetLocks()` en un almacén, una partición o ModelElement. En cada método, se proporciona un conjunto propuesto de bloqueos. Puede devolver el conjunto propuesto o puede Agregar y restar bloqueos.

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

 Para asegurarse de que los usuarios siempre pueden eliminar elementos, incluso si otras llamadas a código `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Para no permitir el cambio en todas las propiedades de todos los elementos de MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Para que la Directiva esté disponible como servicio
 En el `DslPackage` proyecto, agregue un nuevo archivo que contenga código similar al del ejemplo siguiente:

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
