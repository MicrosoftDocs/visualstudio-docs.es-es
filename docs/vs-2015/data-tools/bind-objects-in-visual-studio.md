---
title: Enlazar objetos
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
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 12cbeca740fd81292109183468a304fc2d3da30c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439489"
---
# <a name="bind-objects-in-visual-studio"></a>Enlazar objetos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio proporciona herramientas de tiempo de diseño para trabajar con objetos personalizados, como el origen de datos en la aplicación. Cuando desea almacenar los datos de una base de datos en un objeto que enlazar a controles de interfaz de usuario, el enfoque recomendado es usar Entity Framework para generar la clase o clases. Entidad Frameworkautogenerates todo el código de seguimiento de cambios de código reutilizable, lo que significa que todos los cambios en los objetos locales se guardan automáticamente en la base de datos cuando se llama a AcceptChanges en el objeto de DbSet.    Para obtener más información, consulte [documentación de Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Los métodos de enlace de objetos en este artículo solo se deben considerar si la aplicación ya se basa en los conjuntos de datos. También se pueden usar estos métodos si ya está familiarizado con los conjuntos de datos y los datos que se van a procesar están tabular y no demasiado compleja o demasiado grande. Para obtener un ejemplo incluso más sencillo, que implica cargar datos directamente en objetos mediante un objeto DataReader y actualizar manualmente la interfaz de usuario sin enlace de datos, vea [crear una aplicación de datos sencilla mediante ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisitos de objeto
 El único requisito para los objetos personalizados trabajar con los datos de las herramientas de diseño en Visual Studio es que el objeto necesita al menos una propiedad pública.

 Por lo general, los objetos personalizados no requieren las interfaces específicas, constructores o atributos para que actúe como un origen de datos para una aplicación. Sin embargo, si desea arrastrar el objeto desde el **orígenes de datos** ventana a una superficie de diseño para crear un control enlazado a datos, y si el objeto implementa la <xref:System.ComponentModel.ITypedList> o <xref:System.ComponentModel.IListSource> interfaz, el objeto debe tener un valor predeterminado constructor. En caso contrario, Visual Studio no puede crear instancias del objeto de origen de datos y muestra un error cuando se arrastra el elemento a la superficie de diseño.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Ejemplos del uso de objetos personalizados como orígenes de datos
 Aunque existen innumerables formas de implementar la lógica de aplicación cuando se trabaja con objetos como un origen de datos, para SQL, bases de datos son algunas de las operaciones estándares que se pueden simplificar mediante el uso de los objetos TableAdapter generados por Visual Studio. Esta página explica cómo implementar estos procesos estándares utilizando TableAdapters.It no está pensada como una guía para crear los objetos personalizados. Por ejemplo, normalmente, realizará las siguientes operaciones estándares, independientemente de la implementación específica de los objetos o la lógica de aplicación:

- Cargar datos en objetos (normalmente de una base de datos).

- Creación de una colección de objetos con tipo.

- Adición de objetos a y quitar objetos de una colección.

- Mostrar los datos de objetos a los usuarios en un formulario.

- Cambiar o editar los datos en un objeto.

- Guardar datos de objetos en la base de datos.

> [!NOTE]
> Para comprender mejor y proporcionar el contexto para los ejemplos de esta página, se recomienda que haga lo siguiente: [Tutorial: Conectarse a datos en objetos (formularios Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05). En este tutorial crea los objetos que se tratan aquí.

### <a name="loaddata-into-objects"></a>LoadData en objetos
 En este ejemplo, cargar datos en los objetos mediante el uso de los TableAdapters. De forma predeterminada, los TableAdapters se crean con dos tipos de métodos que toman datos de una base de datos y rellenan tablas de datos.

- El `TableAdapter.Fill` método rellena una tabla de datos existente con los datos devueltos.

- El `TableAdapter.GetData` método devuelve una nueva tabla de datos que se rellena con datos.

  La manera más fácil para cargar los objetos con datos personalizados es llamar a la `TableAdapter.GetData` método, recorra en iteración la colección de filas de la tabla de datos devueltos y rellenar cada objeto con los valores de cada fila. Puede crear un `GetData` método que devuelve una tabla de datos rellenada para cualquier consulta agregada a un TableAdapter.

> [!NOTE]
> Visual Studio los nombres de las consultas de TableAdapter `Fill` y `GetData` de forma predeterminada, pero se pueden cambiar esos nombres para cualquier nombre de método válido.

 El ejemplo siguiente muestra cómo recorrer en iteración las filas de una tabla de datos y rellenar un objeto con datos:

 [!code-csharp[VbRaddataConnecting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Form1.cs#4)]
 [!code-vb[VbRaddataConnecting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Form1.vb#4)]

### <a name="create-a-typed-collection-of-objects"></a>Crear una colección de objetos con tipo
 Puede crear clases de colección para los objetos o usar las colecciones con tipo que proporcionarán automáticamente la [componente BindingSource](http://msdn.microsoft.com/library/3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9).

 Al crear una clase de colección personalizada para los objetos, se recomienda que se hereda de <xref:System.ComponentModel.BindingList%601>. Esta clase genérica proporciona funcionalidad para administrar la colección, así como la capacidad para generar eventos que envían notificaciones a la infraestructura de enlace de datos en Windows Forms.

 La colección generada automáticamente en el <xref:System.Windows.Forms.BindingSource> usa un <xref:System.ComponentModel.BindingList%601> para su colección con tipo. Si la aplicación no requiere una funcionalidad adicional, puede mantener su colección dentro de la <xref:System.Windows.Forms.BindingSource>. Para obtener más información, consulte el <xref:System.Windows.Forms.BindingSource.List%2A> propiedad de la <xref:System.Windows.Forms.BindingSource> clase.

> [!NOTE]
> Si la colección requiere funcionalidad que no proporcionada la implementación base de la <xref:System.ComponentModel.BindingList%601>, debe crear una colección personalizada para que pueda agregar a la clase según sea necesario.

 El código siguiente muestra cómo crear la clase para una colección fuertemente tipada de `Order` objetos:

 [!code-csharp[VbRaddataConnecting#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#8)]
 [!code-vb[VbRaddataConnecting#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#8)]

### <a name="addobjects-to-a-collection"></a>Addobjects a una colección
 Agregar objetos a una colección mediante una llamada a la `Add` método de la clase de colección personalizada o de la <xref:System.Windows.Forms.BindingSource>.

 Para obtener un ejemplo de cómo agregar a una colección mediante un <xref:System.Windows.Forms.BindingSource>, consulte el `LoadCustomers` método [Tutorial: Conectarse a datos en objetos (formularios Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

 Para obtener un ejemplo de cómo agregar objetos a una colección personalizada, vea el `LoadOrders` método [Tutorial: Conectarse a datos en objetos (formularios Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05).

> [!NOTE]
> El `Add` método se proporciona automáticamente para la colección personalizada cuando se hereda de <xref:System.ComponentModel.BindingList%601>.

 El código siguiente muestra cómo agregar objetos a la colección con tipo en un <xref:System.Windows.Forms.BindingSource>:

 [!code-csharp[VbRaddataConnecting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#5)]
 [!code-vb[VbRaddataConnecting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#5)]

 El código siguiente muestra cómo agregar objetos a una colección con tipo que hereda de <xref:System.ComponentModel.BindingList%601>:

> [!NOTE]
> En este ejemplo el `Orders` colección es una propiedad de la `Customer` objeto.

 [!code-csharp[VbRaddataConnecting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#6)]
 [!code-vb[VbRaddataConnecting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#6)]

### <a name="removeobjects-from-a-collection"></a>Quitar objetos de una colección
 Quitar objetos de una colección mediante una llamada a la `Remove` o `RemoveAt` método de la clase de colección personalizada o de <xref:System.Windows.Forms.BindingSource>.

> [!NOTE]
> El `Remove` y `RemoveAt` automáticamente se proporcionan métodos para la colección personalizada cuando se hereda de <xref:System.ComponentModel.BindingList%601>.

 El código siguiente muestra cómo buscar y quitar objetos de la colección con tipo en un <xref:System.Windows.Forms.BindingSource> con el <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> método:

 [!code-csharp[VbRaddataConnecting#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConnecting/CS/Class1.cs#7)]
 [!code-vb[VbRaddataConnecting#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConnecting/VB/Class1.vb#7)]

### <a name="displayobject-data-to-users"></a>DisplayObject datos a los usuarios
 Para mostrar los datos en los objetos a los usuarios, cree un origen de datos de objeto mediante el **configuración origen de datos** asistente y, a continuación, arrastre el objeto completo o propiedades individuales al formulario desde el **orígenes de datos**ventana.

### <a name="modify-the-data-in-objects"></a>Modificar los datos de objetos
 Para modificar datos en objetos personalizados que están enlazados a datos a controles de formularios Windows Forms, basta con modificar los datos en el control enlazado (o directamente en las propiedades del objeto). Arquitectura de enlace de datos actualiza los datos en el objeto.

 Si la aplicación requiere el seguimiento de cambios y revertir los cambios propuestos a sus valores originales, debe implementar esta funcionalidad en su modelo de objetos. Para obtener ejemplos de cómo las tablas de datos realizar un seguimiento de los cambios propuestos, consulte <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, y <xref:System.Data.DataTable.GetChanges%2A>.

### <a name="savedata-in-objects-back-to-the-database"></a>SaveData de objetos en la base de datos
 Guardar los datos en la base de datos pasando los valores de los objetos a los métodos DBDirect del TableAdapter.

 Visual Studio crea métodos DBDirect que se pueden ejecutar directamente en la base de datos. Estos métodos no requieren objetos DataSet o DataTable.

|Método de TableAdapter DBDirect|Descripción|
|----------------------------------|-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos, que le permiten pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualizaciones de registros existentes en una base de datos. El método Update toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se usan para localizar el registro original y los nuevos valores se utilizan para actualizar el registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para conciliar los cambios en un conjunto de datos a la base de datos, tomando un <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, o una matriz de <xref:System.Data.DataRow>como parámetros de método.|
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos según los valores de columna original pasados como parámetros de método.|

 Para guardar los datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, mediante un bucle for next). Los valores para cada objeto se envían a la base de datos utilizando los métodos DBDirect del TableAdapter.

 El ejemplo siguiente muestra cómo usar el `TableAdapter.Insert` DBDirect de un método para agregar un nuevo cliente directamente en la base de datos:

 [!code-csharp[VbRaddataSaving#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form3.cs#23)]
 [!code-vb[VbRaddataSaving#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form3.vb#23)]

## <a name="see-also"></a>Vea también
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
