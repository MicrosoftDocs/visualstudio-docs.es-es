---
title: Las reglas propagan los cambios dentro del modelo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 70bacc7e181c27efd14b613c20af29e850db321a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925555"
---
# <a name="rules-propagate-changes-within-the-model"></a>Las reglas propagan los cambios dentro del modelo
Puede crear una regla de almacén para propagar un cambio de un elemento a otro en la visualización y el SDK de modelado (VMSDK). Cuando se produce un cambio a cualquier elemento en el Store, las reglas se programan para ejecutarse, normalmente, cuando se confirma la transacción más externa. Hay diferentes tipos de reglas para los diferentes tipos de eventos, como agregar un elemento, o eliminarlo. Puede asociar reglas a tipos específicos de elementos, formas y diagramas. Muchas características integradas se definen mediante reglas: por ejemplo, reglas garantizan que un diagrama se actualiza cuando cambia el modelo. Puede personalizar su lenguaje específico de dominio mediante la adición de sus propias reglas.

 Las reglas de Store son especialmente útiles para propagar los cambios en el almacén, es decir, los cambios en los elementos del modelo, las relaciones, formas o conectores y su dominio propiedades. Las reglas no se ejecutan cuando el usuario invoca los comandos Deshacer o rehacer. En su lugar, el Administrador de transacciones garantiza que el contenido del almacén se restaura al estado correcto. Si desea propagar los cambios a los recursos fuera de la tienda, utilice eventos Store. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Por ejemplo, suponga que desea especificar que cada vez que el usuario (o el código) crea un nuevo elemento de tipo ExampleDomainClass, se crea un elemento adicional de otro tipo en otra parte del modelo. Puede escribir un AddRule y asociarla a ExampleDomainClass. Podría escribir código en la regla para crear el elemento adicional.

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
>  El código de una regla debe cambiar el estado únicamente de los elementos dentro de la Store; es decir, debe cambiar la regla solo los elementos del modelo, las relaciones, formas, conectores, diagramas o sus propiedades. Si desea propagar los cambios a los recursos fuera de la tienda, definen los eventos de Store. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Para definir una regla

1. Definir la regla como una clase con el prefijo del `RuleOn` atributo. El atributo asocia la regla con uno de sus clases de dominio, relaciones o elementos del diagrama. La regla se aplicará a todas las instancias de esta clase, que puede ser abstracta.

2. Registrar la regla, éste se agrega al conjunto devuelto por `GetCustomDomainModelTypes()` en la clase de modelo de dominio.

3. Derivar la clase de regla de una de las clases abstractas de la regla y escribir el código del método de ejecución.

   Las secciones siguientes describen estos pasos con más detalle.

### <a name="to-define-a-rule-on-a-domain-class"></a>Para definir una regla en una clase de dominio

-   En un archivo de código personalizado, defina una clase y un prefijo con el <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atributo:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   El tipo de sujeto en el primer parámetro puede ser la clase de dominio, relación de dominio, forma, conector o diagrama. Por lo general, se aplican las reglas para las relaciones y las clases de dominio.

     El `FireTime` suele ser `TopLevelCommit`. Esto garantiza que la regla se ejecuta solo una vez realizados todos los cambios principales de la transacción. Las alternativas son en línea, que se ejecuta la regla poco después del cambio; y LocalCommit, que ejecuta la regla al final de la transacción actual (que podría no ser la más externa). También puede establecer la prioridad de una regla que afecta a su ordenación en la cola, pero se trata de un método no confiable de lograr el resultado que necesita.

-   Puede especificar una clase abstracta como el tipo de sujeto.

-   La regla se aplica a todas las instancias de la clase de asunto.

-   El valor predeterminado de `FireTime` es TimeToFire.TopLevelCommit. Esto hace que la regla se ejecutará cuando se confirma la transacción más externa. Una alternativa es TimeToFire.Inline. Esto hace que la regla se ejecuta poco después del evento desencadenador.

### <a name="to-register-the-rule"></a>Para registrar la regla

-   Agregue la clase de regla a la lista de tipos devuelta por `GetCustomDomainModelTypes` en el modelo de dominio:

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

-   Si no está seguro del nombre de la clase de modelo de dominio, mira dentro del archivo **Dsl\GeneratedCode\DomainModel.cs**

-   Escriba este código en un archivo de código personalizado en el proyecto DSL.

### <a name="to-write-the-code-of-the-rule"></a>Escribir el código de la regla

- Derivar la clase de regla de una de las siguientes clases base:


  | Clase base | Desencadenador |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Se agrega un elemento, un vínculo o una forma.<br /><br /> Utilícelo para detectar nuevas relaciones, además de los nuevos elementos. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Se cambia un valor de propiedad de dominio. El argumento del método proporciona los valores antiguos y nuevos.<br /><br /> Para las formas, esta regla se desencadena cuando la integrada `AbsoluteBounds` cambios de propiedad, si se mueve la forma.<br /><br /> En muchos casos, resulta más cómodo invalidar `OnValueChanged` o `OnValueChanging` en el controlador de propiedad. Estos métodos se llama inmediatamente antes y después del cambio. Por el contrario, la regla se ejecuta normalmente al final de la transacción. Para obtener más información, consulte [controladores de cambio de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md). **Nota:**  Esta regla no se desencadena cuando se crea o elimina un vínculo. En su lugar, escribir un `AddRule` y un `DeleteRule` para la relación de dominio. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Se desencadena cuando un elemento o vínculo está a punto de eliminarse. La propiedad ModelElement.IsDeleting es true hasta el final de la transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Puede realizar cuando se ha eliminado un elemento o vínculo. La regla se ejecuta después de que se han ejecutado todas las demás reglas, incluyendo DeletingRules. ModelElement.IsDeleting es false, y ModelElement.IsDeleted es true. Para permitir una operación de deshacer posteriores, el elemento no se quita de la memoria, pero se quita del Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un elemento se mueve desde un almacén de partición a otra.<br /><br /> (Tenga en cuenta que esto no está relacionado con la posición de una forma gráfica). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Esta regla se aplica solo a las relaciones de dominio. Se desencadena si se asigna explícitamente un elemento de modelo para cualquiera de los extremos de un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Se desencadena cuando el orden de vínculos a o desde un elemento se cambia mediante los métodos MoveBefore o MoveToIndex en un vínculo. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Se ejecuta cuando se crea una transacción. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Se ejecuta cuando la transacción está a punto de confirmarse. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Se ejecuta cuando la transacción se revertirá a. |


- Cada clase tiene un método que reemplazar. Tipo `override` en su clase para detectarlo. El parámetro de este método identifica el elemento que se va a cambiar.

  Tenga en cuenta los siguientes puntos acerca de las reglas:

1.  El conjunto de cambios en una transacción, puede desencadenar muchas reglas. Por lo general, las reglas se ejecutan cuando se confirma la transacción más externa. Se ejecutan en un orden no especificado.

2.  Una regla siempre se ejecuta dentro de una transacción. Por lo tanto, no es necesario crear una nueva transacción para realizar cambios.

3.  Las reglas no se ejecutan cuando se revierte una transacción, o cuando se realizan las operaciones de deshacer o rehacer. Estas operaciones restablecen todo el contenido de la Store a su estado anterior. Por lo tanto, si la regla cambia el estado de cualquier elemento fuera el Store, es posible que no tenga en synchronism con el Store contenido. Para actualizar el estado fuera el Store, es mejor utilizar eventos. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4.  Algunas de las reglas se ejecutan cuando se carga un modelo de archivo. Para determinar si cargar o guardar está en curso, use `store.TransactionManager.CurrentTransaction.IsSerializing`.

5.  Si el código de la regla crea varios desencadenadores de la regla, se agregarán al final de la lista de activación y se ejecutará antes de que finalice la transacción. DeletedRules se ejecutan después de todas las demás reglas. Una regla puede ejecutar muchas veces en una transacción, una vez para cada cambio.

6.  Para pasar información a y desde reglas, puede almacenar información en el `TransactionContext`. Esto es simplemente un diccionario que se mantiene durante la transacción. Se elimina cuando finaliza la transacción. Los argumentos del evento en cada regla de proporcionan acceso a él. Recuerde que las reglas no se ejecutan en un orden predecible.

7.  Reglas de uso después de considerar otras alternativas. Por ejemplo, si desea actualizar una propiedad cuando cambia un valor, considere el uso de una propiedad calculada. Si desea restringir el tamaño o la ubicación de una forma, use un `BoundsRule`. Si desea responder a un cambio en un valor de propiedad, agregue un `OnValueChanged` controlador a la propiedad. Para obtener más información, consulte [responde a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Ejemplo
 El ejemplo siguiente actualiza una propiedad cuando se crea una instancia de una relación de dominio para vincular dos elementos. Se desencadena la regla no solo cuando el usuario crea un vínculo en un diagrama, sino también si el código del programa crea un vínculo.

 Para probar este ejemplo, cree un DSL con la plantilla de solución de flujo de tareas y, inserte el código siguiente en un archivo en el proyecto de Dsl. Compilar y ejecutar la solución y abra el archivo de ejemplo en el proyecto de depuración. Dibuje un comentario de vínculo entre una forma de comentario y un elemento de flujo. Cambia el texto del comentario al informe en el elemento más reciente que se ha conectado a.

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
- [Ubicación y tamaño de las reglas de restricción de formas BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)