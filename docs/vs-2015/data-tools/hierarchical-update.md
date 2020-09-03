---
title: Actualización jerárquica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99e19bce34c2bc8578a062c87aaef10302589075
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670022"
---
# <a name="hierarchical-update"></a>Actualización jerárquica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La actualización jerárquica * hace referencia al proceso de volver a guardar los datos actualizados (de un conjunto de datos con dos o más tablas relacionadas) en una base de datos manteniendo las reglas de integridad referencial. La *integridad referencial* hace referencia a las reglas de coherencia proporcionadas por las restricciones en una base de datos que controlan el comportamiento de inserción, actualización y eliminación de registros relacionados. Por ejemplo, es la integridad referencial que exige la creación de un registro de cliente antes de permitir que se creen pedidos para ese cliente.  Para obtener más información sobre las relaciones de los conjuntos de datos, vea [relaciones en conjuntos de](../data-tools/relationships-in-datasets.md) datos.

 La característica de actualización jerárquica utiliza un `TableAdapterManager` objeto para administrar los objetos `TableAdapter` en un conjunto de elementos con tipo. El `TableAdapterManager` componente es una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] clase generada por, por lo que no forma parte de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Al arrastrar una tabla desde la ventana orígenes de datos a una página de Windows Forms o WPF, Visual Studio agrega una variable de tipo TableAdapterManager al formulario o la página y la ve en el diseñador en la bandeja de componentes. Para obtener información detallada sobre la `TableAdapterManager` clase, vea la sección de referencia de TableAdapterManager de [información general sobre TableAdapterManager](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).

 De forma predeterminada, un conjunto de DataSet trata las tablas relacionadas como "solo relaciones", lo que significa que no impone restricciones de clave externa. Puede modificar ese valor en tiempo de diseño mediante el Diseñador de DataSet. Seleccione la línea de relación entre dos tablas para abrir el cuadro de diálogo **relación** . Los cambios que realice aquí determinarán cómo se comporta TableAdapterManager cuando envía de nuevo los cambios de las tablas relacionadas a la base de datos.

## <a name="enablehierarchical-update-in-a-dataset"></a>Actualización de Enablehierarchical en un conjunto de DataSet
 De forma predeterminada, la actualización jerárquica está habilitada para todos los nuevos conjuntos de datos que se agregan o se crean en un proyecto. Active o desactive la actualización jerárquica estableciendo la propiedad **actualización jerárquica** de un conjunto de tipos en el diseñador de DataSet en **true** o **false**:

 ![Configuración de actualización jerárquica](../data-tools/media/hierarchical-update-setting.png "Configuración de actualización jerárquica")

## <a name="create-a-new-relation-between-tables"></a>Crear una nueva relación entre tablas
 Para crear una nueva relación entre dos tablas, en el Diseñador de DataSet, seleccione la barra de título de cada tabla, haga clic con el botón derecho y seleccione**Agregar relación**.

 ![Menú de agregar relación de actualización jerárquica](../data-tools/media/hierarchical-update-add-relation-menu.png "Menú de agregar relación de actualización jerárquica")

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Descripción de las restricciones Foreign Key, las actualizaciones en cascada y las eliminaciones
 Es importante saber cómo se crean las restricciones FOREIGN KEY y el comportamiento en cascada en la base de datos en el código del conjunto de datos generado.

 De forma predeterminada, las tablas de datos en un conjunto de datos se generan con relaciones (<xref:System.Data.DataRelation>) que coinciden con las relaciones en la base de datos. Sin embargo, la relación en el conjunto de datos no se genera como una restricción FOREIGN KEY. <xref:System.Data.DataRelation>Se configura como **relación solo** sin <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> o <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigor.

 De forma predeterminada, las actualizaciones y las eliminaciones en cascada están desactivadas, incluso si la relación de la base de datos establece que estén activadas. Por ejemplo, crear un nuevo cliente y un nuevo pedido y, a continuación, intentar guardar los datos puede producir un conflicto con las restricciones Foreign Key definidas en la base de datos. Para obtener más información, consulte [Cómo: configurar restricciones Foreign-Key en un conjunto de](https://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e)datos.

## <a name="set-the-order-to-perform-updates"></a>Establecer el orden para realizar actualizaciones
 Al establecer el orden para realizar actualizaciones, se establece el orden de las inserciones, actualizaciones y eliminaciones individuales que se necesitan para guardar todos los datos modificados en todas las tablas de un conjunto de datos. Cuando la actualización jerárquica está habilitada, primero se realizan las inserciones, después las actualizaciones y, por último, las eliminaciones. `TableAdapterManager` proporciona una propiedad `UpdateOrder` que se puede establecer para realizar primero las actualizaciones, después las inserciones y, por último, las eliminaciones.

> [!NOTE]
> Es importante comprender que el orden de actualización es inclusivo. Es decir, cuando se realizan las actualizaciones, las inserciones y, a continuación, se realizan eliminaciones para todas las tablas del conjunto de DataSet.

 Para establecer la `UpdateOrder` propiedad, después de arrastrar elementos desde la [ventana orígenes de datos](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) a un formulario, seleccione `TableAdapterManager` en la bandeja de componentes y, a continuación, establezca la `UpdateOrder` propiedad en la ventana **propiedades** . Para obtener más información, vea [Cómo: establecer el orden al realizar una actualización jerárquica](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Crear una copia de seguridad de un conjunto de copia de seguridad antes de realizar una actualización jerárquica
 Cuando se guardan datos (llamando al método `TableAdapterManager.UpdateAll()` ), `TableAdapterManager` intenta actualizar los datos para cada tabla en una transacción única. Si se produce un error en cualquier parte de la actualización en cualquier tabla, se revierte la transacción entera. En la mayoría de los casos, la reversión devuelve la aplicación a su estado original.

 Sin embargo, a veces se decide restaurar el conjunto de datos a partir de la copia de seguridad. Un ejemplo de esto puede producirse cuando se usan valores de incremento automático. Por ejemplo, si una operación de guardar no se realiza correctamente, los valores de incremento automático no se restablecen en el conjunto de resultados y el conjunto de resultados continúa creando valores de incremento automático. Esto deja un hueco en la numeración que podría no ser aceptable en la aplicación. En situaciones donde éste es un problema, `TableAdapterManager` proporciona una propiedad `BackupDataSetBeforeUpdate` que reemplaza el conjunto de datos existente con una copia de seguridad si se produce un error en la transacción.

> [!NOTE]
> La copia de seguridad solo está en memoria mientras el `TableAdapterManager.UpdateAll` método se está ejecutando. Por lo tanto, no hay acceso mediante programación a este conjunto de copia de seguridad porque reemplaza el conjunto de DataSet original o sale del ámbito en cuanto el `TableAdapterManager.UpdateAll` método termina de ejecutarse.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificar el código de guardado generado para realizar la actualización jerárquica
 Guarde en la base de datos los cambios de las tablas de datos relacionadas del conjunto de datos; para ello, llame al método `TableAdapterManager.UpdateAll` y pase el nombre del conjunto de datos que contiene las tablas relacionadas. Por ejemplo, ejecute el método `TableAdapterManager.UpdateAll(NorthwindDataset)` para enviar las actualizaciones de todas las tablas de NorthwindDataset a la base de datos back-end.

 Después de colocar en los elementos de la ventana **Orígenes de datos**, el código se agrega automáticamente al evento `Form_Load` para rellenar cada tabla (los métodos `TableAdapter.Fill`). También se agrega código al evento de clic del botón **Guardar** del <xref:System.Windows.Forms.BindingNavigator> para guardar los datos desde el conjunto de datos de nuevo a la base de datos (el método `TableAdapterManager.UpdateAll`).

 El código de guardado generado también contiene una línea de código que llama al método `CustomersBindingSource.EndEdit`. Más concretamente, llama al <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método de la primera <xref:System.Windows.Forms.BindingSource> que se agrega al formulario. En otras palabras, este código solo se genera para la primera tabla que se arrastra desde la ventana **orígenes de datos** hasta el formulario. La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el botón **Guardar**, todas las ediciones pendientes en ese control se confirman antes del guardado real (el método `TableAdapterManager.UpdateAll`).

> [!NOTE]
> El Diseñador de DataSet solo agrega el `BindingSource.EndEdit` código para la primera tabla que se coloca en el formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método `BindingSource.EndEdit` para cada tabla relacionada en el formulario. Para este tutorial, esto significa que tiene que agregar una llamada al método `OrdersBindingSource.EndEdit`.

#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Para actualizar el código para confirmar los cambios en las tablas relacionadas antes de guardar

1. Haga doble clic en el botón **Guardar**, en el <xref:System.Windows.Forms.BindingNavigator>, para abrir **Form1** en el Editor de código.

2. Agregue una línea de código para llamar al método `OrdersBindingSource.EndEdit` después de la línea que llama al método `CustomersBindingSource.EndEdit`. El código del evento de clic del botón **Guardar** debe tener un aspecto similar al siguiente:

    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]

   Además de confirmar los cambios en una tabla secundaria relacionada antes de guardar los datos en una base de datos, quizás también tenga que confirmar los registros primarios recién creados antes de agregar nuevos registros secundarios a un conjunto de datos. En otras palabras, quizás tenga que agregar el nuevo registro primario (Customer) al conjunto de datos para que las restricciones de clave externa permitan agregar nuevos registros secundarios (Orders) al conjunto de datos. Para ello, puede usar el evento `BindingSource.AddingNew` secundario.

> [!NOTE]
> Si tiene que confirmar nuevos registros primarios depende del tipo de control que se utiliza para enlazar con el origen de datos. En este tutorial, usará controles individuales para enlazar con la tabla primaria. Esto requiere que el código adicional confirme el nuevo registro primario. Si en su lugar se mostraban los registros primarios en un control de enlace complejo como <xref:System.Windows.Forms.DataGridView> , esta <xref:System.Windows.Forms.BindingSource.EndEdit%2A> llamada adicional para el registro principal no sería necesaria. Esto se debe a que la funcionalidad de enlace a datos subyacente del control controla la confirmación de los nuevos registros.

#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Para agregar código para confirmar los registros primarios en el conjunto de datos antes de agregar registros secundarios

1. Cree un controlador para el evento `OrdersBindingSource.AddingNew`.

    - Abra **Form1** en la vista Diseño, seleccione **OrdersBindingSource** en la bandeja de componentes, seleccione **eventos** en la ventana **propiedades** y, a continuación, haga doble clic en el evento **AddingNew** .

2. Agregue una línea de código al controlador de eventos que llama al `CustomersBindingSource.EndEdit` método. El código del controlador de evento `OrdersBindingSource_AddingNew` debe tener un aspecto similar al siguiente:

     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]

## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager
 De forma predeterminada, `TableAdapterManager` se genera una clase cuando se crea un conjunto de DataSet que contiene tablas relacionadas. Para evitar que se genere la clase, cambie el valor de la `Hierarchical Update` propiedad del conjunto de valores a false. Cuando se arrastra una tabla que tiene una relación en la superficie de diseño de una página de Windows Forms o de WPF, Visual Studio declara una variable miembro de la clase. Si no usa DataBinding, tendrá que declarar manualmente la variable.

 La `TableAdapterManager` clase no forma parte de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Por lo tanto, no se puede buscar en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de elementos.

 A continuación se muestran los métodos y las propiedades de la clase que se usan con frecuencia `TableAdapterManager` :

|Member|Descripción|
|------------|-----------------|
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|
|Propiedad`BackUpDataSetBeforeUpdate`|Determina si se va a crear una copia de seguridad del conjunto de archivos antes de ejecutar el `TableAdapterManager.UpdateAll` método. Booleano.|
|*TableName* `TableAdapter` propiedad|Representa un `TableAdapter` . El generado `TableAdapterManager` contiene una propiedad para cada `TableAdapter` que administra. Por ejemplo, un conjunto de DataSet con una tabla Customers y Orders se genera con un objeto `TableAdapterManager` que contiene `CustomersTableAdapter` `OrdersTableAdapter` las propiedades y.|
|Propiedad`UpdateOrder`|Controla el orden de los comandos de inserción, actualización y eliminación individuales. Establézcalo en uno de los valores de la `TableAdapterManager.UpdateOrderOption` enumeración.<br /><br /> De forma predeterminada, `UpdateOrder` se establece en **InsertUpdateDelete**. Esto significa que las inserciones, las actualizaciones y las eliminaciones se realizan para todas las tablas del conjunto de DataSet. Para obtener más información, vea [Cómo: establecer el orden al realizar una actualización jerárquica](https://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|

## <a name="see-also"></a>Consulte también
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)
