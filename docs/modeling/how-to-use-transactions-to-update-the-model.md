---
title: 'Cómo: Usar transacciones para actualizar el modelo'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 590c355d391516def8f65579e5346281e335eea8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31950012"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Cómo: Usar transacciones para actualizar el modelo
Las transacciones Asegúrese de que los cambios realizados en el almacén se tratan como un grupo. Cambios que se agrupan pueden confirmar o revertir como una sola unidad.

 Cada vez que el código del programa modifica, agrega o elimina cualquier elemento en el almacén [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] SDK de visualización y modelado, debe hacerlo dentro de una transacción. Debe haber una instancia activa de <xref:Microsoft.VisualStudio.Modeling.Transaction> asociado con el almacén cuando se produce el cambio. Esto se aplica a todos los elementos del modelo, las relaciones, formas, diagramas y sus propiedades.

 El mecanismo de transacciones le ayuda a evitar estados incoherentes. Si se produce un error durante una transacción, se revierten todos los cambios. Si el usuario realiza un comando Deshacer, cada transacción reciente se trata como un solo paso. El usuario no puede deshacer partes de un cambio reciente, a menos que coloca explícitamente en transacciones independientes.

## <a name="opening-a-transaction"></a>Abrir una transacción
 Es el método más conveniente de administrar una transacción con un `using` instrucción dentro de un `try...catch` instrucción:

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

 Si una excepción que evita que la última `Commit()` se produce durante los cambios, el almacén se restablecerá a su estado anterior. Esto ayuda a asegurarse de que los errores no dejar el modelo en un estado incoherente.

 Puede realizar cualquier número de cambios dentro de una transacción. También puede abrir las nuevas transacciones dentro de una transacción activa. Las transacciones anidadas deben confirmar o revertir antes de la transacción finaliza que lo contiene. Para obtener más información, vea el ejemplo para el <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propiedad.

 Para realizar los cambios permanentes, debe `Commit` la transacción antes de que se elimina. Si se produce una excepción que no se detecta en la transacción, el almacén se restablecerá a su estado antes de los cambios.

## <a name="rolling-back-a-transaction"></a>Deshacer una transacción
 Para asegurarse de que el almacén permanece en o vuelve a su estado anterior a la transacción, puede utilizar cualquiera de estas tácticas:

1.  Genera una excepción que no se detecta en el ámbito de la transacción.

2.  Revertir explícitamente la transacción:

    ```
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Las transacciones no afectan a los objetos de almacén no
 Las transacciones sólo determinan el estado de la tienda. No se pueden deshacer los cambios parciales que se han realizado en los elementos externos, como archivos, bases de datos u objetos que se han declarado con los tipos normales fuera de la definición DSL.

 Si una excepción podría dejar este cambio incoherente con el almacén, debe tratar con esa posibilidad en el controlador de excepciones. Una manera de asegurarse de que los recursos externos sigan estando sincronizados con los objetos de almacén es acoplar cada objeto externo a un elemento en el almacén mediante el uso de controladores de eventos. Para obtener más información, consulte [controladores propagar cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Activar reglas al final de una transacción
 Al final de una transacción antes de que la transacción se deshace, se activan las reglas asociadas a elementos en el almacén. Cada regla es un método que se aplica a un elemento del modelo que ha cambiado. Por ejemplo, hay reglas "corregir" que actualizarán el estado de una forma cuando ha cambiado su elemento de modelo y que crean una forma cuando se crea un elemento del modelo. No hay ningún orden de activación especificado. Un cambio realizado por una regla puede desencadenar otra regla.

 Puede definir sus propias reglas. Para obtener más información acerca de las reglas, consulte [responder a y propagar los cambios](../modeling/responding-to-and-propagating-changes.md).

 Las reglas no se activan después de una acción de deshacer, una acción de rehacer o un comando de reversión.

## <a name="transaction-context"></a>Contexto de transacción
 Cada transacción tiene un diccionario en el que puede almacenar cualquier información que desee:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Esto es especialmente útil para transferir información entre las reglas.

## <a name="transaction-state"></a>Estado de la transacción
 En algunos casos que es necesario evitar propagar un cambio si se produce el cambio al deshacer o rehacer una transacción. Esto puede ocurrir, por ejemplo, si escribe un controlador de valores de propiedades que puede actualizar otro valor en el almacén. Dado que la operación de Deshacer restablece todos los valores en el almacén a su estado anterior, no es necesario calcular valores actualizados. Use este código:

```
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Las reglas se pueden desencadenar cuando el almacén está cargando inicialmente desde un archivo. Para evitar responder a estos cambios, use:

```
if (!this.Store.InSerializationTransaction) {...}

```