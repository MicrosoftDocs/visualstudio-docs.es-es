---
title: Rellenar conjuntos de datos mediante el uso de los TableAdapters
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic]
- datasets [Visual Basic], loading data
- data retrieval
- retrieving data
- datasets [Visual Basic], filling
- data [Visual Studio], retrieving
- data [Visual Studio], datasets
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 49f3aad9adf319c09097324a6c40a4aa7b8f6692
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="fill-datasets-by-using-tableadapters"></a>Rellenar conjuntos de datos mediante el uso de los TableAdapters
Un componente de TableAdapter rellena un dataset con los datos de la base de datos, en función de una o varias consultas o procedimientos almacenados que especifique. También puede realizar los TableAdapters agrega, actualizaciones y eliminaciones en la base de datos para conservar los cambios realizados en el conjunto de datos. También puede emitir comandos globales que están relacionados con una tabla específica.

> [!NOTE]
>  Los TableAdapters se generan los diseñadores de Visual Studio. Si va a crear conjuntos de datos mediante programación, use DataAdapter, que es una clase de .NET Framework.

 Para obtener información detallada acerca de las operaciones de TableAdapter, puede ir directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Cómo utilizar los diseñadores para crear y configurar los TableAdapters|
|[Crear consultas parametrizadas de TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Cómo permitir a los usuarios proporcionar argumentos de procedimientos de TableAdapter o a las consultas|
|[Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Cómo usar los métodos Dbdirect de TableAdapter|
|[Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Cómo trabajar con las restricciones foreign key durante la actualización de datos|
|[Cómo ampliar la funcionalidad de un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Cómo agregar código personalizado a TableAdapters|
|[Leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Cómo trabajar con XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Información general sobre TableAdapter
 Los TableAdapters son componentes generados por diseñador que se conectan a una base de datos, la ejecución de consultas o procedimientos almacenados y rellenar su DataTable con los datos devueltos. Los TableAdapters también enviar datos actualizados desde la aplicación a la base de datos. Puede ejecutar tantas consultas como desee en un TableAdapter, siempre y cuando devuelvan datos que se ajustan al esquema de la tabla al que está asociado el TableAdapter. El siguiente diagrama muestra cómo interactúan los objetos TableAdapter con bases de datos y otros objetos en memoria:

 ![Flujo de datos en una aplicación cliente](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")

 Aunque los objetos TableAdapter se diseñan con el **Diseñador de Dataset**, las clases TableAdapter no se generan como clases anidadas de <xref:System.Data.DataSet>. Se encuentran en espacios de nombres independientes que son específicas de cada conjunto de datos. Por ejemplo, si tiene un conjunto de datos denominado `NorthwindDataSet`, los TableAdapters que están asociados a <xref:System.Data.DataTable>s en el `NorthwindDataSet` estarían en el `NorthwindDataSetTableAdapters` espacio de nombres. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:

 [!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
 [!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado
 Cuando se crea un objeto TableAdapter, se utiliza la consulta inicial o procedimiento almacenado para definir el esquema del TableAdapter asociado <xref:System.Data.DataTable>. Ejecute esta consulta inicial o procedimiento almacenado mediante una llamada del TableAdapter `Fill` método (que rellena el TableAdapter asociado <xref:System.Data.DataTable>). Los cambios realizados en la consulta principal del TableAdapter se reflejan en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal también quita la columna de la tabla de datos asociada. Si alguna consulta adicional del TableAdapter utiliza instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intenta sincronizar los cambios de columna entre la consulta principal y las consultas adicionales.

## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter
 La funcionalidad de actualización de un objeto TableAdapter depende de la cantidad de información está disponible en la consulta principal en el Asistente de TableAdapter. Por ejemplo, los TableAdapter configurados para obtener valores de varias tablas (consultas JOIN), valores escalares, vistas o los resultados de funciones de agregado no se crean inicialmente con la capacidad de enviar actualizaciones a la base de datos subyacente. Sin embargo, puede configurar los comandos INSERT, UPDATE y DELETE manualmente en el **propiedades** ventana.

## <a name="tableadapter-queries"></a>consultas TableAdapter
 ![TableAdapter con varias consultas](../data-tools/media/tableadapter.gif "TableAdapter")

 Los TableAdapter pueden contener varias consultas que rellenan las tablas de datos asociados. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. Esta función permite un TableAdapter cargar resultados diferentes en función de distintos criterios.

 Por ejemplo, si la aplicación contiene una tabla con los nombres de cliente, puede crear una consulta que rellena la tabla con todos los nombres de cliente comienza con una letra determinada y otra que rellena la tabla con todos los clientes que se encuentran en el mismo estado. Para rellenar un `Customers` tabla con los clientes en un estado determinado, puede crear un `FillByState` consulta que acepta un parámetro para el valor de estado como sigue: `SELECT * FROM Customers WHERE State = @State`. Ejecute la consulta mediante una llamada a la `FillByState` método y pasando el valor del parámetro similar a éste: `CustomerTableAdapter.FillByState("WA")`.

 Además de agregar las consultas que devuelven datos del mismo esquema como tabla de datos del TableAdapter, puede agregar consultas que devuelven valores escalares de (únicos). Por ejemplo, una consulta que devuelve un recuento de clientes (`SELECT Count(*) From Customers`) es válida para un `CustomersTableAdapter,` incluso si los datos que se devuelven no es conforme al esquema de la tabla.

## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill
 De forma predeterminada, cada vez que ejecute una consulta para rellenar la tabla de datos del TableAdapter, se borran los datos existentes, y solo los resultados de la consulta se cargan en la tabla. Establecer el TableAdapter `ClearBeforeFill` propiedad `false` si desea agregar o combinar los datos que se devuelven de una consulta a los datos existentes en una tabla de datos. Sin tener en cuenta si borra los datos, debe enviar explícitamente las actualizaciones a la base de datos, si desea mantenerlas. Por tanto, recuerde guardar los cambios a los datos en la tabla antes de ejecutar otra consulta que rellena la tabla. Para obtener más información, consulte [actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter
 Los TableAdapter amplían la funcionalidad de los adaptadores de datos estándar encapsulando un <xref:System.Data.Common.DataAdapter> clase. De forma predeterminada, el objeto TableAdapter hereda de la <xref:System.ComponentModel.Component> clase y no se puede convertir el <xref:System.Data.Common.DataAdapter> clase. Convertir un TableAdapter a la <xref:System.Data.Common.DataAdapter> clase da como resultado un <xref:System.InvalidCastException> error. Para cambiar la clase base de un TableAdapter, puede especificar una clase que deriva de <xref:System.ComponentModel.Component> en el **clase Base** propiedad del TableAdapter en el **Diseñador de Dataset**.

## <a name="tableadapter-methods-and-properties"></a>Propiedades y métodos de TableAdapter
 La clase TableAdapter no forma parte de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Esto significa que no puede buscarla en la documentación o **Examinador de objetos**. Se crea en tiempo de diseño cuando utiliza uno de los asistentes que se ha mencionado anteriormente. El nombre que se asigna a un TableAdapter al crearlo se basa en el nombre de la tabla que está trabajando. Por ejemplo, cuando se crea un TableAdapter basado en una tabla en una base de datos denominada `Orders`, lo TableAdapter se denomina `OrdersTableAdapter`. Se puede cambiar el nombre de clase del TableAdapter utilizando la **nombre** propiedad en el **Diseñador de Dataset**.

 Siguientes son los métodos utilizados con frecuencia y las propiedades de los TableAdapters:

|Miembro|Descripción|
|------------|-----------------|
|`TableAdapter.Fill`|Rellena la tabla de datos asociada del TableAdapter con los resultados del comando SELECT del TableAdapter.|
|`TableAdapter.Update`|Envía los cambios a la base de datos y devuelve un entero que representa el número de filas afectadas por la actualización. Para obtener más información, consulte [actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Devuelve un nuevo <xref:System.Data.DataTable> que se rellena con datos.|
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, consulte [insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|

## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter
 Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. Inicial de TableAdapter `Fill` consulta (principal) se utiliza como base para crear el esquema de la tabla de datos asociada, así como el `InsertCommand`, `UpdateCommand`, y `DeleteCommand` comandos que están asociados a la `TableAdapter.Update` método. Llamar a un TableAdapter `Update` método ejecuta las instrucciones que se crearon al TableAdapter originalmente era configurado, no una de las consultas adicionales que se agregan con el **TableAdapter Query Configuration Wizard**.

 Cuando utiliza un TableAdapter, éste realiza las mismas operaciones con los comandos que realizaría habitualmente. Por ejemplo, cuando se llama el adaptador `Fill` método, el adaptador ejecuta el comando de datos en su `SelectCommand` propiedad y utiliza un lector de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataReader>) para cargar el conjunto de resultados en la tabla de datos. De forma similar, cuando se llama el adaptador `Update` método, se ejecuta el comando adecuado (en el `UpdateCommand`, `InsertCommand`, y `DeleteCommand` propiedades) para cada registro modificado de la tabla de datos.

> [!NOTE]
>  Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal de TableAdapter es más de una instrucción SELECT de tabla única, es posible que el diseñador no podrá generar `InsertCommand`, `UpdateCommand`, y `DeleteCommand`. Si no se generan estos comandos, podría recibir un error cuando ejecute la `TableAdapter.Update` método.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods
 Además `InsertCommand`, `UpdateCommand`, y `DeleteCommand`, los TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Se puede llamar a estos métodos (`TableAdapter.Insert`, `TableAdapter.Update` y `TableAdapter.Delete`) para manipular los datos directamente en la base de datos. Esto significa que puede llamar a estos métodos individuales desde el código en lugar de llamar `TableAdapter.Update` para controlar las inserciones, actualizaciones y eliminaciones que está pendientes para la tabla de datos asociada.

 Si no desea crear estos métodos directos, establezca el TableAdapter **GenerateDbDirectMethods** propiedad `false` (en el **propiedades** ventana). Consultas adicionales que se agregan al objeto TableAdapter son consultas independientes: no generan estos métodos.

## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad de TableAdapter con tipos que aceptan valores null
 Los TableAdapters admiten tipos que aceptan valores NULL `Nullable(Of T)` y `T?`. Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obtener más información acerca de los tipos que aceptan valores NULL en C#, vea [utilizar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

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

## <a name="security"></a>Seguridad
Cuando utilice comandos de datos con una propiedad CommandType establecida en <xref:System.Data.CommandType.Text>, cuidadosamente Compruebe la información que se envía desde un cliente antes de pasar a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir proporcionados por el usuario a una base de datos, compruebe siempre que la información es válida. Un procedimiento recomendado es siempre utilizar consultas parametrizadas o procedimientos almacenados cuando sea posible.

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos](../data-tools/dataset-tools-in-visual-studio.md)