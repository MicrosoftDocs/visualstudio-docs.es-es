---
title: Actualización jerárquica | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d0176f203f7decb701d678a110856acdad36750b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220184"
---
# <a name="hierarchical-update"></a>Actualización jerárquica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Actualización jerárquica * se refiere al proceso de guardar los datos actualizados (de un conjunto de datos con dos o más tablas relacionadas) a una base de datos manteniendo las reglas de integridad referencial. *La integridad referencial* hace referencia a las reglas de coherencia proporcionadas por las restricciones en una base de datos que controlan el comportamiento de insertar, actualizar y eliminar registros relacionados. Por ejemplo, es integridad referencial que exige la creación de un registro de cliente antes de permitir crear pedidos para ese cliente.  Para obtener más información acerca de las relaciones en conjuntos de datos, vea [relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)  
  
 La característica de actualización jerárquica usa un `TableAdapterManager` para administrar el `TableAdapter`s en un dataset con tipo. El `TableAdapterManager` componente es un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-generado (clase), por lo que no forma parte de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Cuando se arrastra una tabla desde la ventana de orígenes de datos a un formulario de Windows o la página de WPF, Visual Studio agrega una variable de tipo TableAdapterManager al formulario o página y verlo en el diseñador en la Bandeja de componentes. Para obtener información detallada sobre la `TableAdapterManager` de clases, vea la sección de referencia de TableAdapterManager de [información general sobre TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 De forma predeterminada, un conjunto de datos trata las tablas relacionadas como "solo, relaciones" lo que significa que no obliga a restricciones de clave externa. Puede modificar dicha configuración en tiempo de diseño mediante el Diseñador de Dataset. Seleccione la línea de relación entre dos tablas para que aparezca el **relación** cuadro de diálogo. Los cambios que realice aquí determinarán cómo comporta TableAdapterManager al que enviar los cambios en las tablas relacionadas en la base de datos.  
  
## <a name="enablehierarchical-update-in-a-dataset"></a>Actualización de Enablehierarchical en un conjunto de datos  
 De forma predeterminada, la actualización jerárquica está habilitada para todos los nuevos conjuntos de datos que se agregan o se crean en un proyecto. Activar actualización jerárquica o desactivar estableciendo la **actualización jerárquica** propiedad de un dataset con tipo en el [crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) a **True** o **False**:  
  
 ![Configuración de la actualización jerárquica](../data-tools/media/hierarchical-update-setting.png "configuración de la actualización jerárquica")  
  
## <a name="create-a-new-relation-between-tables"></a>Crear a una nueva relación entre tablas  
 Para crear una nueva relación entre dos tablas, en el Diseñador de Dataset, seleccione la barra de título de cada tabla, a continuación, haga clic en y seleccione**agregar relación**.  
  
 ![Actualización jerárquica Agregar menú de la relación](../data-tools/media/hierarchical-update-add-relation-menu.png "actualización jerárquica Agregar menú de relación")  
  
## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Comprender las restricciones foreign key, las actualizaciones en cascada y eliminaciones  
 Es importante entender las restricciones foreign key cómo y comportamiento en cascada en la base de datos se crean en el código del conjunto de datos generado.  
  
 De forma predeterminada, las tablas de datos en un conjunto de datos se generan con relaciones (<xref:System.Data.DataRelation>) que coinciden con las relaciones en la base de datos. Sin embargo, la relación en el conjunto de datos no se genera como una restricción FOREIGN KEY. El <xref:System.Data.DataRelation> está configurado como **sólo relación** sin <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> o <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> en vigor.  
  
 De forma predeterminada, las actualizaciones y las eliminaciones en cascada están desactivadas, incluso si la relación de la base de datos establece que estén activadas. Por ejemplo, crear un nuevo cliente y un pedido nuevo y, a continuación, intenta guardar los datos pueden producir un conflicto con las restricciones de clave externa que se definen en la base de datos. Para obtener más información, consulte [Cómo: configurar las restricciones Foreign Key en un conjunto de datos](http://msdn.microsoft.com/library/3954c388-e209-4a67-a34e-5ca106282f8e).  
  
## <a name="set-the-order-to-perform-updates"></a>Establecer el orden para realizar actualizaciones  
 Establecer el orden para realizar actualizaciones establece el orden de la persona que inserta, actualiza y elimina ese necesarias para guardar todos los datos modificados en todas las tablas de un conjunto de datos. Cuando la actualización jerárquica está habilitada, inserciones se realizan en primer lugar, a continuación, actualiza y, a continuación, se elimina. El `TableAdapterManager` proporciona un `UpdateOrder` propiedad que se puede establecer para realizar actualizaciones en primer lugar, inserciones y eliminaciones.  
  
> [!NOTE]
>  Es importante comprender que el orden de actualización es totalmente inclusivo. Es decir, cuando se realizan actualizaciones, inserciones y eliminaciones se realizan para todas las tablas del conjunto de datos.  
  
 Para establecer el `UpdateOrder` propiedad después de arrastrar elementos desde el [ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) en un formulario, seleccione el `TableAdapterManager` en la Bandeja de componentes y, a continuación, establezca el `UpdateOrder` propiedad en el **propiedades** ventana. Para obtener más información, consulte [Cómo: establecer el orden cuando se lleve a cabo una actualización jerárquica](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).  
  
## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>Crear una copia de seguridad de un conjunto de datos antes de realizar una actualización jerárquica  
 Cuando se guardan datos (llamando al método `TableAdapterManager.UpdateAll()` ), `TableAdapterManager` intenta actualizar los datos para cada tabla en una transacción única. Si se produce un error en cualquier parte de la actualización en cualquier tabla, se revierte la transacción entera. En la mayoría de los casos, la reversión de la aplicación vuelve a su estado original.  
  
 Sin embargo, a veces se decide restaurar el conjunto de datos a partir de la copia de seguridad. Un ejemplo de esto puede producirse cuando se usa valores de incremento automático. Por ejemplo, si una operación de guardar la operación no es correcta, no se restablecen los valores de incremento automático en el conjunto de datos y continúa el conjunto de datos crear valores de incremento automático. Esto deja una discontinuidad en la numeración que puede no ser aceptable en la aplicación. En situaciones donde éste es un problema, `TableAdapterManager` proporciona una propiedad `BackupDataSetBeforeUpdate` que reemplaza el conjunto de datos existente con una copia de seguridad si se produce un error en la transacción.  
  
> [!NOTE]
>  La copia de seguridad únicamente permanece en memoria mientras el `TableAdapterManager.UpdateAll` método se está ejecutando. Por lo tanto, no hay ningún acceso mediante programación a este conjunto de datos de copia de seguridad porque reemplaza el conjunto de datos original o se sale del ámbito tan pronto como el `TableAdapterManager.UpdateAll` método termina de ejecutarse.  
  
## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>Modificar generado código para realizar la actualización jerárquica de guardado  
 Guarde en la base de datos los cambios de las tablas de datos relacionadas del conjunto de datos; para ello, llame al método `TableAdapterManager.UpdateAll` y pase el nombre del conjunto de datos que contiene las tablas relacionadas. Por ejemplo, ejecute el método `TableAdapterManager.UpdateAll(NorthwindDataset)` para enviar las actualizaciones de todas las tablas de NorthwindDataset a la base de datos back-end.  
  
 Después de colocar los elementos de la **orígenes de datos** , ventana de código se agrega automáticamente a la `Form_Load` eventos para rellenar cada tabla (la `TableAdapter.Fill` métodos). También se agrega código para el **guardar** evento de clic de botón el <xref:System.Windows.Forms.BindingNavigator> para guardar los datos del conjunto de datos en la base de datos (el `TableAdapterManager.UpdateAll` método).  
  
 El código de guardado generado también contiene una línea de código que llama al método `CustomersBindingSource.EndEdit`. Más concretamente, llama a la <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método del primer <xref:System.Windows.Forms.BindingSource>que se agrega al formulario. En otras palabras, este código solo se genera para la primera tabla que se arrastra desde el **orígenes de datos** ventana hasta el formulario. La llamada <xref:System.Windows.Forms.BindingSource.EndEdit%2A> confirma los cambios que están en curso en los controles enlazados a datos que se estén editando en ese momento. Por lo tanto, si un control enlazado a datos aún tiene el foco y hace clic en el **guardar** button, todas las ediciones pendientes en ese control se confirman antes del guardado real (el `TableAdapterManager.UpdateAll` método).  
  
> [!NOTE]
>  El Diseñador de Dataset solo agrega el `BindingSource.EndEdit` código para la primera tabla que se coloca en el formulario. Por lo tanto, tiene que agregar una línea de código para llamar al método `BindingSource.EndEdit` para cada tabla relacionada en el formulario. Para este tutorial, esto significa que tiene que agregar una llamada al método `OrdersBindingSource.EndEdit`.  
  
#### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>Para actualizar el código para confirmar los cambios en las tablas relacionadas antes de guardar  
  
1. Haga doble clic en el **guardar** situado en la <xref:System.Windows.Forms.BindingNavigator> para abrir **Form1** en el Editor de código.  
  
2. Agregue una línea de código para llamar al método `OrdersBindingSource.EndEdit` después de la línea que llama al método `CustomersBindingSource.EndEdit`. El código en el **guardar** clic de botón evento debe parecerse al siguiente:  
  
    [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#1)]
    [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#1)]  
  
   Además de confirmar los cambios en una tabla secundaria relacionada antes de guardar los datos en una base de datos, quizás también tenga que confirmar los registros primarios recién creados antes de agregar nuevos registros secundarios a un conjunto de datos. En otras palabras, quizás tenga que agregar el nuevo registro primario (Customer) al conjunto de datos para que las restricciones de clave externa permitan agregar nuevos registros secundarios (Orders) al conjunto de datos. Para ello, puede usar el evento `BindingSource.AddingNew` secundario.  
  
> [!NOTE]
>  Si tiene que confirmar los nuevos registros primarios depende del tipo de control que se usa para enlazar al origen de datos. En este tutorial, se usan controles individuales para enlazar a la tabla primaria. Esto requiere que el código adicional para confirmar el nuevo registro primario. Si los registros primarios se mostraron en su lugar en un control de enlace complejo como el <xref:System.Windows.Forms.DataGridView>este adicionales <xref:System.Windows.Forms.BindingSource.EndEdit%2A> llamar a para el registro primario no sería necesario. Esto se debe a que la funcionalidad de enlace a datos subyacente del control controla la confirmación de los nuevos registros.  
  
#### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>Para agregar código para confirmar los registros primarios en el conjunto de datos antes de agregar registros secundarios  
  
1.  Cree un controlador para el evento `OrdersBindingSource.AddingNew`.  
  
    -   Abra **Form1** en la vista Diseño, seleccione **OrdersBindingSource** en la Bandeja de componentes, seleccione **eventos** en el **propiedades** ventana, y a continuación, haga doble clic en el **AddingNew** evento.  
  
2.  Agregar una línea de código al controlador de eventos que llama el `CustomersBindingSource.EndEdit` método. El código del controlador de evento `OrdersBindingSource_AddingNew` debe tener un aspecto similar al siguiente:  
  
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../snippets/csharp/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/CS/Form1.cs#2)]
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VSProDataOrcasHierarchicalUpdate/VB/Form1.vb#2)]  
  
## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager  
 De forma predeterminada, un `TableAdapterManager` clase se genera cuando se crea un conjunto de datos que contiene las tablas relacionadas. Para evitar que la clase que se está generando, cambie el valor de la `Hierarchical Update` propiedad del conjunto de datos en false. Cuando se arrastra una tabla que tiene una relación a la superficie de diseño de un formulario de Windows o la página de WPF, Visual Studio declara una variable de miembro de la clase. Si no usa el enlace de datos, deberá declarar la variable de forma manual.  
  
 El `TableAdapterManager` clase no es parte de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Por lo tanto, no puede buscarla en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de datos.  
  
 Los siguientes son los métodos usados con frecuencia y propiedades de la `TableAdapterManager` clase:  
  
|Miembro|Descripción|  
|------------|-----------------|  
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|  
|Propiedad`BackUpDataSetBeforeUpdate` |Determina si se debe crear una copia de seguridad del conjunto de datos antes de ejecutar el `TableAdapterManager.UpdateAll` método. Valor booleano.|  
|*tableName* `TableAdapter` propiedad|Representa un `TableAdapter`. Generado `TableAdapterManager` contiene una propiedad para cada `TableAdapter` lo administra. Por ejemplo, se genera un conjunto de datos con una tabla de clientes y pedidos con un `TableAdapterManager` que contiene `CustomersTableAdapter` y `OrdersTableAdapter` propiedades.|  
|Propiedad`UpdateOrder` |Controla el orden de los individual insert, update y los comandos delete. Establezca esta opción a uno de los valores de la `TableAdapterManager.UpdateOrderOption` enumeración.<br /><br /> De forma predeterminada, el `UpdateOrder` está establecido en **InsertUpdateDelete**. Esto significa que se inserta, a continuación, actualizaciones y eliminaciones, a continuación, se realizan para todas las tablas del conjunto de datos. Para obtener más información, consulte [Cómo: establecer el orden cuando se lleve a cabo una actualización jerárquica](http://msdn.microsoft.com/library/a0734935-78dd-4c0b-80d7-5e7925789c83).|  
  
## <a name="see-also"></a>Vea también  
 [Guardar los datos de nuevo en la base de datos](../data-tools/save-data-back-to-the-database.md)

