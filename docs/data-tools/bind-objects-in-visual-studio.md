---
title: Enlazar datos a objetos personalizados
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], object binding
- data [Visual Studio], binding to objects
- object binding
- binding, to objects
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a1d72ed179324b8ab7682e485fbaaf8f34b25cd4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282935"
---
# <a name="bind-objects-as-data-sources-in-visual-studio"></a>Enlazar objetos como orígenes de datos en Visual Studio

Visual Studio proporciona herramientas en tiempo de diseño para trabajar con objetos personalizados como origen de datos en la aplicación. Si desea almacenar los datos de una base de datos en un objeto enlazado a controles de interfaz de usuario, el enfoque recomendado es usar Entity Framework para generar la clase o las clases. Entity Framework genera automáticamente todo el código reutilizable de seguimiento de cambios, lo que significa que los cambios en los objetos locales se conservan automáticamente en la base de datos cuando se llama a AcceptChanges en el objeto DbSet. Para obtener más información, consulte la [documentación de Entity Framework](https://ef.readthedocs.org/en/latest/).

> [!TIP]
> Los enfoques de enlace de objeto de este artículo solo se deben tener en cuenta si la aplicación ya se basa en conjuntos de objetos. También puede usar estos enfoques si ya está familiarizado con los conjuntos de datos y los datos que va a procesar son tabulares y no demasiado complejos o demasiado grandes. Para obtener un ejemplo aún más sencillo, que implique la carga de datos directamente en objetos mediante un DataReader y la actualización manual de la interfaz de usuario sin el enlace de datos, consulte [creación de una aplicación de datos sencilla mediante ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

## <a name="object-requirements"></a>Requisitos de objetos

El único requisito para que los objetos personalizados funcionen con las herramientas de diseño de datos en Visual Studio es que el objeto necesita al menos una propiedad pública.

Por lo general, los objetos personalizados no requieren interfaces, constructores o atributos específicos para actuar como origen de datos de una aplicación. Sin embargo, si desea arrastrar el objeto desde la ventana **orígenes de datos** a una superficie de diseño para crear un control enlazado a datos, y si el objeto implementa <xref:System.ComponentModel.ITypedList> la <xref:System.ComponentModel.IListSource> interfaz o, el objeto debe tener un constructor predeterminado. De lo contrario, Visual Studio no puede crear una instancia del objeto de origen de datos y muestra un error al arrastrar el elemento a la superficie de diseño.

## <a name="examples-of-using-custom-objects-as-data-sources"></a>Ejemplos de uso de objetos personalizados como orígenes de datos

Aunque existen innumerables formas de implementar la lógica de la aplicación cuando se trabaja con objetos como un origen de datos, para las bases de datos SQL hay algunas operaciones estándar que se pueden simplificar mediante el uso de los objetos TableAdapter generados por Visual Studio. En esta página se explica cómo implementar estos procesos estándar mediante TableAdapters. No se ha diseñado como guía para la creación de objetos personalizados. Por ejemplo, normalmente se realizan las siguientes operaciones estándar independientemente de la implementación específica de los objetos o de la lógica de la aplicación:

- Cargar datos en objetos (normalmente desde una base de datos).

- Crear una colección de objetos con tipo.

- Agregar objetos y quitar objetos de una colección.

- Mostrar los datos de objeto a los usuarios de un formulario.

- Cambiar o modificar los datos de un objeto.

- Volver a guardar los datos de los objetos en la base de datos.

### <a name="load-data-into-objects"></a>Cargar datos en objetos

En este ejemplo, los datos se cargan en los objetos mediante TableAdapters. De forma predeterminada, los TableAdapters se crean con dos tipos de métodos que capturan datos de una base de datos y rellenan tablas de datos.

- El `TableAdapter.Fill` método rellena una tabla de datos existente con los datos devueltos.

- El `TableAdapter.GetData` método devuelve una nueva tabla de datos rellenada con datos.

La forma más fácil de cargar los objetos personalizados con datos es llamar al `TableAdapter.GetData` método, recorrer la colección de filas de la tabla de datos devuelta y rellenar cada objeto con los valores de cada fila. Puede crear un `GetData` método que devuelva una tabla de datos rellenada para cualquier consulta agregada a un TableAdapter.

> [!NOTE]
> Visual Studio nombra las consultas de TableAdapter `Fill` y `GetData` , de forma predeterminada, puede cambiar los nombres a cualquier nombre de método válido.

En el ejemplo siguiente se muestra cómo recorrer en bucle las filas de una tabla de datos y rellenar un objeto con datos:

[!code-csharp[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
[!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]

### <a name="create-a-typed-collection-of-objects"></a>Crear una colección de objetos con tipo

Puede crear clases de colección para los objetos o usar las colecciones con tipo que el [componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component)proporciona automáticamente.

Al crear una clase de colección personalizada para los objetos, se recomienda que herede de <xref:System.ComponentModel.BindingList%601> . Esta clase genérica proporciona funcionalidad para administrar la colección, así como la capacidad de generar eventos que envían notificaciones a la infraestructura de enlace de datos en Windows Forms.

La colección generada automáticamente en <xref:System.Windows.Forms.BindingSource> utiliza <xref:System.ComponentModel.BindingList%601> para su colección con tipo. Si la aplicación no requiere ninguna funcionalidad adicional, puede mantener la colección dentro de <xref:System.Windows.Forms.BindingSource> . Para obtener más información, vea la <xref:System.Windows.Forms.BindingSource.List%2A> propiedad de la <xref:System.Windows.Forms.BindingSource> clase.

> [!NOTE]
> Si la colección requiere funcionalidad no proporcionada por la implementación base de <xref:System.ComponentModel.BindingList%601> , debe crear una colección personalizada para que pueda agregar a la clase según sea necesario.

En el código siguiente se muestra cómo crear la clase para una colección fuertemente tipada de `Order` objetos:

[!code-csharp[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
[!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]

### <a name="add-objects-to-a-collection"></a>Agregar objetos a una colección

Los objetos se agregan a una colección llamando al `Add` método de la clase de colección personalizada o del objeto <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> El `Add` método se proporciona automáticamente para la colección personalizada cuando se hereda de <xref:System.ComponentModel.BindingList%601> .

En el código siguiente se muestra cómo agregar objetos a la colección con tipo en un <xref:System.Windows.Forms.BindingSource> :

[!code-csharp[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
[!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]

En el código siguiente se muestra cómo agregar objetos a una colección con tipo que hereda de <xref:System.ComponentModel.BindingList%601> :

> [!NOTE]
> En este ejemplo, la `Orders` colección es una propiedad del `Customer` objeto.

[!code-csharp[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
[!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]

### <a name="remove-objects-from-a-collection"></a>Quitar objetos de una colección

Los objetos de una colección se quitan llamando `Remove` al `RemoveAt` método o de la clase de colección personalizada o de <xref:System.Windows.Forms.BindingSource> .

> [!NOTE]
> Los `Remove` `RemoveAt` métodos y se proporcionan automáticamente para la colección personalizada cuando se hereda de <xref:System.ComponentModel.BindingList%601> .

En el código siguiente se muestra cómo buscar y quitar objetos de la colección con tipo en un <xref:System.Windows.Forms.BindingSource> con el <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> método:

[!code-csharp[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
[!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]

### <a name="display-object-data-to-users"></a>Mostrar datos de objetos a los usuarios

Para mostrar los datos de los objetos a los usuarios, cree un origen de datos de objeto mediante el Asistente para la **configuración de orígenes de datos** y, a continuación, arrastre todo el objeto o las propiedades individuales al formulario desde la ventana orígenes de **datos** .

### <a name="modify-the-data-in-objects"></a>Modificar los datos de los objetos

Para editar los datos de los objetos personalizados que están enlazados a datos a controles Windows Forms, simplemente edite los datos en el control enlazado (o directamente en las propiedades del objeto). La arquitectura de enlace de datos actualiza los datos del objeto.

Si su aplicación requiere el seguimiento de los cambios y la reversión de los cambios propuestos a sus valores originales, debe implementar esta funcionalidad en el modelo de objetos. Para obtener ejemplos de cómo las tablas de datos realizan un seguimiento de los cambios propuestos, vea <xref:System.Data.DataRowState> , <xref:System.Data.DataSet.HasChanges%2A> y <xref:System.Data.DataTable.GetChanges%2A> .

### <a name="save-data-in-objects-back-to-the-database"></a>Volver a guardar los datos de los objetos en la base de datos

Vuelva a guardar los datos en la base de datos pasando los valores del objeto a los métodos DBDirect del TableAdapter.

Visual Studio crea métodos DBDirect que se pueden ejecutar directamente en la base de datos. Estos métodos no requieren objetos DataSet o DataTable.

|Método de TableAdapter DBDirect|Descripción|
| - |-----------------|
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos, lo que permite pasar valores de columna individuales como parámetros de método.|
|`TableAdapter.Update`|Actualiza los registros existentes en una base de datos. El método Update toma los valores de columna originales y nuevos como parámetros de método. Los valores originales se utilizan para buscar el registro original y los nuevos valores se usan para actualizar el registro.<br /><br /> El `TableAdapter.Update` método también se utiliza para reconciliar los cambios de un conjunto de datos en la base de datos, tomando una <xref:System.Data.DataSet> <xref:System.Data.DataTable> matriz de,, <xref:System.Data.DataRow> o de <xref:System.Data.DataRow> s como parámetros de método.|
|`TableAdapter.Delete`|Elimina los registros existentes de la base de datos en función de los valores de columna originales pasados como parámetros de método.|

Para guardar datos de una colección de objetos, recorra en iteración la colección de objetos (por ejemplo, usando un bucle for-Next). Envíe los valores de cada objeto a la base de datos mediante los métodos DBDirect del TableAdapter.

En el ejemplo siguiente se muestra cómo utilizar el `TableAdapter.Insert` método DBDirect para agregar un nuevo cliente directamente a la base de datos:

[!code-csharp[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
[!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]

## <a name="see-also"></a>Vea también

- [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
