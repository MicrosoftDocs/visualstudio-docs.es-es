---
title: 'Cómo: Usar transacciones para actualizar el modelo'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a08ea67477f42008c35b6f141351beaeee03d27b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661135"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Cómo: Usar transacciones para actualizar el modelo
Las transacciones garantizan que los cambios realizados en el almacén se tratan como un grupo. Los cambios que se agrupan se pueden confirmar o revertir como una sola unidad.

 Cada vez que el código de programa modifica, agrega o elimina cualquier elemento del almacén en el SDK de visualización y modelado de Visual Studio, debe hacerlo dentro de una transacción. Debe haber una instancia activa de <xref:Microsoft.VisualStudio.Modeling.Transaction> asociada al almacén cuando se produce el cambio. Esto se aplica a todos los elementos del modelo, las relaciones, las formas, los diagramas y sus propiedades.

 El mecanismo de transacción le ayuda a evitar Estados incoherentes. Si se produce un error durante una transacción, se revierten todos los cambios. Si el usuario realiza un comando Deshacer, cada transacción reciente se trata como un solo paso. El usuario no puede deshacer partes de un cambio reciente, a menos que los coloque explícitamente en transacciones independientes.

## <a name="opening-a-transaction"></a>Abrir una transacción
 El método más práctico para administrar una transacción es con una instrucción `using` que se incluye en una instrucción `try...catch`:

```csharp
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

 Si se produce una excepción que impide el `Commit()` final durante los cambios, el almacén se restablecerá a su estado anterior. Esto le ayuda a asegurarse de que los errores no salen del modelo en un estado incoherente.

 Puede realizar cualquier número de cambios dentro de una transacción. Puede abrir transacciones nuevas dentro de una transacción activa. Las transacciones anidadas deben confirmarse o revertirse antes de que finalice la transacción contenedora. Para obtener más información, vea el ejemplo de la propiedad <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>.

 Para que los cambios sean permanentes, debe `Commit` la transacción antes de que se elimine. Si se produce una excepción que no se detecta dentro de la transacción, el almacén se restablecerá a su estado anterior a los cambios.

## <a name="rolling-back-a-transaction"></a>Deshacer una transacción
 Para asegurarse de que el almacén permanece en o se revierte a su estado anterior a la transacción, puede usar cualquiera de estas tácticas:

1. Genera una excepción que no se detecta dentro del ámbito de la transacción.

2. Revertir explícitamente la transacción:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Las transacciones no afectan a los objetos que no son de almacén
 Las transacciones solo rigen el estado del almacén. No pueden deshacer los cambios parciales realizados en elementos externos como archivos, bases de datos u objetos que se han declarado con tipos normales fuera de la definición de DSL.

 Si una excepción podría dejar tal cambio incoherente con el almacén, debe tratar esa posibilidad en el controlador de excepciones. Una manera de asegurarse de que los recursos externos permanecen sincronizados con los objetos de almacén es acoplar cada objeto externo a un elemento en el almacén mediante controladores de eventos. Para obtener más información, vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Las reglas se activan al final de una transacción
 Al final de una transacción, antes de que se elimine la transacción, se activan las reglas adjuntas a los elementos del almacén. Cada regla es un método que se aplica a un elemento de modelo que ha cambiado. Por ejemplo, hay reglas de "corrección" que actualizan el estado de una forma cuando su elemento de modelo ha cambiado y que crean una forma cuando se crea un elemento de modelo. No hay ningún orden de activación especificado. Un cambio realizado por una regla puede activar otra regla.

 Puede definir sus propias reglas. Para obtener más información acerca de las reglas, consulte [responder a los cambios y propagarlos](../modeling/responding-to-and-propagating-changes.md).

 Las reglas no se activan después de un comando Deshacer, rehacer o rehacer.

## <a name="transaction-context"></a>Contexto de transacción
 Cada transacción tiene un diccionario en el que puede almacenar cualquier información que desee:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Esto es especialmente útil para transferir información entre reglas.

## <a name="transaction-state"></a>Estado de la transacción
 En algunos casos, debe evitar propagar un cambio si el cambio se debe a deshacer o rehacer una transacción. Esto puede ocurrir, por ejemplo, si escribe un controlador de valores de propiedad que puede actualizar otro valor en el almacén. Dado que la operación de deshacer restablece todos los valores del almacén a sus Estados anteriores, no es necesario calcular los valores actualizados. Use este código:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Las reglas se pueden activar cuando el almacén se carga inicialmente desde un archivo. Para evitar responder a estos cambios, use:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```