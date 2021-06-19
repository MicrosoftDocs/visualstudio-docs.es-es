---
title: Las reglas propagan los cambios dentro del modelo
description: Obtenga información sobre cómo crear una regla de almacén para propagar un cambio de un elemento a otro en el SDK de visualización y modelado (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387598"
---
# <a name="rules-propagate-changes-within-the-model"></a>Las reglas propagan los cambios dentro del modelo
Puede crear una regla de almacén para propagar un cambio de un elemento a otro en el SDK de visualización y modelado (VMSDK). Cuando se produce un cambio en cualquier elemento de Store, se programa la ejecución de reglas, normalmente cuando se confirma la transacción más externa. Hay diferentes tipos de reglas para diferentes tipos de eventos, como agregar un elemento o eliminarlo. Puede adjuntar reglas a tipos específicos de elementos, formas o diagramas. Muchas características integradas se definen mediante reglas: por ejemplo, las reglas garantizan que un diagrama se actualice cuando cambia el modelo. Puede personalizar el lenguaje específico del dominio agregando sus propias reglas.

 Las reglas de almacén son especialmente útiles para propagar los cambios dentro del almacén, es decir, los cambios en los elementos del modelo, las relaciones, las formas o los conectores, y sus propiedades de dominio. Las reglas no se ejecutan cuando el usuario invoca los comandos Deshacer o Rehacer. En su lugar, el administrador de transacciones se asegura de que el contenido del almacén se restaura al estado correcto. Si desea propagar los cambios a recursos fuera del almacén, use Eventos de almacén. Para obtener más información, vea [Controladores de eventos propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Por ejemplo, supongamos que desea especificar que cada vez que el usuario (o el código) crea un nuevo elemento de tipo ExampleDomainClass, se crea un elemento adicional de otro tipo en otra parte del modelo. Puede escribir un elemento AddRule y asociarlo a ExampleDomainClass. Escribiría código en la regla para crear el elemento adicional.

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
> El código de una regla debe cambiar el estado solo de los elementos dentro de Store; Es decir, la regla solo debe cambiar los elementos del modelo, las relaciones, las formas, los conectores, los diagramas o sus propiedades. Si desea propagar los cambios a recursos fuera del almacén, defina Eventos de almacén. Para obtener más información, vea [Controladores de eventos propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Para definir una regla

1. Defina la regla como una clase con el prefijo del `RuleOn` atributo . El atributo asocia la regla a una de las clases de dominio, relaciones o elementos de diagrama. La regla se aplicará a cada instancia de esta clase, que puede ser abstracta.

2. Registre la regla agregándole al conjunto devuelto por `GetCustomDomainModelTypes()` en la clase de modelo de dominio.

3. Derive la clase de regla de una de las clases Rule abstractas y escriba el código del método de ejecución.

   En las siguientes secciones se describen estos pasos con más detalle.

### <a name="to-define-a-rule-on-a-domain-class"></a>Para definir una regla en una clase de dominio

- En un archivo de código personalizado, defina una clase y prefijéela con el <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atributo :

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- El tipo de sujeto del primer parámetro puede ser una clase de dominio, una relación de dominio, una forma, un conector o un diagrama. Normalmente, se aplican reglas a las clases y relaciones de dominio.

     suele `FireTime` ser `TopLevelCommit` . Esto garantiza que la regla se ejecute solo después de que se hayan realizado todos los cambios principales de la transacción. Las alternativas son Inline, que ejecuta la regla poco después del cambio. y LocalCommit, que ejecuta la regla al final de la transacción actual (que podría no ser la más externa). También puede establecer la prioridad de una regla para que afecte a su ordenación en la cola, pero se trata de un método poco confiable para lograr el resultado que necesita.

- Puede especificar una clase abstracta como tipo de asunto.

- La regla se aplica a todas las instancias de la clase de sujeto.

- El valor predeterminado de `FireTime` es TimeToFire.TopLevelCommit. Esto hace que la regla se ejecute cuando se confirma la transacción más externa. Una alternativa es TimeToFire.Inline. Esto hace que la regla se ejecute poco después del evento de desencadenamiento.

### <a name="to-register-the-rule"></a>Para registrar la regla

- Agregue la clase de regla a la lista de tipos devueltos por `GetCustomDomainModelTypes` en el modelo de dominio:

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

- Si no está seguro del nombre de la clase de modelo de dominio, busque en el archivo **Dsl\GeneratedCode\DomainModel.cs.**

- Escriba este código en un archivo de código personalizado en el proyecto DSL.

### <a name="to-write-the-code-of-the-rule"></a>Para escribir el código de la regla

- Derive la clase de regla de una de las siguientes clases base:

  | Clase base | Desencadenador |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Se agrega un elemento, vínculo o forma.<br /><br /> Úsese esto para detectar nuevas relaciones, además de nuevos elementos. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Se cambia un valor de propiedad de dominio. El argumento del método proporciona los valores antiguos y nuevos.<br /><br /> En el caso de las formas, esta regla se desencadena cuando cambia la propiedad `AbsoluteBounds` integrada, si se mueve la forma.<br /><br /> En muchos casos, es más conveniente invalidar `OnValueChanged` o en el controlador de `OnValueChanging` propiedades. Estos métodos se llaman inmediatamente antes y después del cambio. Por el contrario, la regla normalmente se ejecuta al final de la transacción. Para obtener más información, vea [Domain Property Value Change Handlers](../modeling/domain-property-value-change-handlers.md). **Nota:**  Esta regla no se desencadena cuando se crea o elimina un vínculo. En su lugar, escriba `AddRule` y para la relación de `DeleteRule` dominio. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Se desencadena cuando un elemento o vínculo está a punto de eliminarse. La propiedad ModelElement.IsDeleting es true hasta el final de la transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Se realiza cuando se ha eliminado un elemento o vínculo. La regla se ejecuta después de que se hayan ejecutado todas las demás reglas, incluido DeletingRules. ModelElement.IsDeleting es false y ModelElement.IsDeleted es true. Para permitir una deshacer posteriormente, el elemento no se quita realmente de la memoria, pero se quita de Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un elemento se mueve de una partición de almacén a otra.<br /><br /> (Observe que esto no está relacionado con la posición gráfica de una forma). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Esta regla solo se aplica a las relaciones de dominio. Se desencadena si asigna explícitamente un elemento de modelo a cualquier extremo de un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Se desencadena cuando se cambia el orden de los vínculos hacia o desde un elemento mediante los métodos MoveBefore o MoveToIndex de un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Se ejecuta cuando se crea una transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Se ejecuta cuando la transacción está a punto de ser confirmada. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Se ejecuta cuando la transacción está a punto de revertirse. |

- Cada clase tiene un método que se invalida. Escriba `override` la clase para detectarla. El parámetro de este método identifica el elemento que se va a cambiar.

  Observe los siguientes puntos sobre las reglas:

1. El conjunto de cambios en una transacción puede desencadenar muchas reglas. Normalmente, las reglas se ejecutan cuando se confirma la transacción más externa. Se ejecutan en un orden no especificado.

2. Una regla siempre se ejecuta dentro de una transacción. Por lo tanto, no es necesario crear una nueva transacción para realizar cambios.

3. Las reglas no se ejecutan cuando se revierte una transacción o cuando se realizan las operaciones Deshacer o Rehacer. Estas operaciones restablecen todo el contenido de Store a su estado anterior. Por lo tanto, si la regla cambia el estado de cualquier elemento fuera de Store, es posible que no se mantenga sincronizado con el contenido de Store. Para actualizar el estado fuera de Store, es mejor usar Eventos. Para obtener más información, vea [Controladores de eventos propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Algunas reglas se ejecutan cuando se carga un modelo desde un archivo. Para determinar si la carga o el guardado están en curso, use `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Si el código de la regla crea más desencadenadores de regla, se agregarán al final de la lista de activación y se ejecutarán antes de que se complete la transacción. DeletedRules se ejecuta después de todas las demás reglas. Una regla se puede ejecutar muchas veces en una transacción, una vez por cada cambio.

6. Para pasar información hacia y desde reglas, puede almacenar información en `TransactionContext` . Se trata simplemente de un diccionario que se mantiene durante la transacción. Se elimina cuando finaliza la transacción. Los argumentos de evento de cada regla proporcionan acceso a él. Recuerde que las reglas no se ejecutan en un orden predecible.

7. Use reglas después de considerar otras alternativas. Por ejemplo, si desea actualizar una propiedad cuando cambia un valor, considere la posibilidad de usar una propiedad calculada. Si desea restringir el tamaño o la ubicación de una forma, use `BoundsRule` . Si desea responder a un cambio en un valor de propiedad, agregue un `OnValueChanged` controlador a la propiedad . Para obtener más información, vea [Responder a y propagar cambios.](../modeling/responding-to-and-propagating-changes.md)

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se actualiza una propiedad cuando se crea una instancia de una relación de dominio para vincular dos elementos. La regla se desencadenará no solo cuando el usuario cree un vínculo en un diagrama, sino también si el código del programa crea un vínculo.

 Para probar este ejemplo, cree un DSL mediante la plantilla de solución Flujo de tareas e inserte el código siguiente en un archivo en el proyecto dsl. Compile y ejecute la solución y abra el archivo de ejemplo en el proyecto Depuración. Dibuje un vínculo de comentario entre una forma Comment y un elemento de flujo. El texto del comentario cambia para informar sobre el elemento más reciente al que se ha conectado.

 En la práctica, normalmente escribiría deleteRule para cada AddRule.

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