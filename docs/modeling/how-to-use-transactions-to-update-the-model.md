---
title: Procedimiento Usar transacciones para actualizar el modelo
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a7514e3ff0c876a669f514a7e17bb02b73c19c2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075030"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procedimiento Usar transacciones para actualizar el modelo
Las transacciones Asegúrese de que los cambios realizados en el almacén se tratan como un grupo. Los cambios que se agrupan pueden ser confirmados o revertidos como una sola unidad.

 Siempre que modifica el código del programa, agrega o elimina cualquier elemento en el Store en Visual Studio SDK de visualización y modelado, debe hacerlo dentro de una transacción. Debe haber una instancia activa de <xref:Microsoft.VisualStudio.Modeling.Transaction> asociada con el Store cuando se produce el cambio. Esto se aplica a todos los elementos del modelo, las relaciones, formas, diagramas y sus propiedades.

 El mecanismo de transacción ayuda a evitar estados incoherentes. Si se produce un error durante una transacción, se revierten todos los cambios. Si el usuario realiza un comando de deshacer, cada transacción reciente se trata como un solo paso. El usuario no puede deshacer partes de un cambio reciente, a menos que ponerlos explícitamente en transacciones independientes.

## <a name="opening-a-transaction"></a>Apertura de una transacción
 Es el método más conveniente de administrar una transacción con un `using` instrucción entre un `try...catch` instrucción:

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

 Si una excepción que impide que el último `Commit()` se produce durante los cambios, se restablecerá el Store a su estado anterior. Esto ayuda a asegurarse de que los errores no dejar el modelo en un estado incoherente.

 Puede realizar cualquier número de cambios dentro de una transacción. Puede abrir nuevas transacciones dentro de una transacción activa. Las transacciones anidadas deben confirmar o revertir antes de que finalice transacciones que lo contiene. Para obtener más información, vea el ejemplo de la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propiedad.

 Para que los cambios permanentes, debe `Commit` la transacción antes de eliminarlas. Si se produce una excepción que no se captura dentro de la transacción, se restablecerá a su estado antes de que cambie el Store.

## <a name="rolling-back-a-transaction"></a>Deshacer una transacción
 Para asegurarse de que permanece en el Store o se revierte a su estado anterior a la transacción, puede utilizar cualquiera de estas tácticas:

1. Generar una excepción que no se captura dentro del ámbito de la transacción.

2. Revertir explícitamente la transacción:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Las transacciones no afectan a los objetos no-Store
 Las transacciones solo controlan el estado de la Store. No se puede deshacer los cambios parciales que se realizaron en los elementos externos, como archivos, bases de datos u objetos que se han declarado con los tipos normales fuera de la definición de DSL.

 Si una excepción, podría dejar un cambio tan coherente con el Store, debe tratar con esa posibilidad en el controlador de excepciones. Una manera de asegurarse de que los recursos externos sigan estando sincronizados con los objetos Store es acoplar cada objeto externo a un elemento en el almacén mediante el uso de controladores de eventos. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Activación de reglas al final de una transacción
 Al final de una transacción antes de elimina la transacción, se activan las reglas asociadas a elementos en el almacén. Cada regla es un método que se aplica a un elemento de modelo que ha cambiado. Por ejemplo, hay reglas "corregir" que actualizan el estado de una forma cuando ha cambiado su elemento de modelo y que crear una forma cuando se crea un elemento de modelo. No hay ningún orden de activación especificado. Un cambio realizado por una regla puede desencadenar otra regla.

 Puede definir sus propias reglas. Para obtener más información acerca de las reglas, consulte [responde a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).

 Las reglas no se activan después de una operación de deshacer, una operación de rehacer o un comando de recuperación.

## <a name="transaction-context"></a>Contexto de transacción
 Cada transacción tiene un diccionario en el que puede almacenar cualquier información que desee:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Esto es especialmente útil para transferir información entre reglas.

## <a name="transaction-state"></a>Estado de transacción
 En ocasiones, es necesario para evitar propagar un cambio si se produce el cambio al deshacer o rehacer una transacción. Esto puede ocurrir, por ejemplo, si escribe un controlador de valor de propiedad que se puede actualizar otro valor en el Store. Dado que la operación de Deshacer restablece todos los valores en el Store a su estado anterior, no es necesario calcular los valores actualizados. Use este código:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Las reglas se pueden desencadenar cuando el almacén que se cargó inicialmente desde un archivo. Para evitar responder a estos cambios, use:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```