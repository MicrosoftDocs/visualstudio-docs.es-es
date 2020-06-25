---
title: Rellenar conjuntos de datos mediante TableAdapters
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 888e2ac47348d7e61d115f51e3ea52d15ea9f447
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282441"
---
# <a name="fill-datasets-by-using-tableadapters"></a>Rellenar conjuntos de datos mediante TableAdapters

Un componente TableAdapter rellena un conjunto de datos con datos de la base de datos, basándose en una o más consultas o procedimientos almacenados especificados. Los TableAdapters también pueden realizar adiciones, actualizaciones y eliminaciones en la base de datos para conservar los cambios que se realicen en el conjunto de datos. También puede emitir comandos globales que no están relacionados con ninguna tabla específica.

> [!NOTE]
> Los diseñadores de Visual Studio generan los TableAdapters. Si va a crear conjuntos de valores mediante programación, use DataAdapter, que es una clase .NET.

Para obtener información detallada acerca de las operaciones de TableAdapter, puede ir directamente a uno de estos temas:

|Tema|Descripción|
|-----------|-----------------|
|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Cómo usar los diseñadores para crear y configurar TableAdapters|
|[Crear consultas parametrizadas de TableAdapter](../data-tools/create-parameterized-tableadapter-queries.md)|Cómo permitir que los usuarios proporcionen argumentos a procedimientos o consultas de TableAdapter|
|[Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Cómo usar los métodos DbDirect de TableAdapters|
|[Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Cómo trabajar con restricciones Foreign Key al actualizar datos|
|[Cómo extender la funcionalidad de un TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Cómo agregar código personalizado a los TableAdapters|
|[Leer datos XML en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md)|Cómo trabajar con XML|

<a name="tableadapter-overview"></a>

## <a name="tableadapter-overview"></a>Introducción a TableAdapter

Los TableAdapters son componentes generados por el diseñador que se conectan a una base de datos, ejecutan consultas o procedimientos almacenados y rellenan su DataTable con los datos devueltos. Los TableAdapters también envían datos actualizados desde la aplicación a la base de datos. Puede ejecutar tantas consultas como desee en un TableAdapter, siempre y cuando devuelvan datos que se ajusten al esquema de la tabla a la que está asociado el TableAdapter. En el diagrama siguiente se muestra cómo interactúan los TableAdapters con las bases de datos y otros objetos de la memoria:

![Flujo de datos de una aplicación cliente](../data-tools/media/clientdatadiagram.gif)

Aunque los TableAdapters están diseñados con el **Diseñador de DataSet**, las clases de TableAdapter no se generan como clases anidadas de <xref:System.Data.DataSet> . Se encuentran en espacios de nombres independientes que son específicos de cada conjunto de información. Por ejemplo, si tiene un conjunto de `NorthwindDataSet` objetos denominado, los TableAdapters asociados a <xref:System.Data.DataTable> s en el `NorthwindDataSet` se encontrarían en el espacio de `NorthwindDataSetTableAdapters` nombres. Para tener acceso a un TableAdapter determinado mediante programación, debe declarar una nueva instancia del TableAdapter. Por ejemplo:

[!code-csharp[VbRaddataTableAdapters#7](../data-tools/codesnippet/CSharp/fill-datasets-by-using-tableadapters_1.cs)]
[!code-vb[VbRaddataTableAdapters#7](../data-tools/codesnippet/VisualBasic/fill-datasets-by-using-tableadapters_1.vb)]

## <a name="associated-datatable-schema"></a>Esquema de DataTable asociado

Cuando se crea un TableAdapter, se usa la consulta inicial o el procedimiento almacenado para definir el esquema del asociado del TableAdapter <xref:System.Data.DataTable> . Ejecute esta consulta o procedimiento almacenado inicial llamando al método del TableAdapter `Fill` (que rellena el asociado del TableAdapter <xref:System.Data.DataTable> ). Cualquier cambio que se realice en la consulta principal del TableAdapter se refleja en el esquema de la tabla de datos asociada. Por ejemplo, al quitar una columna de la consulta principal, también se quita la columna de la tabla de datos asociada. Si alguna consulta adicional en el TableAdapter usa instrucciones SQL que devuelven columnas que no están en la consulta principal, el diseñador intenta sincronizar los cambios de la columna entre la consulta principal y las consultas adicionales.

## <a name="tableadapter-update-commands"></a>Comandos de actualización de TableAdapter

La funcionalidad de actualización de un TableAdapter depende de la cantidad de información disponible en la consulta principal en el **Asistente de TableAdapter**. Por ejemplo, los TableAdapters que están configurados para capturar valores de varias tablas (mediante `JOIN` ), valores escalares, vistas o los resultados de las funciones de agregado no se crean Inicialmente con la capacidad de volver a enviar las actualizaciones a la base de datos subyacente. Sin embargo, puede configurar `INSERT` manualmente los `UPDATE` comandos, y `DELETE` en la ventana **propiedades** .

## <a name="tableadapter-queries"></a>consultas TableAdapter

![TableAdapter con múltiples consultas](../data-tools/media/tableadapter.gif)

Los TableAdapters pueden contener varias consultas para rellenar las tablas de datos asociadas. Puede definir tantas consultas para un TableAdapter como requiera la aplicación, con tal de que cada consulta devuelva datos que cumplan el mismo esquema que la tabla de datos asociada. Esta funcionalidad permite a un TableAdapter cargar resultados diferentes en función de criterios diferentes.

Por ejemplo, si la aplicación contiene una tabla con nombres de cliente, puede crear una consulta que rellene la tabla con todos los nombres de clientes que comiencen con una letra determinada y otro que rellene la tabla con todos los clientes que se encuentran en el mismo estado. Para rellenar una `Customers` tabla con los clientes en un estado determinado, puede crear una `FillByState` consulta que tome un parámetro para el valor de estado de la manera siguiente: `SELECT * FROM Customers WHERE State = @State` . Ejecute la consulta llamando al `FillByState` método y pasando el valor del parámetro de la siguiente manera: `CustomerTableAdapter.FillByState("WA")` .

Además de agregar consultas que devuelven datos del mismo esquema que la tabla de datos del TableAdapter, puede Agregar consultas que devuelvan valores escalares (únicos). Por ejemplo, una consulta que devuelve un recuento de clientes ( `SELECT Count(*) From Customers` ) es válida para un a `CustomersTableAdapter,` pesar de que los datos devueltos no se ajustan al esquema de la tabla.

## <a name="clearbeforefill-property"></a>Propiedad ClearBeforeFill

De forma predeterminada, cada vez que se ejecuta una consulta para rellenar la tabla de datos de un TableAdapter, se borran los datos existentes y solo se cargan en la tabla los resultados de la consulta. Establezca la propiedad del TableAdapter `ClearBeforeFill` en `false` si desea agregar o combinar los datos devueltos de una consulta con los datos existentes en una tabla de datos. Independientemente de si borra los datos, deberá volver a enviar explícitamente las actualizaciones a la base de datos, si desea que se conserven. Por lo tanto, no olvide guardar los cambios realizados en los datos de la tabla antes de ejecutar otra consulta que llene la tabla. Para obtener más información, vea [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).

## <a name="tableadapter-inheritance"></a>Herencia de TableAdapter

Los TableAdapters amplían la funcionalidad de los adaptadores de datos estándar encapsulando una clase configurada <xref:System.Data.Common.DataAdapter> . De forma predeterminada, el TableAdapter hereda de la <xref:System.ComponentModel.Component> clase y no se puede convertir a la <xref:System.Data.Common.DataAdapter> clase. La conversión de un TableAdapter a la <xref:System.Data.Common.DataAdapter> clase produce un <xref:System.InvalidCastException> error. Para cambiar la clase base de un TableAdapter, puede especificar una clase que derive de <xref:System.ComponentModel.Component> en la propiedad de la **clase base** de tableadapter en el **Diseñador de DataSet**.

## <a name="tableadapter-methods-and-properties"></a>Métodos y propiedades de TableAdapter

La clase TableAdapter no es un tipo .NET. Esto significa que no se puede buscar en la documentación o en el **Examinador de objetos**. Se crea en tiempo de diseño cuando se usa uno de los asistentes mencionados anteriormente. El nombre que se asigna a un TableAdapter al crearlo se basa en el nombre de la tabla con la que está trabajando. Por ejemplo, cuando se crea un TableAdapter basado en una tabla de una base de datos denominada `Orders` , el TableAdapter se denomina `OrdersTableAdapter` . Se puede cambiar el nombre de clase del TableAdapter utilizando la propiedad **Name** en el **Diseñador de DataSet**.

A continuación se muestran los métodos y las propiedades de TableAdapters que se usan habitualmente:

|Miembro|Descripción|
|------------|-----------------|
|`TableAdapter.Fill`|Rellena la tabla de datos asociada del TableAdapter con los resultados del comando del TableAdapter `SELECT` .|
|`TableAdapter.Update`|Vuelve a enviar los cambios a la base de datos y devuelve un entero que representa el número de filas afectadas por la actualización. Para obtener más información, vea [actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|
|`TableAdapter.GetData`|Devuelve un nuevo <xref:System.Data.DataTable> que se rellena con datos.|
|`TableAdapter.Insert`|Crea una nueva fila en la tabla de datos. Para obtener más información, vea [Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md).|
|`TableAdapter.ClearBeforeFill`|Determina si se vacía una tabla de datos antes de llamar a uno de los métodos `Fill`.|

## <a name="tableadapter-update-method"></a>Método de actualización de TableAdapter

Los TableAdapter utilizan comandos de datos para leer y escribir en la base de datos. Utilice la `Fill` consulta inicial (principal) de TableAdapter como base para crear el esquema de la tabla de datos asociada, así como los `InsertCommand` comandos, `UpdateCommand` y asociados al `DeleteCommand` `TableAdapter.Update` método. La llamada al método de un TableAdapter `Update` ejecuta las instrucciones que se crearon cuando se configuró originalmente el TableAdapter, no una de las consultas adicionales que agregó con el **Asistente para configuración de consultas de TableAdapter**.

Cuando se utiliza un TableAdapter, realiza las mismas operaciones con los comandos que se realizarían normalmente. Por ejemplo, al llamar al método del adaptador `Fill` , el adaptador ejecuta el comando de datos en su `SelectCommand` propiedad y usa un lector de datos (por ejemplo, <xref:System.Data.SqlClient.SqlDataReader> ) para cargar el conjunto de resultados en la tabla de datos. Del mismo modo, cuando se llama al `Update` método del adaptador, se ejecuta el comando adecuado (en las `UpdateCommand` `InsertCommand` propiedades, y `DeleteCommand` ) para cada registro cambiado en la tabla de datos.

> [!NOTE]
> Si hay bastante información en la consulta principal, se crean los comandos `InsertCommand`, `UpdateCommand` y `DeleteCommand` de manera predeterminada cuando se genera el TableAdapter. Si la consulta principal del TableAdapter es más que una instrucción de tabla única `SELECT` , es posible que el diseñador no pueda generar `InsertCommand` , `UpdateCommand` y `DeleteCommand` . Si no se generan estos comandos, es posible que reciba un error al ejecutar el `TableAdapter.Update` método.

## <a name="tableadapter-generatedbdirectmethods"></a>TableAdapter GenerateDbDirectMethods

Además de `InsertCommand` , `UpdateCommand` y, los `DeleteCommand` TableAdapters se crean con métodos que se pueden ejecutar directamente en la base de datos. Puede llamar a estos métodos ( `TableAdapter.Insert` , `TableAdapter.Update` y `TableAdapter.Delete` ) directamente para manipular los datos de la base de datos. Esto significa que puede llamar a estos métodos individuales desde el código en lugar de llamar `TableAdapter.Update` a para controlar las inserciones, las actualizaciones y las eliminaciones pendientes para la tabla de datos asociada.

Si no desea crear estos métodos directos, establezca la propiedad **GenerateDbDirectMethods** de TableAdapter en `false` (en la ventana **propiedades** ). Las consultas adicionales que se agregan a TableAdapter son consultas independientes; no generan estos métodos.

## <a name="tableadapter-support-for-nullable-types"></a>Compatibilidad del objeto TableAdapter con los tipos que aceptan valores NULL

Los TableAdapters admiten tipos que aceptan valores NULL `Nullable(Of T)` y `T?` . Para más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos que admiten valores null](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obtener más información sobre los tipos que aceptan valores NULL en C#, vea [usar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).

<a name="tableadaptermanager-reference"></a>

## <a name="tableadaptermanager-reference"></a>Referencia de TableAdapterManager

De forma predeterminada, una clase TableAdapterManager genera cuando se crea un conjunto de DataSet que contiene tablas relacionadas. Para evitar que se genere la clase, cambie el valor de la `Hierarchical Update` propiedad del conjunto de valores a false. Cuando se arrastra una tabla que tiene una relación en la superficie de diseño de una página de Windows Forms o de WPF, Visual Studio declara una variable miembro de la clase. Si no usa DataBinding, tendrá que declarar manualmente la variable.

La clase TableAdapterManager no es un tipo .NET. Por lo tanto, no se puede buscar en la documentación. Se crea en tiempo de diseño como parte del proceso de creación del conjunto de elementos.

A continuación se muestran los métodos y las propiedades de la clase que se usan con frecuencia `TableAdapterManager` :

|Miembro|Descripción|
|------------|-----------------|
|Método `UpdateAll`|Guarda todos los datos de todas las tablas de datos.|
|Propiedad `BackUpDataSetBeforeUpdate`|Determina si se va a crear una copia de seguridad del conjunto de archivos antes de ejecutar el `TableAdapterManager.UpdateAll` método. Booleano.|
|*TableName* `TableAdapter` propiedad|Representa un TableAdapter. El TableAdapterManager generado contiene una propiedad para cada `TableAdapter` que administra. Por ejemplo, un conjunto de DataSet con una tabla Customers y Orders genera con un TableAdapterManager que contiene `CustomersTableAdapter` `OrdersTableAdapter` las propiedades y.|
|Propiedad `UpdateOrder`|Controla el orden de los comandos de inserción, actualización y eliminación individuales. Establézcalo en uno de los valores de la `TableAdapterManager.UpdateOrderOption` enumeración.<br /><br /> De forma predeterminada, `UpdateOrder` se establece en **InsertUpdateDelete**. Esto significa que las inserciones, las actualizaciones y las eliminaciones se realizan para todas las tablas del conjunto de DataSet.|

## <a name="security"></a>Seguridad

Al utilizar comandos de datos con una propiedad CommandType establecida en <xref:System.Data.CommandType.Text> , compruebe cuidadosamente la información que se envía desde un cliente antes de pasarla a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir la entrada del usuario a una base de datos, compruebe siempre que la información es válida. Un procedimiento recomendado es usar siempre consultas con parámetros o procedimientos almacenados cuando sea posible.

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de herramientas](../data-tools/dataset-tools-in-visual-studio.md)
