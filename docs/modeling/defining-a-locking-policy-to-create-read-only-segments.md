---
title: "Definir una directiva de bloqueo para crear segmentos de solo lectura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
caps.handback.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Definir una directiva de bloqueo para crear segmentos de solo lectura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La Inmutabilidad API de SDK de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de visualización y modelado permite que un programa bloquear la parte o todo el modelo específico \(DSL\) del lenguaje para que se pueda leer pero no cambiar.  Esta opción de solo lectura puede utilizar, por ejemplo, para que un usuario puede pedir a sus colegas anotan y que revisen un modelo ADSL pero puede denegarlos de cambiar el original.  
  
 Además, como autor ADSL, puede definir *una directiva de bloqueo.* Una directiva de bloqueo define se permite, no se permite que los bloqueos, u obligatorio.  Por ejemplo, al publicar un DSL, puede animar los programadores de otros fabricantes a extenderla con nuevos comandos.  Pero también puede utilizar una directiva de bloqueo para evitar modificar el estado de sólo lectura de partes especificadas del modelo.  
  
> [!NOTE]
>  Una directiva de bloqueo se puede evitar mediante la reflexión.  Proporciona un límite claro para los programadores de otros fabricantes, pero no proporciona de seguridad.  
  
 Más información y ejemplos están disponibles en el sitio Web[El SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkId=186128) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## La configuración y el obtener bloqueos  
 Puede establecer bloqueos en el almacén, en una partición, o en un elemento individual.  Por ejemplo, esta instrucción evitará un elemento modelo sea eliminado, y también evitará que sus propiedades son modificadas:  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 Otros valores de bloqueo se pueden utilizar para evitar cambios en relaciones, creación de elemento, desplazarse entre las particiones, y reordenar vínculos en un rol.  
  
 Los bloqueos se aplican a las acciones del usuario y el código de programa.  Si el código de programa intenta realizar un cambio, `InvalidOperationException` se producirá.  Los bloqueos se omiten en una operación de deshacer o de rehacer.  
  
 Puede detectar si un elemento tiene un cualquier bloqueo en un determinado conjunto con `IsLocked(Locks)` y puede obtener el conjunto actual de interbloqueo en un elemento mediante `GetLocks()`.  
  
 Puede establecer un bloqueo sin utilizar una transacción.  La base de datos de bloqueo no forma parte del almacén.  Si establece un bloqueo en respuesta a un cambio de un valor en el almacén, por ejemplo en OnValueChanged, permite los cambios que forman parte de una operación.  
  
 Estos métodos son métodos de extensión que están definidos en el espacio de nombres <xref:Microsoft.VisualStudio.Modeling.Immutability> .  
  
### Bloqueos en particiones y almacena  
 Los bloqueos también puede aplicarse a las particiones y el almacén.  Un bloqueo que se establece en una partición se aplica a todos los elementos de la partición.  Por tanto, por ejemplo, la siguiente instrucción evitará que todos los elementos de un elemento se eliminen, con independencia de los estados de su propio bloqueo.  Sin embargo, otros bloqueos por ejemplo `Locks.Property` podría establecer en elementos individuales:  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 Un bloqueo que se establece en el almacén se aplica a todos sus elementos, con independencia de los valores de ese bloqueo en particiones y elementos.  
  
### Mediante bloqueos  
 Puede usar bloqueos para implementar esquemas como los ejemplos siguientes:  
  
-   Denegar los cambios a todos los elementos y relaciones excepto los que representan comentarios.  Esto permite a los usuarios anotan un modelo sin cambiarlo.  
  
-   Denegar los cambios en la partición predeterminada, pero permite los cambios en el elemento del diagrama.  el usuario puede reorganizar el diagrama, pero no puede modificar el modelo subyacente.  
  
-   Denegar los cambios al almacén excepto un grupo de usuarios registrados en una base de datos independiente.  Para otros usuarios, el diagrama y el modelo son de solo lectura.  
  
-   Denegar los cambios en el modelo si una propiedad boolean de diagrama se establece en true.  Proporcione un comando de menú para cambiar esa propiedad.  Esto ayuda a los usuarios asegurarse de que no realizan cambios accidentalmente.  
  
-   Denegar la adición y eliminación de elementos y relaciones de determinadas clases, pero permite cambia la propiedad.  Esto proporciona a los usuarios un de forma fija en la que puede rellenar las propiedades.  
  
## Valores de bloqueo  
 Bloqueos puede definir en un almacén, una partición, o un ModelElement individual.  Bloqueos es una enumeración de `Flags` : puede combinar los valores utilizando “&#124;”.  
  
-   Bloqueos de se incluye de ModelElement bloquea siempre de su parte.  
  
-   Bloqueos de una incluyen de partición bloquea siempre store.  
  
 No se puede establecer un bloqueo en una partición o almacenar y al mismo tiempo deshabilitar el bloqueo en un elemento individual.  
  
|Valor|Lo que significa que si `IsLocked(Value)` es true|  
|-----------|-------------------------------------------------------|  
|None|ninguna restricción.|  
|Propiedad.|Las propiedades del dominio de elementos no se pueden cambiar.  Esto no se aplica a las propiedades generadas por el rol de una clase de dominio en una relación.|  
|Agregar|los nuevos elementos y vínculos no se pueden crear en una partición o un almacén.<br /><br /> no aplicable a `ModelElement`.|  
|Mover|El elemento no se puede mover entre las particiones si `element.IsLocked(Move)` es true, o si `targetPartition.IsLocked(Move)` es true.|  
|Eliminar|Un elemento no se puede eliminar si este bloqueo se establece en el propio elemento, o en cualquiera de los elementos a los que la eliminación propagaría, como elementos incrustados y formas.<br /><br /> Puede utilizar `element.CanDelete()` para detectar si un elemento se puede eliminar.|  
|Reordenar|El orden de vínculos en un roleplayer no puede modificarse.|  
|RolePlayer|El conjunto de vínculos que son su origen en este elemento no se puede cambiar.  Por ejemplo, los nuevos elementos no se pueden insertar en este elemento.  Esto no afecta a los vínculos para los que este elemento es el destino.<br /><br /> Si este elemento es un vínculo, el origen y destino no resultan afectados.|  
|Todos|OR bit a bit de los otros valores.|  
  
## Directivas de bloqueo  
 Como autor de DSL, puede definir *una directiva de bloqueo*.  Una directiva de bloqueo modera la operación de SetLocks\(\), de modo que pueda evitar concreto bloquee de establecer o asignadas por mandato concreto bloquea establecido.  Normalmente, utilizaría una directiva de bloqueo de desalentar usuarios o los desarrolladores accidental de contravenir el uso previsto ADSL, de la misma manera que puede declarar `private`variable.  
  
 También puede utilizar una directiva de bloqueo para establecer bloqueos en todos los elementos dependientes en el tipo de elemento.  Esto es porque `SetLocks(Locks.None)` siempre se llama cuando un elemento se crea por primera vez o se deserializa desde un archivo.  
  
 Sin embargo, no puede utilizar una directiva para variar bloqueos en un elemento durante su duración.  Para lograr este efecto, debe utilizar llamadas a `SetLocks()`.  
  
 Para definir una directiva de bloqueo, tiene que:  
  
-   cree una clase que implemente <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.  
  
-   Agregue esta clase a los servicios que están disponibles con el DocData ADSL.  
  
### Para definir una directiva de bloqueo  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> tiene la siguiente definición:  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 Se llama a estos métodos cuando se realiza una llamada a `SetLocks()` en un almacén, una partición, o un ModelElement.  En cada método, proporcionan un conjunto propuesto de bloqueos.  Puede devolver el conjunto propuesto, o puede agregar y quitar bloqueos.  
  
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
  
 Para asegurarse de que los usuarios puedan eliminar siempre elementos, incluso si el código llama a `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 Denegar el cambio en todas las propiedades de cada elemento MyClass:  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### Para que la directiva disponible como servicio  
 En el proyecto de `DslPackage` , agregue un nuevo archivo que contiene el código similar al ejemplo siguiente:  
  
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