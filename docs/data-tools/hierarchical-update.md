---
title: Actualización jerárquica
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 33ca9f91c9b1105af43af21a91f25be13e153aa9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648448"
---
# <a name="hierarchical-update"></a>Actualización jerárquica

La *actualización jerárquica* hace referencia al proceso de guardar los datos actualizados (de un conjunto de datos con dos o más tablas relacionadas) de nuevo en una base de datos manteniendo las reglas de integridad referencial. La *integridad referencial* hace referencia a las reglas de coherencia proporcionadas por las restricciones en una base de datos que controlan el comportamiento de inserción, actualización y eliminación de registros relacionados. Por ejemplo, es la integridad referencial que exige la creación de un registro de cliente antes de permitir que se creen pedidos para ese cliente.  Para obtener más información sobre las relaciones de los conjuntos de datos, vea [relaciones en conjuntos de](../data-tools/relationships-in-datasets.md)datos.

La característica de actualización jerárquica usa un `TableAdapterManager` para administrar la `TableAdapter`s en un conjunto de un conjunto de un tipo. El componente `TableAdapterManager` es una clase generada por Visual Studio, no un tipo .NET. Al arrastrar una tabla desde la ventana **orígenes de datos** a una página de Windows Forms o WPF, Visual Studio agrega una variable de tipo TableAdapterManager al formulario o la página y la ve en el diseñador en la bandeja de componentes. Para obtener información detallada sobre la clase `TableAdapterManager`, vea la sección referencia de TableAdapterManager de [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

De forma predeterminada, un conjunto de DataSet trata las tablas relacionadas como "solo relaciones", lo que significa que no impone restricciones de clave externa. Puede modificar ese valor en tiempo de diseño mediante el **Diseñador de DataSet**. Seleccione la línea de relación entre dos tablas para abrir el cuadro de diálogo **relación** . Los cambios que realice aquí determinarán cómo se comporta el `TableAdapterManager` cuando envía de nuevo los cambios de las tablas relacionadas a la base de datos.

## <a name="enable-hierarchical-update-in-a-dataset"></a>Habilitar la actualización jerárquica en un conjunto de DataSet

De forma predeterminada, la actualización jerárquica está habilitada para todos los nuevos conjuntos de datos que se agregan o se crean en un proyecto. Active o desactive la actualización jerárquica estableciendo la propiedad **actualización jerárquica** de un conjunto de los conjuntos de los conjuntos de valores en **true** o **false**:

![Configuración de actualización jerárquica](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>Crear una nueva relación entre tablas

Para crear una nueva relación entre dos tablas, en el Diseñador de DataSet, seleccione la barra de título de cada tabla, haga clic con el botón derecho y seleccione **Agregar relación**.

![Menú de agregar relación de actualización jerárquica](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Descripción de las restricciones Foreign Key, las actualizaciones en cascada y las eliminaciones

Es importante saber cómo se crean las restricciones FOREIGN KEY y el comportamiento en cascada en la base de datos en el código del conjunto de datos generado.

De forma predeterminada, las tablas de datos en un conjunto de datos se generan con relaciones (<xref:System.Data.DataRelation>) que coinciden con las relaciones en la base de datos. Sin embargo, la relación en el conjunto de datos no se genera como una restricción FOREIGN KEY. El <xref:System.Data.DataRelation> se configura como **relación solo** sin <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> ni <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigor.

De forma predeterminada, las actualizaciones y las eliminaciones en cascada están desactivadas, incluso si la relación de la base de datos establece que estén activadas. Por ejemplo, crear un nuevo cliente y un nuevo pedido y, a continuación, intentar guardar los datos puede producir un conflicto con las restricciones Foreign Key definidas en la base de datos. Para obtener más información, vea [desactivar restricciones al llenar un conjunto](turn-off-constraints-while-filling-a-dataset.md)de datos.

## <a name="set-the-order-to-perform-updates"></a>Establecer el orden para realizar actualizaciones

Al establecer el orden para realizar actualizaciones, se establece el orden de las inserciones, actualizaciones y eliminaciones individuales que se necesitan para guardar todos los datos modificados en todas las tablas de un conjunto de datos. Cuando la actualización jerárquica está habilitada, primero se realizan las inserciones, después las actualizaciones y, por último, las eliminaciones. `TableAdapterManager` proporciona una propiedad `UpdateOrder` que se puede establecer para realizar primero las actualizaciones, después las inserciones y, por último, las eliminaciones.

> [!NOTE]
> Es importante comprender que el orden de actualización es inclusivo. Es decir, cuando se realizan las actualizaciones, las inserciones y eliminaciones se realizan para todas las tablas del conjunto de DataSet.

Para establecer la propiedad `UpdateOrder`, después de arrastrar los elementos desde la [ventana orígenes de datos](add-new-data-sources.md#data-sources-window) hasta un formulario, seleccione el `TableAdapterManager` en la bandeja de componentes y, a continuación, establezca la propiedad `UpdateOrder` en la ventana **propiedades** .

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Crear una copia de seguridad de un conjunto de copia de seguridad antes de realizar una actualización jerárquica

Cuando se guardan datos (llamando al método `TableAdapterManager.UpdateAll()` ), `TableAdapterManager` intenta actualizar los datos para cada tabla en una transacción única. Si se produce un error en cualquier parte de la actualización en cualquier tabla, se revierte la transacción entera. En la mayoría de los casos, la reversión devuelve la aplicación a su estado original.

Sin embargo, a veces se decide restaurar el conjunto de datos a partir de la copia de seguridad. Un ejemplo de esto puede producirse cuando se usan valores de incremento automático. Por ejemplo, si una operación de guardar no se realiza correctamente, los valores de incremento automático no se restablecen en el conjunto de resultados y el conjunto de resultados continúa creando valores de incremento automático. Esto deja un hueco en la numeración que podría no ser aceptable en la aplicación. En situaciones donde éste es un problema, `TableAdapterManager` proporciona una propiedad `BackupDataSetBeforeUpdate` que reemplaza el conjunto de datos existente con una copia de seguridad si se produce un error en la transacción.

> [!NOTE]
> La copia de seguridad solo está en memoria mientras el método `TableAdapterManager.UpdateAll` se está ejecutando. Por lo tanto, no hay acceso mediante programación a este conjunto de copia de seguridad porque reemplaza el conjunto de DataSet original o sale del ámbito en cuanto el método de `TableAdapterManager.UpdateAll` termina de ejecutarse.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificar el código de guardado generado para realizar la actualización jerárquica

Guarde en la base de datos los cambios de las tablas de datos relacionadas del conjunto de datos; para ello, llame al método `TableAdapterManager.UpdateAll` y pase el nombre del conjunto de datos que contiene las tablas relacionadas. Por ejemplo, ejecute el método `TableAdapterManager.UpdateAll(NorthwindDataset)` para enviar las actualizaciones de todas las tablas de NorthwindDataset a la base de datos back-end.

Después de colocar en los elementos de la ventana **Orígenes de datos**, el código se agrega automáticamente al evento `Form_Load` para rellenar cada tabla (los métodos `TableAdapter.Fill`). También se agrega código al evento de clic del botón **Guardar** del <xref:System.Windows.Forms.BindingNavigator> para guardar los datos desde el conjunto de datos de nuevo a la base de datos (el método `TableAdapterManager.UpdateAll`).

El código de guardado generado también contiene una línea de código que llama al método `CustomersBindingSource.EndEdit`. Más concretamente, llama al método <xref:System.Windows.Forms.BindingSource.EndEdit%2A> del primer <xref:System.Windows.Forms.BindingSource>that que se agrega al formulario. En otras palabras, este código solo se genera para la primera tabla que se arrastra desde la ventana **orígenes de datos** hasta el formulario. La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

> [!NOTE]
> En el **Diseñador de DataSet** solo se agrega el código `BindingSource.EndEdit` de la primera tabla que se coloca en el formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método `BindingSource.EndEdit` para cada tabla relacionada en el formulario. Para este tutorial, esto significa que tiene que agregar una llamada al método `OrdersBindingSource.EndEdit`.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Para actualizar el código para confirmar los cambios en las tablas relacionadas antes de guardar

1. Haga doble clic en el botón **Guardar**, en el <xref:System.Windows.Forms.BindingNavigator>, para abrir **Form1** en el Editor de código.

2. Agregue una línea de código para llamar al método `OrdersBindingSource.EndEdit` después de la línea que llama al método `CustomersBindingSource.EndEdit`. El código del evento de clic del botón **Guardar** debe tener un aspecto similar al siguiente:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

Además de confirmar los cambios en una tabla secundaria relacionada antes de guardar los datos en una base de datos, quizás también tenga que confirmar los registros primarios recién creados antes de agregar nuevos registros secundarios a un conjunto de datos. En otras palabras, puede que tenga que agregar el nuevo registro primario (`Customer`) al conjunto de registros antes de que las restricciones Foreign Key permitan que se agreguen nuevos registros secundarios (`Orders`) al DataSet. Para ello, puede usar el evento `BindingSource.AddingNew` secundario.

> [!NOTE]
> Si tiene que confirmar nuevos registros primarios depende del tipo de control que se utiliza para enlazar con el origen de datos. En este tutorial, usará controles individuales para enlazar con la tabla primaria. Esto requiere que el código adicional confirme el nuevo registro primario. Si en su lugar se mostraban los registros primarios en un control de enlace complejo como el <xref:System.Windows.Forms.DataGridView>, esta llamada de <xref:System.Windows.Forms.BindingSource.EndEdit%2A> adicional para el registro principal no sería necesaria. Esto se debe a que la funcionalidad de enlace a datos subyacente del control controla la confirmación de los nuevos registros.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Para agregar código para confirmar los registros primarios en el conjunto de datos antes de agregar registros secundarios

1. Cree un controlador para el evento `OrdersBindingSource.AddingNew`.

    - Abra **Form1** en la vista Diseño, seleccione **OrdersBindingSource** en la bandeja de componentes, seleccione **eventos** en la ventana **propiedades** y, a continuación, haga doble clic en el evento **AddingNew** .

2. Agregue una línea de código al controlador de eventos que llama al método `CustomersBindingSource.EndEdit`. El código del controlador de evento `OrdersBindingSource_AddingNew` debe tener un aspecto similar al siguiente:

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager

De forma predeterminada, se genera una clase de `TableAdapterManager` cuando se crea un conjunto de DataSet que contiene tablas relacionadas. Para evitar que se genere la clase, cambie el valor de la propiedad `Hierarchical Update` del conjunto de valores a false. Cuando se arrastra una tabla que tiene una relación en la superficie de diseño de una página de Windows Forms o de WPF, Visual Studio declara una variable miembro de la clase. Si no usa DataBinding, tendrá que declarar manualmente la variable.

La clase `TableAdapterManager` no es un tipo .NET. Por lo tanto, no se puede buscar en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de elementos.

A continuación se muestran los métodos y las propiedades que se usan con frecuencia de la clase `TableAdapterManager`:

|Miembro|Descripción|
|------------|-----------------|
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|
|Propiedad`BackUpDataSetBeforeUpdate`|Determina si se va a crear una copia de seguridad del conjunto de archivos antes de ejecutar el método `TableAdapterManager.UpdateAll`. Booleano.|
|propiedad *tableName* `TableAdapter`|Representa un `TableAdapter`. El `TableAdapterManager` generado contiene una propiedad para cada `TableAdapter` que administra. Por ejemplo, un conjunto de DataSet con una tabla Customers y Orders se genera con una `TableAdapterManager` que contiene las propiedades `CustomersTableAdapter` y `OrdersTableAdapter`.|
|Propiedad`UpdateOrder`|Controla el orden de los comandos de inserción, actualización y eliminación individuales. Establezca este valor en uno de los valores de la enumeración `TableAdapterManager.UpdateOrderOption`.<br /><br /> De forma predeterminada, la `UpdateOrder` se establece en **InsertUpdateDelete**. Esto significa que las inserciones, las actualizaciones y las eliminaciones se realizan para todas las tablas del conjunto de DataSet.|

## <a name="see-also"></a>Vea también

- [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
