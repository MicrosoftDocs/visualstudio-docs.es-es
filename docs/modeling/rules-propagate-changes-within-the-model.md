---
title: Las reglas propagan los cambios dentro del modelo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4d315bdcae0f48db655a5878e82937478904fd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926409"
---
# <a name="rules-propagate-changes-within-the-model"></a>Las reglas propagan los cambios dentro del modelo
Puede crear una regla de almacén para propagar un cambio de un elemento a otro en el SDK de visualización y modelado (VMSDK). Cuando se produce un cambio en cualquier elemento del almacén, se programan las reglas para que se ejecuten, normalmente cuando se confirma la transacción más externa. Hay diferentes tipos de reglas para diferentes tipos de eventos, como agregar un elemento o eliminarlo. Puede adjuntar reglas a tipos específicos de elementos, formas o diagramas. Muchas características integradas se definen mediante reglas: por ejemplo, las reglas garantizan que un diagrama se actualice cuando cambie el modelo. Puede personalizar el lenguaje específico de dominio agregando sus propias reglas.

 Las reglas de almacenamiento son especialmente útiles para propagar los cambios dentro del almacén; es decir, los cambios en los elementos del modelo, las relaciones, las formas o conectores y sus propiedades de dominio. Las reglas no se ejecutan cuando el usuario invoca los comandos deshacer o rehacer. En su lugar, el administrador de transacciones se asegura de que el contenido del almacén se restaure al estado correcto. Si desea propagar los cambios a los recursos fuera del almacén, use los eventos de la tienda. Para obtener más información, vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Por ejemplo, supongamos que desea especificar que cada vez que el usuario (o el código) cree un nuevo elemento de tipo ExampleDomainClass, se creará un elemento adicional de otro tipo en otra parte del modelo. Podría escribir una AddRule y asociarla a ExampleDomainClass. Escribiría código en la regla para crear el elemento adicional.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> El código de una regla solo debe cambiar el estado de los elementos dentro del almacén. es decir, la regla solo debe cambiar los elementos del modelo, las relaciones, las formas, los conectores, los diagramas o sus propiedades. Si desea propagar los cambios a los recursos fuera del almacén, defina eventos de almacén. Para obtener más información, vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Para definir una regla

1. Defina la regla como una clase con el prefijo `RuleOn` del atributo. El atributo asocia la regla con una de las clases de dominio, las relaciones o los elementos de diagrama. La regla se aplicará a cada instancia de esta clase, que puede ser abstracta.

2. Registre la regla agregándola al conjunto devuelto por `GetCustomDomainModelTypes()` en la clase de modelo de dominio.

3. Derive la clase de regla de una de las clases de regla abstracta y escriba el código del método de ejecución.

   En las siguientes secciones se describen estos pasos con más detalle.

### <a name="to-define-a-rule-on-a-domain-class"></a>Para definir una regla en una clase de dominio

- En un archivo de código personalizado, defina una clase y Prefije con <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> el atributo:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- El tipo de asunto del primer parámetro puede ser una clase de dominio, una relación de dominio, una forma, un conector o un diagrama. Normalmente, las reglas se aplican a las relaciones y las clases de dominio.

     `FireTime` Suele ser`TopLevelCommit`. Esto garantiza que la regla se ejecute solo después de que se hayan realizado todos los cambios principales de la transacción. Las alternativas son alineadas, que ejecutan la regla pronto después del cambio; y LocalCommit, que ejecuta la regla al final de la transacción actual (que podría no ser la externa). También puede establecer la prioridad de una regla para que afecte a su orden en la cola, pero se trata de un método poco confiable para lograr el resultado que necesita.

- Puede especificar una clase abstracta como el tipo de asunto.

- La regla se aplica a todas las instancias de la clase de asunto.

- El valor predeterminado de `FireTime` es TimeToFire. TopLevelCommit. Esto hace que se ejecute la regla cuando se confirma la transacción más externa. Una alternativa es TimeToFire. Inline. Esto hace que la regla se ejecute pronto después del evento de desencadenamiento.

### <a name="to-register-the-rule"></a>Para registrar la regla

- Agregue la clase de regla a la lista de tipos devuelta por `GetCustomDomainModelTypes` en el modelo de dominio:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Si no está seguro del nombre de la clase de modelo de dominio, mire dentro del archivo **Dsl\GeneratedCode\DomainModel.CS**

- Escriba este código en un archivo de código personalizado en el proyecto DSL.

### <a name="to-write-the-code-of-the-rule"></a>Para escribir el código de la regla

- Derive la clase Rule de una de las clases base siguientes:

  | Clase base | Desencadenador |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Se agrega un elemento, un vínculo o una forma.<br /><br /> Úselo para detectar nuevas relaciones, además de los nuevos elementos. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Se cambia el valor de una propiedad de dominio. El argumento Method proporciona los valores antiguos y nuevos.<br /><br /> En el caso de las formas, esta regla se desencadena cuando cambia `AbsoluteBounds` la propiedad integrada, si se mueve la forma.<br /><br /> En muchos casos, es más conveniente invalidar `OnValueChanged` o `OnValueChanging` en el controlador de propiedad. Estos métodos se llaman inmediatamente antes y después del cambio. Por el contrario, la regla normalmente se ejecuta al final de la transacción. Para obtener más información, vea [controladores de cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md). **Nota:**  Esta regla no se desencadena cuando se crea o se elimina un vínculo. En su lugar, escriba `AddRule` `DeleteRule` y para la relación de dominio. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Se desencadena cuando un elemento o vínculo está a punto de eliminarse. La propiedad ModelElement. IsDeleting es true hasta el final de la transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Se realiza cuando se ha eliminado un elemento o vínculo. La regla se ejecuta después de que se hayan ejecutado todas las demás reglas, incluido DeletingRules. ModelElement. IsDeleting es false y ModelElement. IsDeleted es true. Para permitir una operación de deshacer posterior, el elemento no se quita realmente de la memoria, pero se quita del almacén. ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un elemento se mueve de una partición del almacén a otra.<br /><br /> (Observe que esto no está relacionado con la posición gráfica de una forma). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Esta regla solo se aplica a las relaciones de dominio. Se desencadena si asigna explícitamente un elemento de modelo a cualquier extremo de un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Se desencadena cuando se cambia el orden de los vínculos hacia o desde un elemento mediante los métodos MoveBefore o MoveToIndex de un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Se ejecuta cuando se crea una transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Se ejecuta cuando la transacción está a punto de confirmarse. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Se ejecuta cuando se va a revertir la transacción. |

- Cada clase tiene un método invalidado. Escriba `override` en la clase para detectarlo. El parámetro de este método identifica el elemento que se va a cambiar.

  Tenga en cuenta los siguientes aspectos sobre las reglas:

1. El conjunto de cambios en una transacción podría desencadenar muchas reglas. Normalmente, las reglas se ejecutan cuando se confirma la transacción más externa. Se ejecutan en un orden no especificado.

2. Una regla siempre se ejecuta dentro de una transacción. Por lo tanto, no es necesario crear una nueva transacción para realizar cambios.

3. Las reglas no se ejecutan cuando se revierte una transacción o cuando se realizan las operaciones de deshacer o rehacer. Estas operaciones restablecen todo el contenido del almacén a su estado anterior. Por lo tanto, si la regla cambia el estado de cualquier cosa fuera del almacén, puede que no se mantenga en synchronism con el contenido de la tienda. Para actualizar el estado fuera del almacén, es mejor usar eventos. Para obtener más información, vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Algunas reglas se ejecutan cuando se carga un modelo desde el archivo. Para determinar si la carga o el almacenamiento están en curso `store.TransactionManager.CurrentTransaction.IsSerializing`, use.

5. Si el código de la regla crea más desencadenadores de reglas, se agregarán al final de la lista de activación y se ejecutarán antes de que se complete la transacción. DeletedRules se ejecutan después de todas las demás reglas. Una regla se puede ejecutar muchas veces en una transacción, una vez por cada cambio.

6. Para pasar información a las reglas y desde ellas, puede almacenar información en `TransactionContext`. Se trata simplemente de un diccionario que se mantiene durante la transacción. Se elimina cuando finaliza la transacción. Los argumentos de evento de cada regla proporcionan acceso a ella. Recuerde que las reglas no se ejecutan en un orden predecible.

7. Use reglas después de considerar otras alternativas. Por ejemplo, si desea actualizar una propiedad cuando cambia un valor, considere la posibilidad de usar una propiedad calculada. Si desea restringir el tamaño o la ubicación de una forma, use `BoundsRule`. Si desea responder a un cambio en un valor de propiedad, agregue un `OnValueChanged` controlador a la propiedad. Para obtener más información, consulte [responder a los cambios y](../modeling/responding-to-and-propagating-changes.md)propagarlos.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se actualiza una propiedad cuando se crea una instancia de una relación de dominio para vincular dos elementos. La regla se desencadenará no solo cuando el usuario cree un vínculo en un diagrama, sino también si el código del programa crea un vínculo.

 Para probar este ejemplo, cree un DSL con la plantilla de solución flujo de tareas e inserte el código siguiente en un archivo del proyecto DSL. Compile y ejecute la solución y abra el archivo de ejemplo en el proyecto de depuración. Dibuje un vínculo de comentario entre una forma de comentario y un elemento de flujo. El texto del comentario cambia a informe en el elemento más reciente al que se ha conectado.

 En la práctica, normalmente escribiría un DeleteRule para cada AddRule.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Vea también

- [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)