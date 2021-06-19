---
title: 'Cómo: Usar transacciones para actualizar el modelo'
description: Obtenga información sobre que las transacciones se asegura de que los cambios realizados en el almacén se tratan como un grupo y cómo usar transacciones para actualizar el modelo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e91e569573076d1614a9fa946b67f3bda01e6fba
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390547"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Cómo: Usar transacciones para actualizar el modelo
Las transacciones se asegura de que los cambios realizados en el almacén se tratan como un grupo. Los cambios que se agrupan se pueden realizar o revertir como una sola unidad.

 Cada vez que el código del programa modifica, agrega o elimina cualquier elemento del Almacén en el SDK de visualización y modelado de Visual Studio, debe hacerlo dentro de una transacción. Debe haber una instancia activa de asociada <xref:Microsoft.VisualStudio.Modeling.Transaction> al almacén cuando se produce el cambio. Esto se aplica a todos los elementos del modelo, relaciones, formas, diagramas y sus propiedades.

 El mecanismo de transacción ayuda a evitar estados incoherentes. Si se produce un error durante una transacción, todos los cambios se revierte. Si el usuario realiza un comando Deshacer, cada transacción reciente se trata como un solo paso. El usuario no puede deshacer partes de un cambio reciente, a menos que las coloque explícitamente en transacciones independientes.

## <a name="opening-a-transaction"></a>Apertura de una transacción
 El método más conveniente para administrar una transacción es con una `using` instrucción incluida en una instrucción `try...catch` :

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

 Si se produce una excepción que impide la final durante los `Commit()` cambios, store se restablecerá a su estado anterior. Esto le ayuda a asegurarse de que los errores no dejan el modelo en un estado incoherente.

 Puede realizar cualquier número de cambios dentro de una transacción. Puede abrir nuevas transacciones dentro de una transacción activa. Las transacciones anidadas deben confirmarse o revertirse antes de que finalice la transacción que lo contiene. Para obtener más información, vea el ejemplo de la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> propiedad .

 Para que los cambios se realicen de forma permanente, debe `Commit` realizar la transacción antes de que se deseche. Si se produce una excepción que no se detecta dentro de la transacción, store se restablecerá a su estado antes de los cambios.

## <a name="rolling-back-a-transaction"></a>Revertir una transacción
 Para asegurarse de que store permanece en su estado antes de la transacción, puede usar cualquiera de estas tácticas:

1. Generar una excepción que no se detecta dentro del ámbito de la transacción.

2. Revierte explícitamente la transacción:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Las transacciones no afectan a objetos que no son de almacén
 Las transacciones solo rigen el estado del almacén. No pueden deshacer los cambios parciales realizados en elementos externos, como archivos, bases de datos u objetos declarados con tipos normales fuera de la definición de DSL.

 Si una excepción puede dejar este cambio incoherente con store, debe tratar esa posibilidad en el controlador de excepciones. Una manera de asegurarse de que los recursos externos permanecen sincronizados con los objetos Store es asociar cada objeto externo a un elemento en el almacén mediante controladores de eventos. Para obtener más información, vea [Controladores de eventos Propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Las reglas se disparan al final de una transacción
 Al final de una transacción, antes de que se desechar la transacción, se desencadenan las reglas adjuntas a los elementos del almacén. Cada regla es un método que se aplica a un elemento de modelo que ha cambiado. Por ejemplo, hay reglas de "corrección" que actualizan el estado de una forma cuando su elemento de modelo ha cambiado y que crean una forma cuando se crea un elemento de modelo. No hay ningún orden de activación especificado. Un cambio realizado por una regla puede abrir otra regla.

 Puede definir sus propias reglas. Para obtener más información sobre las reglas, vea [Responder a y propagar cambios.](../modeling/responding-to-and-propagating-changes.md)

 Las reglas no se pueden ejecutar después de una deshacer, una rehacer o un comando de reversión.

## <a name="transaction-context"></a>Contexto de transacción
 Cada transacción tiene un diccionario en el que puede almacenar cualquier información que desee:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Esto es especialmente útil para transferir información entre reglas.

## <a name="transaction-state"></a>Estado de las transacciones
 En algunos casos, debe evitar propagar un cambio si el cambio se debe a la deshacer o rehacer una transacción. Esto puede ocurrir, por ejemplo, si escribe un controlador de valores de propiedad que puede actualizar otro valor en store. Dado que la operación de deshacer restablece todos los valores del Almacén a sus estados anteriores, no es necesario calcular los valores actualizados. Use este código:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Las reglas se pueden abrir cuando el almacén se carga inicialmente desde un archivo. Para evitar responder a estos cambios, use:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
