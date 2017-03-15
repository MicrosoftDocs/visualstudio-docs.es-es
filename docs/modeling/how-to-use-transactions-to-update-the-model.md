---
title: "C&#243;mo: Usar transacciones para actualizar el modelo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 7
---
# C&#243;mo: Usar transacciones para actualizar el modelo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las transacciones garantizan que los cambios realizados en el almacén se tratarán como grupo.  Los cambios se agrupan que se pueden confirmar o revertir como una unidad.  
  
 Cuando el código de programa modifique, agregue, o elimine cualquier elemento del almacén en la vista de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y SDK de modelado, debe hacerlo dentro de una transacción.  Debe existir una instancia activa de <xref:Microsoft.VisualStudio.Modeling.Transaction> asociado al almacén cuando ocurre el cambio.  Esto se aplica a todos los elementos de modelo, relaciones, las formas, los diagramas, y sus propiedades.  
  
 Ayuda del mecanismo de la transacción impide a estados incoherentes.  Si se produce un error durante una transacción, todos los cambios se revierten.  Si el usuario ejecuta un comando undo, cada transacción reciente se trata como un solo paso.  El usuario no puede las partes de la fase de reversión de un cambio reciente, a menos que explícitamente las coloque en transacciones independientes.  
  
## Abrir una transacción  
 El método más cómoda de administrar una transacción está con una instrucción de `using` agregada en una instrucción de `try...catch` :  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Si una excepción que evita `Commit()`final durante los cambios, el almacén se restaurará el estado anterior.  Esto ayuda a asegurarse de que los errores no permiten el modelo en un estado incoherente.  
  
 Puede realizar cualquier número de cambios dentro de una transacción.  Puede abrir nuevas transacciones dentro de una transacción activa.  Transacciones anidadas deben confirmarse o revertirse antes de que finalice la transacción que contienen.  Para obtener más información, vea el ejemplo para la propiedad de <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> .  
  
 Para crear la permanente de los cambios, debe `Commit` la transacción antes de eliminar.  Si se produce una excepción que no se detecta en la transacción, el almacén se restaurará el estado antes de los cambios.  
  
## Revertir una transacción  
 Para garantizar que el almacén permanezca en o revierta a su estado anterior de la transacción, puede utilizar cualquiera de estas tácticas:  
  
1.  Inicie una excepción que no se detecte dentro del ámbito de la transacción.  
  
2.  Explícitamente revertir la transacción:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## Las transacciones no afectan a objetos de No\-Almacén  
 Las transacciones rigen sólo el estado del almacén.  No pueden realizar cambios parciales de deshacer realizados en los elementos externos como archivos, bases de datos, u objetos declarados con tipos normales fuera de la definición del ADSL.  
  
 Si una excepción podría dejar el cambio incoherente con el almacén, debe tratar con esa posibilidad en el controlador de excepciones.  Una manera de asegurarse de que los recursos externos sigan sincronizados con los objetos de almacén es acoplar cada objeto externo a un elemento de almacén mediante controladores de eventos.  Para obtener más información, vea [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## Activación de las reglas del final de una transacción  
 Al final de una transacción, antes de eliminar la transacción, las reglas asociadas a los elementos en el almacén se active.  Cada regla es un método que se aplica a un elemento de modelo que ha cambiado.  Por ejemplo, hay “corrige hacia arriba” reglas que actualizan el estado de una forma cuando el elemento modelo ha cambiado, y que crean una forma cuando se crea un elemento de modelo.  No hay ningún orden de desencadenamiento especificado.  Un cambio realizado por una regla puede activar otra regla.  
  
 Puede definir dispone de reglas.  Para obtener más información sobre las reglas, consulte [Responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).  
  
 Las reglas no desencadenan después de una operación de deshacer, una operación de rehacer, o un comando rollback.  
  
## contexto de transacción  
 Cada transacción tiene un diccionario en el que puede almacenar cualquier información que desee:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Esto es especialmente útil para transferir información entre las reglas.  
  
## estado de la transacción  
 En algunos casos necesita evitar propagar un cambio si el cambio está provocado deshaciendo o rehaciendo una transacción.  Esto puede suceder, por ejemplo, si escribe un controlador de valores de propiedad que pueda actualizar otro valor en el almacén.  Dado que la operación de deshacer restablece todos los valores en el almacén a sus estados anteriores, no es necesario calcular valores actualizados.  Use este código:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Las reglas pueden desencadenar cuando el almacén se carga inicialmente de un archivo.  para evitar responder a estos cambios, utilice:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```