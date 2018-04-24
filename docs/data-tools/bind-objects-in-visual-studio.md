---
title: Enlazar los objetos en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5b515a802c4b82bb3b1400f5ea88720242b80aa9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="bind-objects-in-visual-studio"></a>Enlazar los objetos en Visual Studio
Visual Studio proporciona herramientas en tiempo de diseño para trabajar con objetos personalizados, como el origen de datos en la aplicación. Cuando desea almacenar los datos de una base de datos en un objeto que se enlazan a controles de interfaz de usuario, el enfoque recomendado es usar Entity Framework para generar la clase o clases. Entity Framework genera automáticamente todo el código de seguimiento de cambios de código reutilizable, lo que significa que los cambios realizados en los objetos locales guardan automáticamente en la base de datos cuando se llama a AcceptChanges en el objeto DbSet. Para obtener más información, consulte [documentación de Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
>  Las metodologías de enlace de objetos en este artículo sólo se deben considerar si la aplicación ya se basa en los conjuntos de datos. Estos métodos también pueden utilizarse si ya está familiarizado con los conjuntos de datos y los datos que se van a procesar están demasiado grande y no demasiado complejo o tabular. Para obtener un ejemplo incluso más sencillo, que implica la carga de datos directamente en objetos mediante un objeto DataReader y actualizar manualmente la interfaz de usuario sin enlace de datos, vea [crear una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisitos de objeto
 El único requisito para los objetos personalizados trabajar con los datos de las herramientas de diseño en Visual Studio es que el objeto debe tener al menos una propiedad pública.

 Por lo general, los objetos personalizados no requieren las interfaces específicas, constructores o atributos para que actúe como un origen de datos para una aplicación. Sin embargo, si desea arrastrar el objeto desde el **orígenes de datos** ventana hasta una superficie de diseño para crear un control enlazado a datos, y si el objeto implementa la <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaz, el objeto debe tener un valor predeterminado constructor. En caso contrario, Visual Studio no se puede crear una instancia del objeto de origen de datos, y muestra un error cuando se arrastra el elemento a la superficie de diseño.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Ejemplos del uso de objetos personalizados como orígenes de datos
 Aunque hay muchas maneras de implementar la lógica de aplicación cuando se trabaja con objetos como origen de datos, para SQL hay bases de datos son algunas operaciones estándar que se pueden simplificar mediante el uso de los objetos TableAdapter generado por Visual Studio. Esta página explica cómo implementar estos procesos estándares utilizando TableAdapters.It no está pensado como una guía para crear los objetos personalizados. Por ejemplo, normalmente realizará las siguientes operaciones estándares, independientemente de la implementación específica de los objetos y la lógica de la aplicación:

-   Para cargar datos en objetos (normalmente de una base de datos).

-   Crear una colección de objetos con tipo.

-   Adición de objetos a y quitar objetos de una colección.

-   Mostrar los datos de objeto a los usuarios en un formulario.

-   Cambiar o editar los datos de un objeto.

-   Guardar los datos de objetos en la base de datos.

### <a name="load-data-into-objects"></a>Cargar datos en objetos
 En este ejemplo, cargar datos en los objetos mediante el uso de los TableAdapters. De forma predeterminada, los TableAdapters se crean con dos tipos de métodos que toman datos de una base de datos y rellenan tablas de datos.

-   El `TableAdapter.Fill` método rellena una tabla de datos existente con los datos devueltos.

-   El `TableAdapter.GetData` método devuelve una nueva tabla de datos rellenada con datos.

 La manera más fácil para cargar los objetos personalizados con los datos es llamar a la `TableAdapter.GetData` (método), recorrer en iteración la colección de filas de la tabla de datos devuelta y rellenar cada objeto con los valores de cada fila. Puede crear un `GetData` método que devuelve una tabla de datos rellenada para cualquier consulta agregada a un TableAdapter.

> [!NOTE]
>  Visual Studio denomina las consultas de TableAdapter `Fill` y `GetData` de forma predeterminada, pero se pueden cambiar esos nombres para cualquier nombre de método válido.

 En el ejemplo siguiente se muestra cómo recorrer en iteración las filas de una tabla de datos y rellenar un objeto con datos:

 [!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Crear una colección de objetos con tipo
 Puede crear clases de colección para los objetos, o usar las colecciones con tipo que proporcionan automáticamente la [BindingSource (componente)](/dotnet/framework/winforms/controls/bindingsource-component).

 Cuando está creando una clase de colección personalizada para los objetos, sugerimos que hereda de <xref:System.ComponentModel.BindingList%601>. Esta clase genérica proporciona funcionalidad para administrar la colección, así como la capacidad para generar eventos que envían notificaciones a la infraestructura de enlace de datos en formularios Windows Forms.

 La colección generada automáticamente en el <xref:System.Windows.Forms.BindingSource> utiliza un <xref:System.ComponentModel.BindingList%601> para su colección con tipo. Si la aplicación no requiere una funcionalidad adicional, puede mantener su colección dentro de la <xref:System.Windows.Forms.BindingSource>. Para obtener más información, consulte el <xref:System.Windows.Forms.BindingSource.List%2A> propiedad de la <xref:System.Windows.Forms.BindingSource> clase.

> [!NOTE]
>  Si la colección requiere funcionalidad que no proporcionada la implementación base de la <xref:System.ComponentModel.BindingList%601>, debe crear una colección personalizada para que pueda agregar a la clase según sea necesario.

 El código siguiente muestra cómo crear la clase para una colección fuertemente tipada de `Order` objetos:

 [!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Agregar objetos a una colección
 Agregar objetos a una colección mediante una llamada a la `Add` método de la clase de colección personalizada o de la <xref:System.Windows.Forms.BindingSource>.


> [!NOTE]
>  El `Add` método se proporciona automáticamente para la colección personalizada cuando hereda de <xref:System.ComponentModel.BindingList%601>.

 El código siguiente muestra cómo agregar objetos a la colección con tipo en un <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

 El código siguiente muestra cómo agregar objetos a una colección con tipo que hereda de <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
>  En este ejemplo el `Orders` colección es una propiedad de la `Customer` objeto.

 [!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Quitar objetos de una colección
 Quitar objetos de una colección mediante una llamada a la `Remove` o `RemoveAt` método de la clase de colección personalizada o de <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
>  El `Remove` y `RemoveAt` automáticamente se proporcionan métodos para la colección personalizada cuando hereda de <xref:System.ComponentModel.BindingList%601>.

 El código siguiente muestra cómo buscar y quitar objetos de la colección con tipo en un <xref:System.Windows.Forms.BindingSource> con el <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> método:

 [!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Mostrar datos de objetos a los usuarios
 Para mostrar los datos de objetos a los usuarios, crear un origen de datos de objeto mediante la **configuración del origen de datos** asistente y, a continuación, arrastre el objeto completo o propiedades individuales al formulario desde el **orígenes de datos**ventana.

### <a name="modify-the-data-in-objects"></a>Modifique los datos de objetos
 Para modificar datos en objetos personalizados que están enlazados a datos a controles de formularios Windows Forms, basta con modificar los datos en el control enlazado (o directamente en las propiedades del objeto). Arquitectura de enlace de datos actualiza los datos en el objeto.

 Si la aplicación requiere el seguimiento de cambios y revertir los cambios propuestos a sus valores originales, debe implementar esta funcionalidad en el modelo de objetos. Para obtener ejemplos de cómo las tablas de datos realizar un seguimiento de los cambios propuestos, consulte <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, y <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="save-data-in-objects-back-to-the-database"></a>Guardar datos de objetos en la base de datos
 Guardar datos en la base de datos pasando los valores de los objetos a los métodos DBDirect del TableAdapter.

 Visual Studio crea DBDirect (métodos) que se pueden ejecutar directamente en la base de datos. Estos métodos no requieren objetos DataSet ni DataTable.

|Método DBDirect de TableAdapter|Descripción|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos, lo que le permite pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualizaciones de registros existentes en una base de datos. El método Update toma los valores de columna originales y los nuevos como parámetros de método. Los valores originales se utilizan para ubicar el registro original y los nuevos valores se utilizan para actualizar ese registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para conciliar los cambios en un conjunto de datos a la base de datos, tomando un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matriz de <xref:System.Data.DataRow>s como parámetros de método.|
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos en función de los valores de columna originales pasados como parámetros de método.|

 Para guardar los datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, con un bucle for next). Los valores para cada objeto se envían a la base de datos utilizando los métodos DBDirect del TableAdapter.

 En el ejemplo siguiente se muestra cómo utilizar el `TableAdapter.Insert` método DBDirect para agregar un nuevo cliente directamente en la base de datos:

 [!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)