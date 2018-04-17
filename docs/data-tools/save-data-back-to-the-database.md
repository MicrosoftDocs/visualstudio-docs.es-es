---
title: Guardar datos en la base de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1e7d2b27f0d90677d99d3f0fbc434493fdc7da83
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="save-data-back-to-the-database"></a>Guardar datos en la base de datos
El conjunto de datos es una copia en memoria de datos. Si modifica datos, es una buena práctica para guardar los cambios en la base de datos. Para ello en uno de tres maneras:  
  
-   Llamando a uno de los métodos de actualización de un TableAdapter  
  
-   Llamando a uno de los métodos DBDirect de TableAdapter  
  
-   Llamando al método UpdateAll en TableAdapterManager que Visual Studio genera automáticamente cuando el conjunto de datos contiene tablas que están relacionadas con otras tablas del conjunto de datos  
  
Al enlazar a datos las tablas de conjunto de datos a controles en una página XAML o formulario Windows Forms, la arquitectura de enlace de datos realiza todo el trabajo automáticamente.  
  
Si está familiarizado con los TableAdapters, puede ir directamente a uno de estos temas:  
  
|Tema|Descripción|  
|-----------|-----------------|  
|[Insertar nuevos registros en una base de datos](../data-tools/insert-new-records-into-a-database.md)|Cómo realizar actualizaciones e inserta con objetos TableAdapters o un comando|  
|[Actualizar datos mediante un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Cómo realizar actualizaciones con TableAdapters|  
|[Actualización jerárquica](../data-tools/hierarchical-update.md)|Cómo realizar actualizaciones de un conjunto de datos con dos o más tablas relacionadas|  
|[Tratar las excepciones de simultaneidad](../data-tools/handle-a-concurrency-exception.md)|Cómo controlar las excepciones cuando dos usuarios intentan cambiar los mismos datos en una base de datos al mismo tiempo|  
|[Cómo: guardar datos utilizando una transacción](../data-tools/save-data-by-using-a-transaction.md)|Cómo guardar datos en una transacción utilizando el espacio de nombres System.Transactions y un objeto TransactionScope|  
|[Tutorial: Guardado de datos en una transacción](../data-tools/save-data-in-a-transaction.md)|Tutorial en el que se crea una aplicación de formularios Windows Forms para mostrar guardar datos en una base de datos dentro de una transacción|  
|[Guardar datos en una base de datos (varias tablas)](../data-tools/save-data-to-a-database-multiple-tables.md)|Cómo editar los registros y guardar los cambios en varias tablas a la base de datos|  
|[Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)|Cómo pasar datos de un objeto que no está en un conjunto de datos a una base de datos mediante un método DbDirect de TableAdapter|  
|[Guardar datos con los métodos DBDirect de un TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Cómo usar el objeto TableAdapter para enviar consultas SQL directamente a la base de datos|  
|[Guardar un conjunto de datos como XML](../data-tools/save-a-dataset-as-xml.md)|Cómo guardar un conjunto de datos en un documento XML|  
  
## <a name="two-stage-updates"></a>Actualizaciones en dos fases  
 Actualizar un origen de datos es un proceso de dos pasos. El primer paso es actualizar el conjunto de datos con nuevos registros, registros cambiados o registros eliminados. Si la aplicación nunca envía esos cambios en el origen de datos, a continuación, haya terminado con la actualización.  
  
 Si envía los cambios a la base de datos, un segundo paso es necesario. Si no está utilizando controles enlazados a datos, a continuación, se debe llamar manualmente al método Update del mismo TableAdapter (o adaptador de datos) que se utilizó para llenar el conjunto de datos. Sin embargo, también puede utilizar adaptadores diferentes, por ejemplo, para mover datos desde un origen de datos a otro o para actualizar múltiples orígenes de datos. Si no está usando el enlace de datos y está guardando los cambios para las tablas relacionadas, tendrá que crear manualmente una instancia de una variable de la clase de TableAdapterManager generado automáticamente y, a continuación, llame a su método UdpateAll.  
  
 ![Las actualizaciones del conjunto de datos de Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Proceso de actualización en dos fases y rol de DataRowVersion en una actualización correcta  
  
 Un conjunto de datos contiene colecciones de las tablas que contienen una colección de filas. Si tiene previsto actualizar un origen de datos subyacente más adelante, debe utilizar los métodos en la propiedad DataTable.DataRowCollection al agregar o quitar las filas. Los métodos realizan el seguimiento de cambios que se necesita para actualizar el origen de datos. Si se llama a la colección RemoveAt en la propiedad de filas, la eliminación no se comunican a la base de datos.  
  
## <a name="merge-datasets"></a>Combinar conjuntos de datos  
 Puede actualizar el contenido de un conjunto de datos por *combinar* con otro conjunto de datos. Esto implica copiar el contenido de un *origen* conjunto de datos en el conjunto de datos que realiza la llamada (denominados el *destino* conjunto de datos). Cuando se fusionan mediante combinación conjuntos de datos, los registros nuevos del conjunto de datos de origen se agregan al conjunto de datos de destino. Asimismo, las columnas adicionales del conjunto de datos de origen se agregan al conjunto de datos de destino. Combinar conjuntos de datos es útil cuando tiene un conjunto de datos local y obtenga un segundo conjunto de datos desde otra aplicación. También es útil cuando se obtiene un segundo conjunto de datos desde un componente como un servicio web XML, o cuando necesite integrar datos procedentes de varios conjuntos de datos.  
  
 Al combinar conjuntos de datos, puede pasar un argumento booleano (`preserveChanges`) que indica la <xref:System.Data.DataSet.Merge%2A> método si desea conservar las modificaciones existentes del conjunto de datos de destino. Debido a que los conjuntos de datos mantienen varias versiones de los registros, es importante tener en cuenta que se está combinada más de una versión de los registros. En la tabla siguiente se muestra cómo se combina un registro en dos conjuntos de datos:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|--------------------|--------------------|  
|Original|James Wilson|James C. Wilson|  
|Current|Jim Wilson|James C. Wilson|  
  
 Llamar a la <xref:System.Data.DataSet.Merge%2A> método en la tabla anterior con `preserveChanges=false targetDataset.Merge(sourceDataset)` Obtiene el siguiente resultado:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|--------------------|--------------------|  
|Original|James C. Wilson|James C. Wilson|  
|Current|James C. Wilson|James C. Wilson|  
  
 Al llamar al método <xref:System.Data.DataSet.Merge%2A> con `preserveChanges = true targetDataset.Merge(sourceDataset, true)`, se obtiene el siguiente resultado:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|--------------------|--------------------|  
|Original|James C. Wilson|James C. Wilson|  
|Current|Jim Wilson|James C. Wilson|  
  
> [!CAUTION]
>  En el `preserveChanges = true` escenario, si la <xref:System.Data.DataSet.RejectChanges%2A> método se llama en un registro en el conjunto de datos de destino, a continuación, vuelve a los datos originales de la *origen* conjunto de datos. Esto significa que si se intenta actualizar el origen de datos original con el conjunto de datos de destino, no sería capaz de encontrar la fila original para actualizar. Puede evitar que una infracción de simultaneidad rellenando otro conjunto de datos con los registros actualizados del origen de datos y, a continuación, realizar una combinación para evitar que una infracción de simultaneidad. (Una infracción de simultaneidad se produce cuando otro usuario modifica un registro del origen de datos después de que se ha rellenado el conjunto de datos.)  
  
## <a name="update-constraints"></a>Restricciones de actualización  
 Para realizar cambios en una fila de datos existente, agregar o actualizar datos en las columnas individuales. Si el conjunto de datos contiene restricciones (como claves externas o restricciones que no aceptan valores NULL), es posible que el registro pueda encontrarse temporalmente en un estado de error tal y como lo actualice. Es decir, puede ser en un estado de error cuando termine de actualizar una columna pero antes de pasar al siguiente.  
  
 Para impedir que se produzcan infracciones de restricciones prematuras, puede suspender temporalmente las restricciones de actualización. Esta suspensión tiene dos fines:  
  
-   Impide que un error que se produce una vez que haya terminado de actualizar una columna pero no ha empezado a actualizar a otra.  
  
-   Se evita que determinadas actualizaciones los eventos que producen (eventos que suelen utilizarse para la validación).  
   
> [!NOTE]
>  En Windows Forms, la arquitectura de enlace de datos que está integrada en la cuadrícula de datos suspende la restricción de comprobación hasta que el foco sale de una fila, y no es necesario llamar explícitamente a la <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, o <xref:System.Data.DataRow.CancelEdit%2A> métodos.  
  
 Las restricciones se deshabilitan automáticamente cuando se invoca el método <xref:System.Data.DataSet.Merge%2A> en un conjunto de datos. Cuando la combinación finaliza, si no hay ninguna restricción en el conjunto de datos que no se puede habilitar, un <xref:System.Data.ConstraintException> se produce. En esta situación, la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> se establece en `false,` y todas las infracciones de las restricciones se deben resolver antes de restablecer la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> a `true`.  
  
 Después de completar una actualización, puede volver a habilitar la comprobación de restricción, que también vuelve a habilitar eventos de actualización e iniciarlos.  
  
 Para obtener más información sobre la suspensión de eventos, vea [desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## <a name="dataset-update-errors"></a>Errores de actualización del conjunto de datos  
 Cuando se actualiza un registro de un conjunto de datos, existe la posibilidad de que se produzca un error. Por ejemplo, podría escribir accidentalmente datos de un tipo incorrecto a una columna, o datos que es demasiado largos o datos que tenga algún otro problema de integridad. O bien, es posible que tenga las comprobaciones de validación específica de la aplicación que generen errores personalizados durante cualquier fase de un evento de actualización. Para obtener más información, consulte [validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## <a name="maintaining-information-about-changes"></a>Mantener la información acerca de los cambios  
 Información sobre los cambios en un conjunto de datos se mantiene de dos formas: marcando filas que indican que han cambiado (<xref:System.Data.DataRow.RowState%2A>) y guardando varias copias de un registro (<xref:System.Data.DataRowVersion>). Con esta información, los procesos pueden determinar qué ha cambiado en el conjunto de datos y pueden enviar las actualizaciones correspondientes al origen de datos.  
  
### <a name="rowstate-property"></a>Propiedad RowState  
 La propiedad <xref:System.Data.DataRow.RowState%2A> de un objeto <xref:System.Data.DataRow> es un valor que proporciona información sobre el estado de una fila de datos determinada.  
  
 En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowState>:  
  
|Valor de DataRowState|Descripción|  
|------------------------|-----------------|  
|<xref:System.Data.DataRowState.Added>|La fila se ha agregado como elemento a <xref:System.Data.DataRowCollection>. (Una fila con este estado no tiene una versión original correspondiente, ya que no existía cuando el último <xref:System.Data.DataRow.AcceptChanges%2A> método se llamó).|  
|<xref:System.Data.DataRowState.Deleted>|La fila se eliminó utilizando el método <xref:System.Data.DataRow.Delete%2A> de un objeto <xref:System.Data.DataRow>.|  
|<xref:System.Data.DataRowState.Detached>|La fila se ha creado pero no forma parte de ninguna <xref:System.Data.DataRowCollection>. Un <xref:System.Data.DataRow> objeto se encuentra en este estado inmediatamente después de que se ha creado, antes de que se ha agregado a una colección y una vez que se ha quitado de una colección.|  
|<xref:System.Data.DataRowState.Modified>|Un valor de columna en la fila ha cambiado de alguna manera.|  
|<xref:System.Data.DataRowState.Unchanged>|La fila no ha cambiado desde la última vez que se llamó a <xref:System.Data.DataRow.AcceptChanges%2A>.|  
  
### <a name="datarowversion-enumeration"></a>DataRowVersion (enumeración)  
Los conjuntos de datos mantienen varias versiones de los registros. El <xref:System.Data.DataRowVersion> al recuperar el valor encontrado en campos que se pueden usar un <xref:System.Data.DataRow> mediante la <xref:System.Data.DataRow.Item%2A> propiedad o el <xref:System.Data.DataRow.GetChildRows%2A> método de la <xref:System.Data.DataRow> objeto.  
  
En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowVersion>:  
  
|Valor de DataRowVersion|Descripción|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|La versión actual de un registro contiene todas las modificaciones que se han realizado en el registro desde la última vez <xref:System.Data.DataRow.AcceptChanges%2A> se llamó. Si se ha eliminado la fila, no hay ninguna versión actual.|  
|<xref:System.Data.DataRowVersion.Default>|Es el valor predeterminado de un registro, tal como se define en el esquema del conjunto de datos o en el origen de datos.|  
|<xref:System.Data.DataRowVersion.Original>|La versión original de un registro es una copia del registro tal como se encontraba la última vez que se confirmaron cambios en el conjunto de datos. En términos prácticos, suele ser la versión de un registro leído de un origen de datos.|  
|<xref:System.Data.DataRowVersion.Proposed>|La versión propuesta de un registro que está disponible temporalmente mientras está en curso una actualización, es decir, entre el momento en que se llamó el <xref:System.Data.DataRow.BeginEdit%2A> método y el <xref:System.Data.DataRow.EndEdit%2A> método. Normalmente, se obtiene acceso a la versión propuesta de un registro en un controlador de un evento tal como <xref:System.Data.DataTable.RowChanging>. Al invocar al método <xref:System.Data.DataRow.CancelEdit%2A>, se anulan los cambios y se elimina la versión propuesta de la fila de datos.|  
  
 Las versiones original y actual son de utilidad cuando se transmite la información de actualización a un origen de datos. Normalmente, cuando envía una actualización al origen de datos, la nueva información de la base de datos está en la versión actual de un registro. Para buscar el registro que actualizar se utiliza información de la versión original.  
  
 Por ejemplo, en un caso donde se cambia la clave principal de un registro, necesita una manera de buscar el registro correcto en el origen de datos para actualizar los cambios. Si no existiese una versión original, lo más probable es que el registro se agregase al final del origen de datos, con lo que se obtendría no sólo un registro adicional no deseado, sino que, además, sería inexacto y obsoleto. Las dos versiones también se usan en el control de simultaneidad. Puede comparar la versión original con un registro en el origen de datos para determinar si el registro ha cambiado desde que se cargó en el conjunto de datos.  
  
 La versión propuesta es de utilidad cuando se necesita realizar una validación antes de confirmar los cambios en el conjunto de datos.  
  
 Incluso aunque los registros hayan cambiado, no siempre hay versiones originales o actuales de esa fila. Cuando se inserta una fila nueva en la tabla, no hay versión original, sólo una versión actual. Lo mismo sucede si se elimina una fila mediante una llamada al método `Delete` de la tabla: hay una versión original, pero no hay versión actual.  
  
 Para comprobar si existe una versión específica de un registro, haga una consulta al método <xref:System.Data.DataRow.HasVersion%2A> de una fila de datos. Para obtener acceso a cualquiera de las versiones de un registro, pase un valor de la enumeración <xref:System.Data.DataRowVersion> como argumento opcional cuando solicite el valor de una columna.  
  
## <a name="getting-changed-records"></a>Obtener los registros modificados  
 Es una práctica común no se actualizan todos los registros en un conjunto de datos. Por ejemplo, un usuario puede estar trabajando con un control <xref:System.Windows.Forms.DataGridView> de formularios Windows Forms que muestre muchos registros, pero puede actualizar sólo algunos, eliminar uno e insertar otro. Los conjuntos de datos y las tablas de datos proporcionan un método (`GetChanges`) para devolver sólo las filas que se hayan modificado.  
  
 Es posible crear subconjuntos de registros modificados con el método `GetChanges` de cualquiera de las tablas de datos (<xref:System.Data.DataTable.GetChanges%2A>) o del propio conjunto de datos (<xref:System.Data.DataSet.GetChanges%2A>). Si se llama al método de la tabla de datos, devuelve una copia de la tabla donde sólo se muestran los registros cambiados. De igual forma, si llama al método en el conjunto de datos, obtiene un nuevo conjunto de datos solo con los registros modificados.  
  
 `GetChanges` por sí solo devuelve todos los registros modificados. En cambio, pasando el deseado <xref:System.Data.DataRowState> como un parámetro a la `GetChanges` método, puede especificar qué subconjunto de registros cambiados desea: recién agregado registros, registros marcados para su eliminación, registros desasociados o registros modificados.  
  
 Obtener un subconjunto de registros modificados es útil cuando desea enviar registros a otro componente para su procesamiento. En lugar de enviar todo el conjunto de datos, se puede reducir la sobrecarga de la comunicación con el otro componente al obtener únicamente los registros necesarios.   
  
## <a name="committing-changes-in-the-dataset"></a>Confirmar los cambios en el conjunto de datos  
 Cuando se realizan cambios en el conjunto de datos, se establece la propiedad <xref:System.Data.DataRow.RowState%2A> de las filas modificadas. Las versiones originales y actuales de registros se establece, mantiene y que pone a disposición mediante el <xref:System.Data.DataRowView.RowVersion%2A> propiedad. Los metadatos que se almacenan en las propiedades de estas filas modificadas están necesario para enviar las actualizaciones correctas para el origen de datos.  
  
 Si los cambios reflejan el estado actual del origen de datos, ya no es necesario mantener esta información. Por lo general, hay dos veces cuando el conjunto de datos y su origen están sincronizados:  
  
-   Inmediatamente después de haber cargado información en el conjunto de datos; por ejemplo, cuando lee datos del origen.  
  
-   Después de enviar los cambios desde el conjunto de datos al origen de datos (pero no antes, porque se perdería la información de los cambios que se necesita para enviar los cambios a la base de datos).  
  
Para confirmar los cambios pendientes en el conjunto de datos, puede llamar al método <xref:System.Data.DataSet.AcceptChanges%2A>. Por lo general, <xref:System.Data.DataSet.AcceptChanges%2A> se llama en los momentos siguientes:  
  
-   Después de cargar el conjunto de datos. Si se carga un conjunto de datos mediante una llamada al método `Fill` del TableAdapter, este adaptador confirma los cambios automáticamente. Sin embargo, si carga un conjunto de datos mediante la combinación de otro conjunto de datos, los cambios se deben confirmar manualmente.  
  
    > [!NOTE]
    >  Puede impedir que el adaptador confirme los cambios automáticamente al llamar a la `Fill` método estableciendo la `AcceptChangesDuringFill` propiedad del adaptador `false`. Si se establece en `false`, la <xref:System.Data.DataRow.RowState%2A> de cada fila que se inserta durante el relleno se establece en <xref:System.Data.DataRowState.Added>.  
  
-   Después de enviar los cambios de conjunto de datos a otro proceso, como un servicio Web XML.  
  
    > [!CAUTION]
    >  Si confirma el cambio de este modo, se borra la información sobre cambios existente. No confirmar los cambios hasta que haya termine de realizar las operaciones que requieren la aplicación saber qué cambios se realizaron en el conjunto de datos.  
  
Este método realiza las funciones siguientes:  
  
-   Escribe el <xref:System.Data.DataRowVersion.Current> versión de un registro en su <xref:System.Data.DataRowVersion.Original> versión y sobrescribe la versión original.  
  
-   Quita cualquier fila donde el <xref:System.Data.DataRow.RowState%2A> propiedad está establecida en <xref:System.Data.DataRowState.Deleted>.  
  
-   Establece la propiedad <xref:System.Data.DataRow.RowState%2A> de un registro en <xref:System.Data.DataRowState.Unchanged>.  
  
El método <xref:System.Data.DataSet.AcceptChanges%2A> está disponible en tres niveles. También puede llamarlo en un <xref:System.Data.DataRow> objeto a confirmaciones cambia sólo para esa fila. También puede llamarlo sobre un <xref:System.Data.DataTable> objeto para confirmar todas las filas de una tabla. Por último, se pueden llamar en el <xref:System.Data.DataSet> objeto para confirmar todos los cambios pendientes en todos los registros de todas las tablas del conjunto de datos.  
  
En la tabla siguiente se describen los cambios que se confirman en función del objeto en el que se llame el método.  
  
|Método|Resultado|  
|------------|------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman sólo en una fila específica.|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de una tabla específica.|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de todas las tablas del conjunto de datos.|  
  
> [!NOTE]
>  Si se carga un conjunto de datos mediante una llamada a un TableAdapter `Fill` método, no tiene que aceptar los cambios explícitamente. De forma predeterminada, el `Fill` llamadas al método el `AcceptChanges` método después de que termine de rellenar la tabla de datos.  
  
 Un método relacionado, <xref:System.Data.DataSet.RejectChanges%2A>, deshace el efecto de los cambios copiando la <xref:System.Data.DataRowVersion.Original> versión en la <xref:System.Data.DataRowVersion.Current> versión de registros. También establece la <xref:System.Data.DataRow.RowState%2A> de cada registro de nuevo en <xref:System.Data.DataRowState.Unchanged>.  
  
## <a name="data-validation"></a>Validación de datos  
 Para comprobar que los datos de una aplicación satisfacen los requisitos de los procesos a los que se pasan, normalmente se agrega validación. Esto podría significar tener que comprobar que la entrada de un usuario en un formulario es correcta, validación de datos que se envían a la aplicación por otra aplicación, o incluso comprobar que la información que se calcula dentro de un componente se encuentra dentro de las restricciones del origen de datos y requisitos de la aplicación.  
  
 Los datos se pueden validar de distintas maneras:  
  
-   En la capa de empresa, agregando código a la aplicación para validar los datos. Un lugar en el que puede hacerlo es en el conjunto de datos. El conjunto de datos proporciona algunas ventajas de validación back end, como la capacidad de validar los cambios a medida que se modifican los valores de las columnas y las filas. Para obtener más información, consulte [validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
-   En la capa de presentación, agregando validación a los formularios. Para obtener más información, consulte [validación de entrada de usuario en formularios Windows Forms](/dotnet/framework/winforms/user-input-validation-in-windows-forms).  
  
-   En el servidor de datos, al enviar los datos al origen de datos, por ejemplo la base de datos, y dejar que éste los acepte o los rechace. Si trabaja con una base de datos que incluye funciones sofisticadas para validar datos y proporcionar información sobre errores, puede ser un planteamiento práctico, porque los datos se pueden validar sea cual sea su procedencia. Sin embargo, este enfoque no puede adaptarse a los requisitos de validación específicos de la aplicación. Además, con el origen de datos de validar los datos puede producir numerosas acciones de ida y al origen de datos, dependiendo de cómo resuelva la aplicación la resolución de errores de validación provocados por el back-end.  
  
    > [!IMPORTANT]
    >  Cuando utilice comandos de datos con un <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> propiedad que se establece en <xref:System.Data.CommandType.Text>, cuidadosamente Compruebe la información que se envía desde un cliente antes de pasar a la base de datos. Usuarios con malas intenciones podrían intentar enviar (inyectar) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos. Antes de transferir proporcionados por el usuario a una base de datos, compruebe siempre que la información es válida. Es una práctica recomendada de usar siempre las consultas parametrizadas o procedimientos almacenados cuando sea posible.  
  
## <a name="transmitting-updates-to-the-data-source"></a>Transmitir actualizaciones al origen de datos  
Después de modificar un conjunto de datos, se pueden transmitir los cambios a un origen de datos. Lo más frecuente será hacerlo mediante una llamada al método `Update` del TableAdapter (o adaptador de datos). El método recorre cada registro de una tabla de datos, determina qué tipo de actualización se requiere (actualizar, insertar o eliminar), si existe, y, a continuación, se ejecuta el comando adecuado.  

 Para ilustrar cómo se realizan las actualizaciones, supongamos que la aplicación utiliza un conjunto de datos que contiene una tabla de datos único. La aplicación obtiene dos filas de la base de datos. Después de recuperarlas, la tabla de datos en memoria sería como la siguiente:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Su aplicación cambia el estado de Nancy Buchanan a "Preferred". Como resultado de este cambio, el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de esa fila cambia de <xref:System.Data.DataRowState.Unchanged> a <xref:System.Data.DataRowState.Modified>. El valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de la primera fila se mantiene como <xref:System.Data.DataRowState.Unchanged>. Ahora, la tabla de datos tiene este aspecto:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Llegados a este punto, su aplicación llama al método `Update` para transmitir el conjunto de datos a la base de datos. El método inspecciona cada fila de una en una. Para la primera fila, el método no transmite ninguna instrucción SQL a la base de datos porque esa fila no ha cambiado desde que se obtuvo de la base de datos.  
  
 Para la segunda fila, sin embargo, la `Update` método automáticamente, se invoca el comando de datos correcto y los transmite a la base de datos. La sintaxis específica de la instrucción SQL depende del dialecto de SQL que sea compatible con el almacén de datos subyacente. Con todo, cabe señalar los siguientes rasgos generales de la instrucción SQL transmitida:  
  
-   Es una instrucción UPDATE. El adaptador sabe cómo utilizar una instrucción UPDATE, porque el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> es <xref:System.Data.DataRowState.Modified>.  
  
-   La instrucción SQL transmitida incluye una cláusula WHERE que indica que el destino de la instrucción UPDATE es la fila donde `CustomerID = 'c400'`. Esta parte de la instrucción SELECT distingue la fila de destino de las demás porque `CustomerID` es la clave principal de la tabla de destino. La información de la cláusula WHERE se deriva de la versión original del registro (`DataRowVersion.Original`), en caso de que hayan cambiado los valores necesarios para identificar la fila.  
  
-   Incluye la cláusula SET para establecer los nuevos valores de las columnas modificadas.  
  
    > [!NOTE]
    >  Si la propiedad `UpdateCommand` del TableAdapter se ha establecido en el nombre de un procedimiento almacenado, el adaptador no construye una instrucción SQL. En su lugar, invoca al procedimiento almacenado pasando los parámetros correspondientes.  
  
## <a name="passing-parameters"></a>Pasar parámetros  
 Normalmente, se usan parámetros para pasar los valores para los registros que se van a actualizar en la base de datos.  Cuando el TableAdapter `Update` método ejecuta una instrucción UPDATE, necesita rellenar los valores de parámetro. Dichos valores los obtiene de la colección `Parameters` del comando de datos correspondiente, en este caso, el objeto `UpdateCommand` de TableAdapter.  
  
 Si ha utilizado las herramientas de Visual Studio para generar un adaptador de datos, la `UpdateCommand` objeto contiene una colección de parámetros que corresponden a cada marcador de posición de parámetro en la instrucción.  
  
 La propiedad <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> de cada parámetro señala a una columna en la tabla de datos. Por ejemplo, la propiedad `SourceColumn` para `au_id` y los parámetros `Original_au_id` están establecidos en la columna de la tabla de datos que contenga el identificador del autor. Cuando el adaptador `Update` método se ejecuta, lee el autor de la columna de identificador del registro que se está actualizando y rellena los valores de la instrucción.  
  
 En una instrucción UPDATE, debe especificar los valores nuevos (los que se escribirán en el registro), así como los valores antiguos (para que el registro puede encontrarse en la base de datos). Por tanto, hay dos parámetros para cada valor: uno para la cláusula SET y otro diferente para la cláusula WHERE. Ambos parámetros leen los datos del registro que se está actualizando, pero obtienen versiones diferentes del valor de columna basándose en el parámetro <xref:System.Data.SqlClient.SqlParameter.SourceVersion> propiedad. El parámetro de la cláusula SET obtiene la versión actual y el parámetro de la cláusula WHERE obtiene la versión original.  
  
> [!NOTE]
>  También puede establecer los valores de la colección `Parameters` en el código; en ese caso, sería necesario hacerlo en un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging> del adaptador de datos.  
  
## <a name="see-also"></a>Vea también
[Herramientas de conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
[Crear y configurar los TableAdapters](create-and-configure-tableadapters.md)  
[Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
[Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[Validar datos](validate-data-in-datasets.md)   
[Guardar datos](../data-tools/saving-data.md)