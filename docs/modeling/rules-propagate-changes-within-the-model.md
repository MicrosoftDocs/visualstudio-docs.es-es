---
title: "Reglas de propagan los cambios en el modelo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, los modelos de dominio de programación"
  - "Lenguaje específico de dominio, las reglas"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Reglas de propagan los cambios en el modelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear una regla de almacén para propagar un cambio de un elemento a otro en la visualización y el SDK de modelado \(VMSDK\). Cuando se produce un cambio a cualquier elemento en el almacén, las reglas están programadas para ejecutarse, normalmente cuando se confirma la transacción más externa. Hay diferentes tipos de reglas para los diferentes tipos de eventos, como agregar un elemento o eliminarlo. Puede asociar reglas a tipos específicos de elementos, formas o diagramas. Muchas características integradas se definen mediante reglas: por ejemplo, asegúrese de que un diagrama se actualiza cuando cambia el modelo de reglas. Puede personalizar su lenguaje específico de dominio agregando sus propias reglas.  
  
 Almacén de reglas son especialmente útiles para propagar los cambios en el almacén, es decir, los cambios en su dominio, relaciones, formas o conectores y elementos del modelo propiedades. Las reglas no se ejecutan cuando el usuario invoca los comandos Deshacer o rehacer. En su lugar, el Administrador de transacciones garantiza que el contenido del almacén se restaura en el estado correcto. Si desea propagar los cambios a los recursos fuera del almacén, utilice almacenar eventos. Para obtener más información, consulta [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Por ejemplo, suponga que desea especificar que cada vez que el usuario \(o el código\) crea un nuevo elemento de tipo ExampleDomainClass, se crea un elemento adicional de otro tipo en otra parte del modelo. Puede escribir un AddRule y asociarla a ExampleDomainClass. Código que escribe en la regla para crear el elemento adicional.  
  
```c#  
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
  
    // Code here propagates change as required – for example:  
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
>  El código de una regla debe cambiar el estado solo de elementos dentro del almacén; es decir, debe cambiar la regla solo elementos del modelo, las relaciones, formas, conectores, diagramas o sus propiedades. Si desea propagar los cambios a los recursos fuera de la tienda, definen los eventos de almacén. Para obtener más información, vea [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### Para definir una regla  
  
1.  Defina la regla como una clase con el prefijo del `RuleOn` atributo. El atributo asocia la regla con una de sus clases de dominio, relaciones o elementos del diagrama. La regla se aplicará a todas las instancias de esta clase, que puede ser abstracta.  
  
2.  Registrar la regla, éste se agrega al conjunto devuelto por `GetCustomDomainModelTypes()` en la clase de modelo de dominio.  
  
3.  Derive la clase de regla de una de las clases abstractas de la regla y escribir el código del método de ejecución.  
  
 Las secciones siguientes describen estos pasos con más detalle.  
  
### Para definir una regla de una clase de dominio  
  
-   En un archivo de código personalizado, defina una clase y un prefijo con el <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> atributo:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   El tipo de sujeto en el primer parámetro puede ser una clase de dominio, relación de dominio, forma, conector o diagrama. Normalmente, aplicar reglas a las relaciones y las clases de dominio.  
  
     El `FireTime` suele ser `TopLevelCommit`. Esto garantiza que la regla se ejecuta sólo una vez realizados todos los cambios principales de la transacción. Las alternativas son Inline, que se ejecuta la regla poco después del cambio; y LocalCommit, que ejecuta la regla al final de la transacción actual \(que puede no ser la más externa\). También puede establecer la prioridad de una regla que afecta a su orden en la cola, pero éste es un método confiable de lograr el resultado que necesita.  
  
-   Puede especificar una clase abstracta como el tipo de sujeto.  
  
-   La regla se aplica a todas las instancias de la clase de objeto.  
  
-   El valor predeterminado de `FireTime` es TimeToFire.TopLevelCommit. Esto hace que la regla que se ejecuta cuando se confirma la transacción más externa. Una alternativa es TimeToFire.Inline. Esto hace que la regla se ejecuta poco después del evento desencadenador.  
  
### Para registrar la regla  
  
-   Agregue la clase de regla a la lista de tipos devuelta por `GetCustomDomainModelTypes` en el modelo de dominio:  
  
    ```  
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
  
-   Si no está seguro del nombre de la clase de modelo de dominio, mira dentro del archivo **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   Este código se puede escribir en un archivo de código personalizado en el proyecto DSL.  
  
### Escribir el código de la regla  
  
-   Derive la clase de regla de una de las siguientes clases base:  
  
    |Clase base|Desencadenador|  
    |----------------|--------------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Se agrega un elemento, un vínculo o una forma.<br /><br /> Úselo para detectar nuevas relaciones, además de nuevos elementos.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Se cambia el valor de una propiedad de dominio. El argumento del método proporciona los valores antiguos y nuevos.<br /><br /> Las formas, esta regla se desencadena cuando integrado `AbsoluteBounds` cambios de propiedad, si se mueve la forma.<br /><br /> En muchos casos, es más conveniente reemplazar `OnValueChanged` o `OnValueChanging` en el controlador de propiedad. Estos métodos se llama inmediatamente antes y después del cambio. Por el contrario, la regla se ejecuta normalmente al final de la transacción. Para obtener más información, consulta [Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md). **Note:**  Esta regla no se desencadena cuando se crea o se elimina un vínculo. En su lugar, escribir un `AddRule` y un `DeleteRule` para la relación de dominio.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Se desencadena cuando un elemento o vínculo se va a eliminar. La propiedad ModelElement.IsDeleting es true hasta el final de la transacción.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Se realiza cuando se ha eliminado un elemento o vínculo. La regla se ejecuta después de que se han ejecutado todas las demás reglas, incluyendo DeletingRules. ModelElement.IsDeleting es false, y ModelElement.IsDeleted es true. Para permitir una acción de deshacer posterior, el elemento no se quita de la memoria, pero se quita del Store.ElementDirectory.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Se mueve un elemento de la partición de un almacén a otro.<br /><br /> \(Observe que esto no está relacionado con la posición de una forma gráfica\).|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Esta regla se aplica sólo a las relaciones de dominio. Se desencadena si asigna explícitamente un elemento del modelo a cualquiera de los extremos de un vínculo.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Se desencadena cuando el orden de los vínculos a o desde un elemento se modifica mediante los métodos MoveBefore o MoveToIndex en un vínculo.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Se ejecuta cuando se crea una transacción.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Se ejecuta cuando la transacción está a punto de confirmarse.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Se ejecuta cuando es se revierte la transacción.|  
  
-   Cada clase tiene un método que reemplazar. Tipo de `override` en su clase para detectarlo. El parámetro de este método identifica el elemento que se va a cambiar.  
  
 Tenga en cuenta los siguientes puntos acerca de las reglas:  
  
1.  El conjunto de cambios en una transacción, puede desencadenar muchas reglas. Normalmente, las reglas se ejecutan cuando se confirma la transacción más externa. Se ejecutan en un orden no especificado.  
  
2.  Una regla se ejecuta siempre dentro de una transacción. Por lo tanto, no es necesario crear una nueva transacción para realizar cambios.  
  
3.  Las reglas no se ejecutan cuando se revierte una transacción, o cuando se realizan las operaciones de deshacer o rehacer. Estas operaciones restablecen todo el contenido del almacén a su estado anterior. Por lo tanto, si la regla cambia el estado de cualquier elemento fuera de la tienda, podría no tenga synchronism con el almacén de contenido. Para actualizar el estado fuera de la tienda, es mejor utilizar eventos. Para obtener más información, consulta [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Algunas reglas se ejecutan cuando un modelo de carga de archivo. Para determinar si cargar o guardar está en curso, utilice `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Si el código de la regla crea varios desencadenadores de regla, se agregarán al final de la lista de activación y se ejecutará antes de que finalice la transacción. DeletedRules se ejecuta después de todas las demás reglas. Una regla puede ejecutar muchas veces en una transacción, una vez para cada cambio.  
  
6.  Para pasar información a y desde reglas, puede almacenar información en el `TransactionContext`. Esto es simplemente un diccionario que se mantiene durante la transacción. Se eliminan cuando finaliza la transacción. Los argumentos de evento en cada regla de proporcionan acceso a él. Recuerde que las reglas no se ejecutan en un orden predecible.  
  
7.  Use reglas tras considerar otras alternativas. Por ejemplo, si desea actualizar una propiedad cuando cambia un valor, considere la posibilidad de usar una propiedad calculada. Si desea limitar el tamaño o la ubicación de una forma, use un `BoundsRule`. Si desea responder a un cambio en un valor de propiedad, agregue un `OnValueChanged` controlador para la propiedad. Para obtener más información, consulta [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).  
  
## Ejemplo  
 En el ejemplo siguiente se actualiza una propiedad cuando se crea una instancia de una relación de dominio para vincular dos elementos. No sólo cuando el usuario crea un vínculo en un diagrama, sino también si el código de programa crea un vínculo, se activará la regla.  
  
 Para probar este ejemplo, cree un DSL con la plantilla de solución de flujo de tareas y, inserte el siguiente código en un archivo en el proyecto de Dsl. Compilar y ejecutar la solución y abra el archivo de ejemplo en el proyecto de depuración. Dibuje un comentario de vínculo entre una forma de comentario y un elemento de flujo. Cambia el texto del comentario al informe en el elemento más reciente que se ha conectado a.  
  
 En la práctica, normalmente se escribiría un DeleteRule para cada AddRule.  
  
```  
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
  
## Vea también  
 [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Ubicación y tamaño de las reglas de restricción de formas BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)