---
title: "Guardar los datos en conjuntos de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], guardar"
  - "validación de datos, conjuntos de datos"
  - "conjuntos de datos [Visual Basic], acerca de los conjuntos de datos"
  - "conjuntos de datos [Visual Basic], restricciones"
  - "conjuntos de datos [Visual Basic], combinar"
  - "conjuntos de datos [Visual Basic], validar datos"
  - "versión de fila"
  - "guardar datos, acerca de guardar datos"
  - "TableAdapters"
  - "actualizaciones, restricciones en conjuntos de datos"
  - "actualizar conjuntos de datos, restricciones"
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 27
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Guardar los datos en conjuntos de datos
Guardar datos es el proceso de conservación de los datos modificados en una aplicación en el almacén inicial de datos originales, normalmente una base de datos relacional como SQL Server.  
  
 Debido a que un conjunto de datos es en realidad una caché \(una copia en memoria\) de datos, el proceso de escribir información en el origen de datos original es independiente del proceso de modificar los datos del conjunto de datos.  Puede devolver los datos actualizados a la base de datos llamando a uno de los métodos `Update` de un TableAdapter, o bien, llamando a uno de los métodos DBDirect del TableAdapter.  
  
 Para obtener más información sobre cómo devolver los cambios de un conjunto de datos a la base de datos, vea [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) y [Cómo: Guardar cambios de un conjunto de datos en una base de datos](../data-tools/how-to-save-dataset-changes-to-a-database.md).  
  
 Visual Studio ofrece un componente `TableAdapterManager` que sirve de ayuda en el proceso de guardar datos en tablas relacionadas.  Este componente garantiza que el proceso para guardar datos se realiza en el orden correcto basado en las restricciones FOREIGN KEY definidas en la base de datos.  Para obtener más información, vea [Información general sobre la actualización jerárquica](../Topic/Hierarchical%20Update%20Overview.md).  
  
 Para obtener información sobre cómo modificar datos en el conjunto de datos, vea [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md).  
  
## Actualizaciones en dos fases  
 La actualización de un origen de datos mediante un conjunto de datos es un proceso de dos pasos.  El primer paso consiste en actualizar el conjunto de datos con información nueva \(registros nuevos, modificados o eliminados\).  Si su aplicación sólo trabaja con el conjunto de datos, por ejemplo, si después de actualizar el conjunto de datos lo envía a otra aplicación que realizará un posterior procesamiento del mismo, habrá terminado con la actualización.  
  
> [!NOTE]
>  En los formularios Windows Forms, la arquitectura de enlace a datos se ocupa de enviar los cambios desde los controles enlazados al conjunto de datos, sin que sea necesario actualizar explícitamente el conjunto de datos con código propio.  Para obtener más información, vea [Enlace de datos en Windows Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
 Si va a actualizar un origen de datos, como una base de datos, el segundo paso consiste en enviar los cambios desde el conjunto de datos hasta el origen de datos original.  En otras palabras, en la actualización del conjunto de datos no se escriben los cambios en el origen de datos subyacente, sino que el segundo paso debe realizarse explícitamente.  Para ello, se llama al método Update del mismo TableAdapter \(o adaptador de datos\) que se utilizó para llenar el conjunto de datos, aunque también se pueden utilizar adaptadores diferentes, por ejemplo, para mover los datos de un origen de datos a otro o para actualizar múltiples orígenes de datos.  
  
 ![Actualizaciones de conjunto de datos de Visual Basic](../data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Proceso de actualización en dos fases y rol de DataRowVersion en una actualización correcta  
  
 Estructuralmente, un conjunto de datos hace que los datos estén disponibles como conjuntos de colecciones.  Los conjuntos de datos contienen colecciones de tablas.  Las tablas contienen colecciones de filas.  Las tablas se exponen como una colección del objeto <xref:System.Data.DataSet> y los registros están disponible en la colección <xref:System.Data.DataTable.Rows%2A> de objetos <xref:System.Data.DataTable>.  Se pueden modificar los datos de un conjunto de datos con sólo manipular estas colecciones mediante los métodos base de la colección, pero, si tiene previsto actualizar un origen de datos subyacente, debe utilizar los métodos que han sido diseñados específicamente para la modificación de conjuntos de datos.  
  
 Por ejemplo, para quitar un registro de una tabla de datos, podría llamar al [método RemoveAt](https://msdn.microsoft.com/en-us/library/system.data.datarowcollection.removeat.aspx) de la colección <xref:System.Data.DataTable.Rows%2A> de la tabla, con lo que el registro quedaría físicamente eliminado del conjunto de datos.  Si sólo utiliza el conjunto de datos como almacén de datos estructurado y no debe transmitir la información sobre los cambios a otra aplicación, manipular las colecciones de este modo es aceptable para actualizar un conjunto de datos.  
  
 No obstante, si tiene pensado enviar los cambios a un origen de datos o a otra aplicación, necesita mantener la información de los cambios, es decir, los metadatos, sobre cada actualización.  Más adelante, cuando envíe los cambios al origen de datos o a la aplicación, el proceso tendrá la información necesaria para buscar y actualizar los registros correspondientes.  Por ejemplo, si elimina un registro del conjunto de datos, la información sobre el registro eliminado se debe mantener en el conjunto de datos.  De esa manera, cuando se llama al comando `DeleteCommand` del TableAdapter, hay suficiente información de historial para localizar el recurso original en el origen de datos y poder eliminarlo.  Para obtener más información, vea "Mantener la información sobre los cambios" a continuación.  
  
## Combinar conjuntos de datos  
 El contenido de un conjunto de datos se puede actualizar mediante *combinación*, es decir, copiando el contenido de un conjunto de datos \(denominado conjunto de datos de *origen*\) en el conjunto de datos que realiza la llamada \(denominado conjunto de datos de *destino*\).  Cuando se combinan conjuntos de datos, los registros nuevos del conjunto de datos de origen se agregan al conjunto de datos de destino.  Asimismo, las columnas adicionales del conjunto de datos de origen se agregan al conjunto de datos de destino.  Combinar conjuntos de datos resulta especialmente útil cuando tenga un conjunto de datos local y obtenga un segundo registro de datos desde otra aplicación o desde un componente como un servicio Web XML.  También es útil cuando es necesario integrar datos incluidos en varios conjuntos de datos.  
  
 Al combinar conjuntos de datos, también se puede pasar un argumento booleano opcional \(`preserveChanges`\) que indique al método <xref:System.Data.DataSet.Merge%2A> si debe conservar las modificaciones existentes del conjunto de datos de destino.  Debido a que los conjuntos de datos mantienen varias versiones de los registros, es importante recordar que se está combinado más de una versión de los registros.  En la tabla siguiente se muestra un registro en dos conjuntos de datos que se combinarán:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James Wilson|James C.  Wilson|  
|Actual|Jim Wilson|James C.  Wilson|  
  
 Al llamar al método <xref:System.Data.DataSet.Merge%2A> de la tabla anterior con `preserveChanges=false targetDataset.Merge(sourceDataset)`, se obtiene el siguiente resultado:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James C.  Wilson|James C.  Wilson|  
|Actual|James C.  Wilson|James C.  Wilson|  
  
 Al llamar al método <xref:System.Data.DataSet.Merge%2A> con `preserveChanges = true targetDataset.Merge(sourceDataset, true)`, se obtiene el siguiente resultado:  
  
|DataRowVersion|Conjunto de datos de destino|Conjunto de datos de origen|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James C.  Wilson|James C.  Wilson|  
|Actual|Jim Wilson|James C.  Wilson|  
  
> [!CAUTION]
>  En el escenario de `preserveChanges = true`, si se llama al método <xref:System.Data.DataSet.RejectChanges%2A> en un registro del conjunto de datos de destino, éste volverá a tomar los datos originales del conjunto de datos *de origen*.  Esto significa que, si intenta actualizar el origen de datos original con el conjunto de datos de destino, puede que no se pueda encontrar la fila original que se debe actualizar.  Sin embargo, puede evitar que se produzca una infracción de simultaneidad rellenando otro conjunto de datos con los registros actualizados del origen de datos y después realizar una combinación para evitar que ocurra una infracción de simultaneidad. \(Una infracción de simultaneidad se produce cuando otro usuario modifica un registro del origen de datos después de que se ha rellenado el conjunto de datos.\)  
  
## Restricciones de actualización  
 Para realizar cambios en una fila de datos existente, se agregan o actualizan datos en cada columna.  Si el conjunto de datos contiene restricciones \(como claves externas o restricciones que no aceptan valores NULL\), es posible que, mientras se actualiza un registro, después de haber terminado de actualizar una columna pero antes de pasar a la siguiente, el registro pueda encontrarse temporalmente en un estado de error.  
  
 Para impedir que se produzcan infracciones de restricciones prematuras, puede suspender temporalmente las restricciones de actualización.  Esta suspensión tiene dos fines:  
  
-   Impide que se genere un error cuando, después de actualizar una columna, desea pasar a la siguiente.  
  
-   Evita que se provoquen determinados eventos de actualización \(eventos que suelen utilizarse para la validación\).  
  
 Una vez finalizada una actualización, se puede volver a habilitar la comprobación de restricciones, con lo que también se vuelven a habilitar e iniciar los eventos de actualización.  
  
> [!NOTE]
>  En los formularios Windows Forms, la arquitectura de enlace a datos integrada en la cuadrícula de datos suspende la comprobación de restricciones hasta que el foco sale de una fila, y no es necesario llamar explícitamente a los métodos <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> o <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Las restricciones se deshabilitan automáticamente cuando se invoca el método <xref:System.Data.DataSet.Merge%2A> en un conjunto de datos.  Cuando la combinación finaliza, si el conjunto de datos tiene restricciones que no se pueden habilitar, se produce una <xref:System.Data.ConstraintException>.  En esta situación, la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> se establece en `false` y todas las infracciones de las restricciones se deben resolver antes de restablecer la propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> a `true`.  
  
 Una vez finalizada una actualización, se puede volver a habilitar la comprobación de restricciones, con lo que también se vuelven a habilitar e iniciar los eventos de actualización.  
  
 Para obtener más información sobre la suspensión de eventos, vea [Cómo: Desactivar restricciones al llenar un conjunto de datos](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## Errores de actualización de conjuntos de datos  
 Cuando se actualiza un registro de un conjunto de datos, existe la posibilidad de que se produzca un error.  Por ejemplo, es posible que, accidentalmente, escriba datos en una columna de un tipo de datos incorrecto, demasiado larga o que tenga algún otro problema de integridad.  Además, puede haber comprobaciones de validación específicas de una aplicación que generen errores personalizados durante cualquier fase de un evento de actualización.  Para obtener más información, vea [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
## Mantener la información sobre los cambios  
 La información sobre los cambios de un conjunto de datos se mantiene de dos formas: marcando la fila que indica si ha cambiado \(<xref:System.Data.DataRow.RowState%2A>\) y guardando varias copias de un registro \(<xref:System.Data.DataRowVersion>\).  Con esta información, los procesos pueden determinar qué ha cambiado en el conjunto de datos y pueden enviar las actualizaciones correspondientes al origen de datos.  
  
### Propiedad RowState  
 La propiedad <xref:System.Data.DataRow.RowState%2A> de un objeto <xref:System.Data.DataRow> es un valor que proporciona información sobre el estado de una fila de datos determinada.  
  
 En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowState>:  
  
|Valor de DataRowState|Descripción|  
|---------------------------|-----------------|  
|<xref:System.Data.DataRowState>|La fila se ha agregado como elemento a <xref:System.Data.DataRowCollection>. \(Una fila con este estado no tiene una versión original correspondiente, ya que no existía cuando se llamó al último método <xref:System.Data.DataRow.AcceptChanges%2A>\).|  
|<xref:System.Data.DataRowState>|La fila se eliminó utilizando el método <xref:System.Data.DataRow.Delete%2A> de un objeto <xref:System.Data.DataRow>.|  
|<xref:System.Data.DataRowState>|La fila se ha creado pero no forma parte de ninguna <xref:System.Data.DataRowCollection>.  Un objeto <xref:System.Data.DataRow> se encuentra en este estado inmediatamente después de ser creado y antes de que se agregue a una colección, o si se ha quitado de una colección.|  
|<xref:System.Data.DataRowState>|Un valor de columna de la fila se ha modificado de alguna forma.|  
|<xref:System.Data.DataRowState>|La fila no ha cambiado desde la última vez que se llamó a <xref:System.Data.DataRow.AcceptChanges%2A>.|  
  
### Enumeración DataRowVersion  
 Los conjuntos de datos mantienen varias versiones de los registros.  La enumeración <xref:System.Data.DataRowVersion> de un objeto <xref:System.Data.DataRow> es un valor que se puede utilizar para devolver una versión específica de un objeto <xref:System.Data.DataRow>.  
  
 En la tabla siguiente se detallan los posibles valores de la enumeración <xref:System.Data.DataRowVersion>:  
  
|Valor de DataRowVersion|Descripción|  
|-----------------------------|-----------------|  
|<xref:System.Data.DataRowVersion>|La versión actual de un registro contiene todas las modificaciones realizadas en el mismo desde la última vez que se llamó a <xref:System.Data.DataRow.AcceptChanges%2A>.  Si la fila se ha eliminado, no existe una versión actual.|  
|<xref:System.Data.DataRowVersion>|Es el valor predeterminado de un registro, tal como se define en el esquema del conjunto de datos o en el origen de datos.|  
|<xref:System.Data.DataRowVersion>|La versión original de un registro es una copia del registro tal como se encontraba la última vez que se confirmaron cambios en el conjunto de datos.  En términos prácticos, suele ser la versión de un registro leído de un origen de datos.|  
|<xref:System.Data.DataRowVersion>|Es la versión propuesta de un registro que está disponible temporalmente, mientras está en curso una actualización, es decir, el intervalo que transcurre desde que se llama al método <xref:System.Data.DataRow.BeginEdit%2A> hasta que se llama al método <xref:System.Data.DataRow.EndEdit%2A>.  Normalmente, se obtiene acceso a la versión propuesta de un registro en un controlador de un evento tal como <xref:System.Data.DataTable.RowChanging>.  Al invocar al método <xref:System.Data.DataRow.CancelEdit%2A>, se anulan los cambios y se elimina la versión propuesta de la fila de datos.|  
  
 Las versiones original y actual son de utilidad cuando se transmite la información de actualización a un origen de datos.  Normalmente, cuando envía una actualización al origen de datos, la nueva información de la base de datos está en la versión actual de un registro.  Para buscar el registro que actualizar se utiliza información de la versión original.  Por ejemplo, si se modifica la clave principal de un registro, se necesita algún medio de encontrar el registro correspondiente en el origen de datos para actualizar los cambios.  Si no existiese una versión original, lo más probable es que el registro se agregase al final del origen de datos, con lo que se obtendría no sólo un registro adicional no deseado, sino que, además, sería inexacto y obsoleto.  Ambas versiones se utilizan también en el control de simultaneidad; se puede comparar la versión original con un registro del origen de datos para determinar si dicho registro ha cambiado desde que se cargó en el conjunto de datos.  
  
 La versión propuesta es de utilidad cuando se necesita realizar una validación antes de confirmar los cambios en el conjunto de datos.  
  
 Incluso aunque los registros hayan cambiado, no siempre hay versiones originales o actuales de esa fila.  Cuando se inserta una fila nueva en la tabla, no hay versión original, sólo una versión actual.  Lo mismo sucede si se elimina una fila mediante una llamada al método `Delete` de la tabla: hay una versión original, pero no hay versión actual.  
  
 Para comprobar si existe una versión específica de un registro, haga una consulta al método <xref:System.Data.DataRow.HasVersion%2A> de una fila de datos.  Para obtener acceso a cualquiera de las versiones de un registro, pase un valor de la enumeración <xref:System.Data.DataRowVersion> como argumento opcional cuando solicite el valor de una columna.  
  
## Obtener los registros modificados  
 Normalmente, no se actualizan todos los registros de un conjunto de datos.  Por ejemplo, un usuario puede estar trabajando con un control <xref:System.Windows.Forms.DataGridView> de formularios Windows Forms que muestre muchos registros,  pero puede actualizar sólo algunos, eliminar uno e insertar otro.  Los conjuntos de datos y las tablas de datos proporcionan un método \(`GetChanges`\) para devolver sólo las filas que se hayan modificado.  
  
 Es posible crear subconjuntos de registros modificados con el método `GetChanges` de cualquiera de las tablas de datos \(<xref:System.Data.DataTable.GetChanges%2A>\) o del propio conjunto de datos \(<xref:System.Data.DataSet.GetChanges%2A>\).  Si se llama al método de la tabla de datos, devuelve una copia de la tabla donde sólo se muestran los registros cambiados.  De igual forma, si llama al método en el conjunto de datos, obtiene un nuevo conjunto de datos solo con los registros modificados.  `GetChanges` solo devolverá todos los registros modificados.  Por contraste, pasando el <xref:System.Data.DataRowState> deseado como un parámetro al método `GetChanges`, puede especificar qué subconjunto de registros cambiados desea usar: registros recién agregados, registros marcados para su eliminación, registros desasociados o registros modificados.  
  
 Obtener subconjuntos de registros modificados es especialmente útil cuando se desea enviar registros a otro componente para su procesamiento.  En lugar de enviar todo el conjunto de datos, se puede reducir la sobrecarga de la comunicación con el otro componente al obtener únicamente los registros necesarios.  Para obtener más información, vea [Cómo: Recuperar filas modificadas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
## Confirmar los cambios del conjunto de datos  
 Cuando se realizan cambios en el conjunto de datos, se establece la propiedad <xref:System.Data.DataRow.RowState%2A> de las filas modificadas.  Se establecen y mantienen las versiones original y actual de los registros, y se ponen a su disposición mediante la propiedad <xref:System.Data.DataRowView.RowVersion%2A>.  Los metadatos almacenados en estas propiedades, que representan los cambios, son necesarios para enviar las actualizaciones correspondientes al origen de datos.  
  
 Si los cambios reflejan el estado actual del origen de datos, ya no es necesario mantener esta información.  Normalmente, el conjunto de datos y su origen están sincronizados en dos ocasiones:  
  
-   Inmediatamente después de haber cargado información en el conjunto de datos; por ejemplo, cuando lee datos del origen.  
  
-   Después de enviar los cambios del conjunto de datos al origen de datos \(pero no antes, porque se perdería la información sobre los cambios que es necesaria para enviar las modificaciones a la base de datos\).  
  
 Para confirmar los cambios pendientes en el conjunto de datos, puede llamar al método <xref:System.Data.DataSet.AcceptChanges%2A>.  Normalmente, en una aplicación se llama al método <xref:System.Data.DataSet.AcceptChanges%2A> en las siguientes ocasiones:  
  
-   Después de haber cargado el conjunto de datos.  Si se carga un conjunto de datos mediante una llamada al método `Fill` del TableAdapter, este adaptador confirma los cambios automáticamente.  Sin embargo, si carga un conjunto de datos mediante la combinación de otro conjunto de datos, los cambios se deben confirmar manualmente.  
  
    > [!NOTE]
    >  Puede impedir que el adaptador confirme los cambios automáticamente al llamar al método `Fill` estableciendo la propiedad `AcceptChangesDuringFill` del adaptador en `false`.  Si se establece en `false`, el <xref:System.Data.DataRow.RowState%2A> de cada fila insertada durante la operación de rellenar se establece en <xref:System.Data.DataRowState>.  
  
-   Después de enviar los cambios del conjunto de datos a otro proceso, como un servicio Web XML.  
  
    > [!CAUTION]
    >  Si confirma el cambio de este modo, se borra la información sobre cambios existente.  No confirme los cambios hasta que haya realizado todas las operaciones en las que su aplicación necesite saber qué cambios se han hecho en el conjunto de datos.  
  
 Este método realiza las funciones siguientes:  
  
-   Escribe la versión <xref:System.Data.DataRowVersion> de un registro en la versión <xref:System.Data.DataRowVersion>, con lo que se sobrescribe la versión original.  
  
-   Quita cualquier fila cuya propiedad <xref:System.Data.DataRow.RowState%2A> esté establecida en <xref:System.Data.DataRowState>.  
  
-   Establece la propiedad <xref:System.Data.DataRow.RowState%2A> de un registro en <xref:System.Data.DataRowState>.  
  
 El método <xref:System.Data.DataSet.AcceptChanges%2A> está disponible en tres niveles.  Puede llamarlo sobre un objeto <xref:System.Data.DataRow>, con lo que se confirman los cambios realizados sólo para esa fila.  También puede llamarlo en un objeto <xref:System.Data.DataTable> para confirmar todas las filas de una tabla, o en el objeto <xref:System.Data.DataSet> para confirmar todos los cambios pendientes en todos los registros de todas las tablas del conjunto de datos.  
  
 En la tabla siguiente se describen los cambios que se confirman en función del objeto en el que se llame el método.  
  
|Método|Resultado|  
|------------|---------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman sólo en una fila específica|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de una tabla específica|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|Los cambios se confirman en todas las filas de todas las tablas del conjunto de datos|  
  
> [!NOTE]
>  Si carga un conjunto de datos mediante una llamada al método `Fill` de un TableAdapter, es necesario aceptar los cambios explícitamente; de manera predeterminada, el método `Fill` llama al método `AcceptChanges` cuando ha terminado de rellenar la tabla de datos.  
  
 Un método relacionado, `RejectChanges`, deshace el efecto de los cambios copiando la versión <xref:System.Data.DataRowVersion> de vuelta a la versión <xref:System.Data.DataRowVersion> de los registros y estableciendo el <xref:System.Data.DataRow.RowState%2A> de cada registro de nuevo en <xref:System.Data.DataRowState>.  
  
## Validación de datos  
 Para comprobar que los datos de una aplicación satisfacen los requisitos de los procesos a los que se pasan, normalmente se agrega validación.  Ello puede significar tener que comprobar si es correcta la entrada de un usuario en un formulario, validar los datos enviados a la aplicación por otra aplicación, o incluso comprobar que la información calculada dentro de un componente satisface las restricciones del origen de datos y los requisitos de la aplicación.  
  
 Los datos se pueden validar de distintas maneras:  
  
-   En la capa de empresa, agregando código a la aplicación para validar los datos.  Un lugar en el que puede hacerlo es en el conjunto de datos.  El conjunto de datos proporciona algunas ventajas de validación back end, como la capacidad de validar los cambios a medida que se modifican los valores de las columnas y las filas.  Para obtener más información, vea [Validar los datos en conjuntos de datos](../data-tools/validate-data-in-datasets.md).  
  
-   En la capa de presentación, agregando validación a los formularios.  Para obtener más información, vea [User Input Validation in Windows Forms](../Topic/User%20Input%20Validation%20in%20Windows%20Forms.md).  
  
-   En el servidor de datos, al enviar los datos al origen de datos, por ejemplo la base de datos, y dejar que éste los acepte o los rechace.  Si trabaja con una base de datos que incluye funciones sofisticadas para validar datos y proporcionar información sobre errores, puede ser un planteamiento práctico, porque los datos se pueden validar sea cual sea su procedencia.  Sin embargo, puede no adaptarse a los requisitos de validación específicos de la aplicación.  Además, si los datos se validan en el origen de datos, puede que éste tenga que realizar numerosas acciones de ida y vuelta, dependiendo de cómo resuelva la aplicación los errores de validación provocados por el servidor.  
  
    > [!IMPORTANT]
    >  Cuando utilice comandos de datos con una propiedad <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> cuyo valor esté establecido en <xref:System.Data.CommandType>, compruebe minuciosamente la información enviada desde el cliente antes de pasarla a la base de datos.  Usuarios con malas intenciones podrían intentar enviar \(inyectar\) instrucciones de SQL modificadas o adicionales con el fin de obtener acceso no autorizado o dañar la base de datos.  Antes de transferir la entrada del usuario a una base de datos, debe comprobar siempre que la información es válida; un procedimiento recomendado es utilizar siempre que sea posible consultas parametrizadas o procedimientos almacenados.  Para obtener más información, vea [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
 Después de modificar un conjunto de datos, se pueden transmitir los cambios a un origen de datos.  Lo más frecuente será hacerlo mediante una llamada al método `Update` del TableAdapter \(o adaptador de datos\).  El método recorre cada uno de los registros de una tabla de datos, determina qué tipo de actualización se requiere \(actualizar, insertar o eliminar\), si se requiere alguna, y después ejecuta el comando correspondiente.  
  
## Cómo se transmite una actualización al origen de datos  
 Para ilustrar cómo se realizan las actualizaciones, supongamos que su aplicación utiliza un conjunto de datos que contiene una sola tabla de datos.  La aplicación obtiene dos filas de la base de datos.  Después de recuperarlas, la tabla de datos en memoria sería como la siguiente:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Su aplicación cambia el estado de Nancy Buchanan a "Preferred". Como resultado de este cambio, el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de esa fila cambia de <xref:System.Data.DataRowState> a <xref:System.Data.DataRowState>.  El valor de la propiedad <xref:System.Data.DataRow.RowState%2A> de la primera fila se mantiene como <xref:System.Data.DataRowState>.  Ahora, la tabla de datos tiene este aspecto:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Llegados a este punto, su aplicación llama al método `Update` para transmitir el conjunto de datos a la base de datos.  El método inspecciona cada fila de una en una.  Para la primera fila, el método no transmite ninguna instrucción SQL a la base de datos, porque esa fila no ha cambiado desde la primera vez que se obtuvo de la base de datos.  
  
 Sin embargo, para la segunda fila, el método `Update` invoca automáticamente el comando de datos correspondiente y lo transmite a la base de datos.  La sintaxis específica de la instrucción SQL depende del dialecto de SQL que admita el almacén de datos subyacente.  Con todo, cabe señalar los siguientes rasgos generales de la instrucción SQL transmitida:  
  
-   Es una instrucción UPDATE.  El adaptador sabe cómo utilizar una instrucción UPDATE, porque el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> es <xref:System.Data.DataRowState>.  
  
-   Incluye una cláusula WHERE que indica que el destino de la instrucción UPDATE es la fila donde `CustomerID = 'c400'`.  Esta parte de la instrucción SELECT distingue la fila de destino de las demás porque `CustomerID` es la clave principal de la tabla de destino.  La información de la cláusula WHERE se deriva de la versión original del registro \(`DataRowVersion.Original`\), en caso de que hayan cambiado valores necesarios para identificar la fila.  
  
-   Incluye la cláusula SET para establecer los nuevos valores de las columnas modificadas.  
  
    > [!NOTE]
    >  Si la propiedad `UpdateCommand` del TableAdapter se ha establecido en el nombre de un procedimiento almacenado, el adaptador no construye una instrucción SQL.  En su lugar, invoca al procedimiento almacenado pasando los parámetros correspondientes.  
  
## Pasar parámetros  
 Normalmente, los valores de los registros que se deben actualizar en la base de datos se pasan mediante parámetros.  Cuando el método `Update` del TableAdapter ejecuta una instrucción UPDATE, necesita rellenar los valores de los parámetros.  Dichos valores los obtiene de la colección `Parameters` del comando de datos correspondiente, en este caso, el objeto `UpdateCommand` de TableAdapter.  
  
 Si ha utilizado Visual Studio Tools para generar un adaptador de datos, el objeto `UpdateCommand` contendrá una colección de parámetros que se corresponden con cada marcador de posición de parámetro de la instrucción.  
  
 La propiedad <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> de cada parámetro señala a una columna en la tabla de datos.  Por ejemplo, la propiedad `SourceColumn` para `au_id` y los parámetros `Original_au_id` están establecidos en la columna de la tabla de datos que contenga el identificador del autor.  Cuando el método `Update` del adaptador se ejecuta, lee la columna del identificador del autor del registro que se está actualizado y rellena los valores de la instrucción.  
  
 En una instrucción UPDATE, debe especificar los valores nuevos \(los que se escribirán en el registro\) y los valores antiguos \(para poder encontrar el registro que se va a actualizar en la base de datos\).  Por tanto, hay dos parámetros para cada valor: uno para la cláusula SET y otro diferente para la cláusula WHERE.  Ambos parámetros leen los datos del registro que se actualiza, pero obtienen versiones diferentes del valor de la columna basándose en la [propiedad SqlParameter.SourceVersion](https://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlparameter.sourceversion.aspx) del parámetro.  El parámetro de la cláusula SET obtiene la versión actual y el parámetro de la cláusula WHERE obtiene la versión original.  
  
> [!NOTE]
>  También puede establecer los valores de la colección `Parameters` en el código; en ese caso, sería necesario hacerlo en un controlador de eventos para el evento <xref:System.Data.DataTable.RowChanging> del adaptador de datos.  
  
## Actualizar tablas relacionadas  
 Si su conjunto de datos contiene múltiples tablas, debe actualizarlas una a una, llamando al método `Update` de cada adaptador de datos por separado.  Si las tablas guardan una relación de principal\-secundario, es probable que tenga que enviar las actualizaciones a la base de datos en un orden concreto.  Un escenario común es agregar registros principales y registros secundarios relacionados a un conjunto de datos; por ejemplo, un nuevo registro de cliente y uno o más registros de pedidos relacionados.  Si la propia base de datos impone reglas de integridad relacional, se producirán errores si envía a la base de datos los nuevos registros secundarios antes de crear el registro principal.  
  
 Por otra parte, si elimina registros relacionados en el conjunto de datos, en general, deberá enviar las actualizaciones en el orden inverso: primero la tabla secundaria y después la tabla principal.  De lo contrario, es posible que la base de datos genere un error, porque las reglas de integridad referencial impedirán que elimine un registro principal mientras todavía existan registros secundarios relacionados.  
  
 Como regla general, para enviar las actualizaciones de tablas relacionadas, siga este orden:  
  
1.  Tabla secundaria: eliminar registros.  
  
2.  Tabla principal: insertar, actualizar y eliminar registros.  
  
3.  Tabla secundaria: insertar y actualizar registros.  
  
4.  Para obtener más información, vea [Tutorial: Guardar datos en una base de datos \(Varias tablas\)](../data-tools/save-data-to-a-database-multiple-tables.md).  
  
## Control de simultaneidad  
 Debido a que los conjuntos de datos están desconectados del origen de datos, no se mantienen bloqueos sobre los registros en este último.  Por tanto, si desea actualizar la base de datos y si es importante para su aplicación mantener el control de simultaneidad, debe reconciliar los registros del conjunto de datos con los de la base de datos.  Por ejemplo, puede encontrarse con que los registros de la base de datos han cambiado desde la última vez que se llenó el conjunto de datos.  Si es así, debe ejecutar lógica específica de la aplicación para especificar qué debería suceder con el registro de la base de datos o con el registro modificado del conjunto de datos.  
  
## Vea también  
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)