---
title: "Actualización jerárquica | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b02ef945136297287d18c2b29ea2d3afab1b3683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="hierarchical-update"></a>Actualización jerárquica
*Actualización jerárquica* hace referencia al proceso de guardar los datos actualizados (de un conjunto de datos con dos o más tablas relacionadas) a una base de datos manteniendo las reglas de integridad referencial. *La integridad referencial* hace referencia a las reglas de coherencia proporcionadas por las restricciones en una base de datos que controlan el comportamiento de insertar, actualizar y eliminar registros relacionados. Por ejemplo, es integridad referencial que exige la creación de un registro de cliente antes de permitir que los pedidos se va a crearse para ese cliente.  Para obtener más información acerca de las relaciones en conjuntos de datos, vea [relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)  
  
 La característica de actualización jerárquica usa un `TableAdapterManager` para administrar el `TableAdapter`s en un conjunto de datos con tipo. El `TableAdapterManager` componente es un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-generado (clase), por lo que no forma parte de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Cuando se arrastra una tabla desde la ventana de orígenes de datos a un formulario Windows Forms o la página WPF, Visual Studio agrega una variable de tipo TableAdapterManager al formulario o la página y se muestra en el diseñador en la Bandeja de componentes. Para obtener información detallada sobre la `TableAdapterManager` de clases, vea la sección de referencia de TableAdapterManager de [TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 De forma predeterminada, un conjunto de datos trata las tablas relacionadas como "solo, relaciones" lo que significa que no obliga a usar restricciones foreign key. Puede modificar esa configuración en tiempo de diseño mediante el Diseñador de Dataset. Seleccione la línea de relación entre dos tablas para que aparezca el **relación** cuadro de diálogo. Los cambios que realice aquí determinarán cómo comporta el TableAdapterManager al que enviar los cambios en las tablas relacionadas en la base de datos.  
  
## <a name="enable-hierarchical-update-in-a-dataset"></a>Habilitar la actualización jerárquica en un conjunto de datos  
 De forma predeterminada, la actualización jerárquica está habilitada para todos los nuevos conjuntos de datos que se agregan o se crean en un proyecto. Activar o desactivar la actualización jerárquica estableciendo la **actualización jerárquica** propiedad de un conjunto de datos con tipo en el conjunto de datos **True** o **False**:  
  
 ![Configuración de actualización jerárquica](../data-tools/media/hierarchical-update-setting.png "la configuración de actualización jerárquica")  
  
## <a name="create-a-new-relation-between-tables"></a>Crear a una nueva relación entre tablas  
 Para crear una nueva relación entre dos tablas, en el Diseñador de Dataset, seleccione la barra de título de cada tabla, a continuación, haga clic en y seleccione **agregar relación**.  
  
 ![Actualización jerárquica Agregar menú relación](../data-tools/media/hierarchical-update-add-relation-menu.png "actualización jerárquica agregar menús de relación")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Comprender las restricciones foreign key, las actualizaciones en cascada y las eliminaciones  
 Es importante entender las restricciones foreign key cómo y comportamiento en cascada en la base de datos se crean en el código de conjunto de datos generado.  
  
 De forma predeterminada, las tablas de datos en un conjunto de datos se generan con relaciones (<xref:System.Data.DataRelation>) que coinciden con las relaciones en la base de datos. Sin embargo, la relación en el conjunto de datos no se genera como una restricción FOREIGN KEY. El <xref:System.Data.DataRelation> está configurado como **sólo relación** sin <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> o <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigor.  
  
 De forma predeterminada, las actualizaciones y las eliminaciones en cascada están desactivadas, incluso si la relación de la base de datos establece que estén activadas. Por ejemplo, crear un nuevo cliente y un nuevo pedido y, a continuación, intenta guardar los datos pueden producir un conflicto con las restricciones de clave externa que se definen en la base de datos. Para obtener más información, consulte [desactivar restricciones al llenar un conjunto de datos](turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="set-the-order-to-perform-updates"></a>Establecer el orden para realizar actualizaciones  
 Establecer el orden para realizar actualizaciones establece el orden de la persona inserta, actualiza y elimina ese necesarias para guardar todos los datos modificados en todas las tablas de un conjunto de datos. Cuando la actualización jerárquica está habilitada, las inserciones se llevan a cabo en primer lugar, a continuación, actualiza y, a continuación, se elimina. El `TableAdapterManager` proporciona un `UpdateOrder` propiedad que se puede establecer para realizar actualizaciones en primer lugar, inserciones y eliminaciones.  
  
> [!NOTE]
>  Es importante entender que el orden de actualización es totalmente inclusivo. Es decir, cuando se realizan las actualizaciones, inserciones y, a continuación, las eliminaciones se realizan para todas las tablas del conjunto de datos.  
  
 Para establecer el `UpdateOrder` propiedad después de arrastrar elementos desde la [ventana Orígenes de datos](add-new-data-sources.md) en un formulario, seleccione la `TableAdapterManager` en la Bandeja de componentes y, a continuación, establezca el `UpdateOrder` propiedad en la **propiedades** ventana. 
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Crear una copia de seguridad de un conjunto de datos antes de realizar una actualización jerárquica  
 Cuando se guardan datos (llamando al método `TableAdapterManager.UpdateAll()` ), `TableAdapterManager` intenta actualizar los datos para cada tabla en una transacción única. Si se produce un error en cualquier parte de la actualización en cualquier tabla, se revierte la transacción entera. En la mayoría de los casos, la reversión de la aplicación vuelve a su estado original.  
  
 Sin embargo, a veces se decide restaurar el conjunto de datos a partir de la copia de seguridad. Un ejemplo de esto se puede producir cuando usa valores de incremento automático. Por ejemplo, si un proceso de guardar la operación no es correcta, valores de incremento automático no se restablecen en el conjunto de datos y el conjunto de datos continúa crear valores de incremento automático. Esto deja un vacío en la numeración que puede no ser aceptable en la aplicación. En situaciones donde éste es un problema, `TableAdapterManager` proporciona una propiedad `BackupDataSetBeforeUpdate` que reemplaza el conjunto de datos existente con una copia de seguridad si se produce un error en la transacción.  
  
> [!NOTE]
>  La copia de seguridad únicamente permanece en memoria mientras el `TableAdapterManager.UpdateAll` método se está ejecutando. Por lo tanto, no hay ningún acceso mediante programación a este conjunto de datos de copia de seguridad porque reemplaza el conjunto de datos original o se sale del ámbito en cuanto el `TableAdapterManager.UpdateAll` método termina de ejecutarse.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificar generado guardar código para realizar la actualización jerárquica  
 Guarde en la base de datos los cambios de las tablas de datos relacionadas del conjunto de datos; para ello, llame al método `TableAdapterManager.UpdateAll` y pase el nombre del conjunto de datos que contiene las tablas relacionadas. Por ejemplo, ejecute el método `TableAdapterManager.UpdateAll(NorthwindDataset)` para enviar las actualizaciones de todas las tablas de NorthwindDataset a la base de datos back-end.  
  
 Después de colocar los elementos de la **orígenes de datos** ventana, se agrega automáticamente código para el `Form_Load` eventos para rellenar cada tabla (la `TableAdapter.Fill` métodos). También se agrega código para el **guardar** evento de clic de botón la <xref:System.Windows.Forms.BindingNavigator> para guardar los datos del conjunto de datos en la base de datos (el `TableAdapterManager.UpdateAll` método).  
  
 El código de guardado generado también contiene una línea de código que llama al método `CustomersBindingSource.EndEdit`. Más específicamente, llama a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método del primer <xref:System.Windows.Forms.BindingSource>que se agrega al formulario. En otras palabras, este código solo se genera para la primera tabla que se arrastra desde el **orígenes de datos** ventana hasta el formulario. La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene foco y hace clic en el **guardar** button, todas las ediciones pendientes en ese control se confirman antes del guardado real (el `TableAdapterManager.UpdateAll` método).  
  
> [!NOTE]
>  El Diseñador de Dataset solo agrega el `BindingSource.EndEdit` código para la primera tabla que se coloca en el formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método `BindingSource.EndEdit` para cada tabla relacionada en el formulario. Para este tutorial, esto significa que tiene que agregar una llamada al método `OrdersBindingSource.EndEdit`.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Para actualizar el código para confirmar los cambios en las tablas relacionadas antes de guardar  
  
1.  Haga doble clic en el **guardar** situado en la <xref:System.Windows.Forms.BindingNavigator> para abrir **Form1** en el Editor de código.  
  
2.  Agregue una línea de código para llamar al método `OrdersBindingSource.EndEdit` después de la línea que llama al método `CustomersBindingSource.EndEdit`. El código en el **guardar** clic en el botón eventos deben ser similar a lo siguiente:  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]  
  
Además de confirmar los cambios en una tabla secundaria relacionada antes de guardar los datos en una base de datos, quizás también tenga que confirmar los registros primarios recién creados antes de agregar nuevos registros secundarios a un conjunto de datos. En otras palabras, quizás tenga que agregar el nuevo registro primario (Customer) al conjunto de datos para que las restricciones de clave externa permitan agregar nuevos registros secundarios (Orders) al conjunto de datos. Para ello, puede usar el evento `BindingSource.AddingNew` secundario.  
  
> [!NOTE]
>  Si se deben confirmar los nuevos registros primarios depende del tipo de control que se usa para enlazar al origen de datos. En este tutorial, usa controles individuales para enlazar a la tabla primaria. Esto requiere que el código adicional confirme el nuevo registro primario. Si los registros primarios se mostraron en su lugar en un control de enlace complejo, como el <xref:System.Windows.Forms.DataGridView>este adicionales <xref:System.Windows.Forms.BindingSource.EndEdit%2A> llamar a para el registro primario no sería necesario. Esto se debe a que la funcionalidad de enlace a datos subyacente del control controla la confirmación de los nuevos registros.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Para agregar código para confirmar los registros primarios en el conjunto de datos antes de agregar registros secundarios  
  
1.  Cree un controlador para el evento `OrdersBindingSource.AddingNew`.  
  
    -   Abra **Form1** en la vista de diseño, seleccione **OrdersBindingSource** en la Bandeja de componentes, seleccione **eventos** en el **propiedades** ventana, y a continuación, haga doble clic en el **AddingNew** evento.  
  
2.  Agregar una línea de código al controlador de eventos que llama el `CustomersBindingSource.EndEdit` método. El código del controlador de evento `OrdersBindingSource_AddingNew` debe tener un aspecto similar al siguiente:  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]  
  
## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager  
 De forma predeterminada, un `TableAdapterManager` clase se genera cuando se crea un conjunto de datos contiene tablas relacionadas. Para evitar que la clase que se está generando, cambie el valor de la `Hierarchical Update` propiedad del conjunto de datos en false. Cuando se arrastra una tabla que tiene una relación a la superficie de diseño de un formulario Windows Forms o la página WPF, Visual Studio declara una variable de miembro de la clase. Si no usa el enlace de datos, es necesario manualmente declarar la variable.  
  
 El `TableAdapterManager` clase no es parte de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Por lo tanto, no puede buscarla en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de datos.  
  
 Los siguientes son los métodos usados con frecuencia y las propiedades de la `TableAdapterManager` clase:  
  
|Miembro|Descripción|  
|------------|-----------------|  
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|  
|Propiedad `BackUpDataSetBeforeUpdate`|Determina si se debe crear una copia de seguridad del conjunto de datos antes de ejecutar el `TableAdapterManager.UpdateAll` método. Valor booleano.|  
|*tableName* `TableAdapter` propiedad|Representa un `TableAdapter`. Generado `TableAdapterManager` contiene una propiedad para cada `TableAdapter` que administra. Por ejemplo, un conjunto de datos con una tabla Customers y Orders se genera con un `TableAdapterManager` que contiene `CustomersTableAdapter` y `OrdersTableAdapter` propiedades.|  
|Propiedad `UpdateOrder`|Controla el orden de los individual insert, update y comandos delete. Establezca esta propiedad en uno de los valores de la `TableAdapterManager.UpdateOrderOption` enumeración.<br /><br /> De forma predeterminada, el `UpdateOrder` está establecido en **InsertUpdateDelete**. Esto significa que se inserta, a continuación, actualizaciones y eliminaciones, a continuación, se realizan para todas las tablas del conjunto de datos.|  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)