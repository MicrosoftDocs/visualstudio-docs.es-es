---
title: Definir una directiva de bloqueo para crear segmentos de solo lectura | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6848f2c0b6c8d25fe7964fdb5519aa3f075bde57
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definir una directiva de bloqueo para crear segmentos de solo lectura
La API de inmutabilidad de los [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de visualización y modelado permite que un programa parte de bloqueo o la totalidad de un modelo de lenguaje específico de dominio (DSL) para que se puede leer pero no cambia. Se usa esta opción de solo lectura, por ejemplo, para que un usuario puede preguntar a compañeros para agregar anotaciones y revisar un modelo DSL pero puede no puedan cambiar el original.  
  
 Además, como autor de un DSL, puede definir un *la política de bloqueo.* Una directiva de bloqueo define los bloqueos que son permitidos, no se permite u obligatorio. Por ejemplo, cuando se publica un DSL, puede recomendar a los programadores de otros fabricantes para ampliar con nuevos comandos. Pero también podría utilizar una directiva de bloqueo para evitar que modificar el estado de solo lectura de elementos especificados del modelo.  
  
> [!NOTE]
>  Una directiva de bloqueo puede evitarse mediante la reflexión. Proporciona un límite claro para los desarrolladores de aplicaciones de terceros, pero no proporcionan una gran seguridad.  
  
 Obtener más información y ejemplos están disponibles en Visual Studio [SDK de visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) sitio Web.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>Establecer u obtener bloqueos  
 Puede establecer los bloqueos en el almacén, en una partición o en un elemento individual. Por ejemplo, esta instrucción impedirá que un elemento del modelo que se va a eliminar y también impide que sus propiedades que se va a cambiar:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Pueden utilizar otros valores de bloqueo para evitar cambios en las relaciones, la creación de elemento, el movimiento entre particiones y volver a ordenación vínculos en un rol.  
  
 Los bloqueos se aplican a las acciones del usuario tanto para código de programa. Si el código de programa intenta realizar un cambio, un `InvalidOperationException` se iniciará. Se omiten los bloqueos en una operación de deshacer o rehacer.  
  
 Puede detectar si un elemento tiene un bloqueo de cualquier en un conjunto determinado mediante el uso de `IsLocked(Locks)` y puede obtener el conjunto actual de bloqueos en un elemento mediante `GetLocks()`.  
  
 Puede establecer un bloqueo sin utilizar una transacción. La base de datos de bloqueo no forma parte de la tienda. Si establece un bloqueo en respuesta a un cambio de un valor en el almacén, por ejemplo en OnValueChanged, debe permitir los cambios que forman parte de una operación de deshacer.  
  
 Estos métodos son métodos de extensión que se definen en el <xref:Microsoft.VisualStudio.Modeling.Immutability> espacio de nombres.  
  
### <a name="locks-on-partitions-and-stores"></a>Bloqueos de particiones y los almacenes  
 También puede aplicarse a las particiones y el almacén de bloqueos. Un bloqueo que se establece en una partición se aplica a todos los elementos de la partición. Por lo tanto, por ejemplo, la siguiente instrucción impedirá todos los elementos de una partición que se va a eliminar, independientemente de los Estados de sus propios bloqueos. No obstante, otros bloqueos como `Locks.Property` todavía puede establecerse en elementos individuales:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un bloqueo que se establece en el almacén se aplica a todos sus elementos, independientemente de la configuración de dicho bloqueo en las particiones y los elementos.  
  
### <a name="using-locks"></a>Uso de bloqueos  
 Podría utilizar bloqueos para implementar esquemas como en los ejemplos siguientes:  
  
-   No permitir cambios a todos los elementos y relaciones, salvo aquellos que representan los comentarios. Esto permite a los usuarios anotar un modelo sin modificarlo.  
  
-   No permitir cambios en la partición predeterminada, pero permitir que los cambios en la partición de diagrama. El usuario puede reorganizar el diagrama, pero no puede modificar el modelo subyacente.  
  
-   No permitir cambios en el almacén excepto para un grupo de usuarios que están registrados en una base de datos independiente. Para otros usuarios, el diagrama y el modelo son de solo lectura.  
  
-   No permitir cambios en el modelo si se establece una propiedad booleana del diagrama en true. Proporciona un comando de menú para cambiar esa propiedad. Esto ayuda a garantizar que los usuarios que no hagan cambios accidentalmente.  
  
-   No permitir la adición y eliminación de elementos y relaciones de determinadas clases, pero permitir que los cambios de propiedad. Esto proporciona a los usuarios un formulario fijo en el que pueden rellenar las propiedades.  
  
## <a name="lock-values"></a>Valores de bloqueo  
 Los bloqueos se pueden establecer en un almacén, partición o ModelElement individual. Locks es una `Flags` enumeración: puede combinar sus valores usando ' &#124;'.  
  
-   Bloqueos de una ModelElement siempre incluyen los bloqueos de su partición.  
  
-   Bloqueos de una partición siempre incluyen los bloqueos de la tienda.  
  
 No se puede establecer un bloqueo en una partición o almacenar y al mismo tiempo, deshabilite el bloqueo en un elemento individual.  
  
|Valor|Lo que significa que si `IsLocked(Value)` es true|  
|-----------|------------------------------------------|  
|Ninguna|Sin restricción.|  
|Property|No se puede cambiar las propiedades de dominio de los elementos. Esto no se aplica a las propiedades que se generan mediante la función de una clase de dominio en una relación.|  
|Add|No se puede crear nuevos elementos y vínculos en una partición o en el almacén.<br /><br /> No es aplicable a `ModelElement`.|  
|Mover|No se puede mover el elemento entre particiones si `element.IsLocked(Move)` es true, o si `targetPartition.IsLocked(Move)` es true.|  
|Eliminar|No se puede eliminar un elemento si este bloqueo se establece en el propio elemento o en cualquiera de los elementos a los que podría propagar la eliminación, como las formas y los elementos incrustados.<br /><br /> Puede usar `element.CanDelete()` para detectar si se puede eliminar un elemento.|  
|Volver a ordenar|No se puede cambiar el orden de vínculos en un roleplayer.|  
|RolePlayer|No se puede cambiar el conjunto de vínculos que se generan en este elemento. Por ejemplo, no se puede incrustar elementos nuevos en este elemento. Esto no afecta a los vínculos para el que este elemento es el destino.<br /><br /> Si este elemento es un vínculo, su origen y destino no se ven afectados.|  
|Todas|Operación OR bit a bit de los demás valores.|  
  
## <a name="locking-policies"></a>Directivas de bloqueos  
 Como autor de un DSL, puede definir un *bloqueo directiva*. Una directiva de bloqueo modera la operación de SetLocks(), por lo que puede impedir que bloqueos específicos que se va a establecer o exigir que se deben establecer bloqueos específicos. Normalmente, se usa una directiva de bloqueo para evitar que los usuarios o los desarrolladores cometen accidentalmente el uso previsto de un DSL, de la misma manera que puede declarar una variable `private`.  
  
 También puede usar una directiva de bloqueo para establecer bloqueos en todos los elementos dependientes en el tipo del elemento. Esto es porque `SetLocks(Locks.None)` siempre se llama cuando un elemento en primer lugar se crea o se deserializa desde archivo.  
  
 Sin embargo, no se puede utilizar una directiva para variar los bloqueos sobre un elemento durante su vida útil. Para lograr este efecto, debe utilizar llamadas a `SetLocks()`.  
  
 Para definir una directiva de bloqueo, tendrá que:  
  
-   Cree una clase que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Agregar esta clase a los servicios que están disponibles a través de la DocData del ADSL.  
  
### <a name="to-define-a-locking-policy"></a>Para definir una directiva de bloqueo  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>tiene la siguiente definición:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Estos métodos se invocan cuando se realiza una llamada a `SetLocks()` en un almacén, partición o ModelElement. En cada método, se le proporcionará un conjunto propuesto de bloqueos. Puede devolver el conjunto de propuesta, o puede agregar y sustraer bloqueos.  
  
 Por ejemplo:  
  
```  
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
  
 Para asegurarse de que los usuarios siempre pueden eliminar elementos, incluso si llama a otro código`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Para no permitir cambios en todas las propiedades de cada elemento de MyClass:  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>Para que la directiva esté disponible como un servicio  
 En su `DslPackage` del proyecto, agregue un nuevo archivo que contiene código que es similar al siguiente:  
  
```  
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
