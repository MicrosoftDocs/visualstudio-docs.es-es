---
title: "Trabajar con los conjuntos de datos en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "caché [Visual Studio], conjuntos de datos"
  - "distinción de mayúsculas y minúsculas, conjuntos de datos"
  - "registros secundarios"
  - "restricciones [Visual Basic], conjuntos de datos"
  - "registro actual del conjunto de datos"
  - "adaptadores de datos, llenar conjuntos de datos"
  - "almacenamiento de datos en caché, conjuntos de datos"
  - "relaciones entre datos"
  - "bases de datos [Visual Basic], actualizar"
  - "DataRelation (objeto), conjuntos de datos"
  - "DataSet (clase)"
  - "DataSet (clase), acerca de los conjuntos de datos"
  - "conjuntos de datos [Visual Basic]"
  - "conjuntos de datos [Visual Basic], propiedades extendidas"
  - "conjuntos de datos [Visual Basic], rellenar"
  - "conjuntos de datos [Visual Basic], msprop"
  - "conjuntos de datos [Visual Basic], namespace"
  - "conjuntos de datos [Visual Basic], llenar"
  - "conjuntos de datos [Visual Basic], relaciones"
  - "propiedades extendidas, en conjuntos de datos con tipo"
  - "claves externas, conjuntos de datos"
  - "tablas principal-detalle, conjuntos de datos"
  - "msprop"
  - "registros primarios de conjuntos de datos"
  - "tablas relacionadas"
  - "tablas relacionadas, conjuntos de datos"
  - "relaciones, conjuntos de datos"
  - "esquemas [Visual Basic], conjuntos de datos"
  - "conjuntos de datos con tipo"
  - "conjuntos de datos con tipo, comparación con conjuntos de datos sin tipo"
  - "restricciones unique (conjuntos de datos)"
  - "conjuntos de datos sin tipo"
  - "conjuntos de datos sin tipo, comparación con conjuntos de datos con tipo"
  - "actualizar conjuntos de datos, acerca de las actualizaciones de conjuntos de datos"
  - "XML [Visual Basic], conjuntos de datos"
  - "esquemas XML, acerca de los conjuntos de datos y esquemas XML"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trabajar con los conjuntos de datos en Visual Studio
Los conjuntos de datos son objetos que contienen tablas de datos en las que se pueden almacenar temporalmente los datos para su uso en la aplicación.  Si su aplicación requiere trabajar con datos, puede cargarlos en un conjunto de datos, que proporciona a su aplicación una caché de memoria local para los datos que utiliza.  Puede trabajar con los datos incluidos en un conjunto de datos aun cuando su aplicación se desconecte de la base de datos.  El conjunto de datos mantiene información sobre los cambios efectuados en sus datos, de manera que se pueden controlar las actualizaciones y devolverlas a la base de datos cuando se restablezca la conexión con ella.  
  
 En los siguientes temas se proporcionan detalles para trabajar con conjuntos de datos en Visual Studio:  
  
|Tema|Descripción|  
|----------|-----------------|  
|[Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)|Describe las herramientas en tiempo de diseño para crear conjuntos de datos.|  
|[Cómo: Crear un conjunto de datos con tipo](../data-tools/create-and-configure-datasets-in-visual-studio.md)|Explica cómo crear un conjunto de datos con tipo mediante las herramientas de diseño de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Cómo: Extender la funcionalidad de un conjunto de datos](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|Proporciona los pasos para crear una clase parcial del conjunto de datos en los que puede agregar código además del código generado por el diseñador.|  
|[Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)|Explica cómo abrir los conjuntos de datos del **Explorador de soluciones** y la ventana **Orígenes de datos**.|  
|[Cómo: Editar un conjunto de datos](../Topic/How%20to:%20Edit%20a%20Dataset.md)|Explica cómo modificar objetos en un conjunto de datos mediante el **Diseñador de DataSet**.|  
|[Tutorial: Crear un conjunto de datos con el Diseñador de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)|Proporciona las instrucciones paso a paso para crear un conjunto de datos con tipo sin la ayuda del **Asistente para la configuración de orígenes de datos**.|  
|[Diseñar DataTables](../data-tools/designing-datatables.md)|Proporciona vínculos a temas que explican cómo crear y modificar tablas con herramientas en tiempo de diseño.|  
|[Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)|Proporciona vínculos a temas que explican cómo crear y modificar relaciones de datos con herramientas en tiempo de diseño.|  
|[TableAdapters](../Topic/TableAdapters.md)|Proporciona vínculos a temas que explican la forma de crear y editar TableAdapters con herramientas en tiempo de diseño.|  
|[Trabajar con conjuntos de datos en aplicaciones de n capas](../data-tools/work-with-datasets-in-n-tier-applications.md)|Explica qué son las aplicaciones de n niveles, qué características están disponibles para trabajado con conjuntos de datos en aplicaciones de n niveles.|  
  
 La estructura de un <xref:System.Data.DataSet> es similar a la de una base de datos relacional; expone un modelo jerárquico de tablas, filas, columnas, restricciones y relaciones.  
  
 Los conjuntos de datos pueden tener tipo o no.  .\(Para obtener más información, consulte la siguiente sección titulada "Conjuntos de datos con tipo y sin tipo"\). Los conjuntos de datos con tipo derivan su esquema \(tabla y estructura de columnas\) de archivos .xsd y es más fácil programar con ellos.  En sus aplicaciones puede utilizar cualquiera de estos tipos de conjuntos de datos.  Sin embargo, Visual Studio proporciona más herramientas para los conjuntos de datos con tipo, que hacen que la programación con ellos sea más sencilla y tenga menor probabilidad de error.  
  
 Los conjuntos de datos con tipo se crean ejecutando el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) o agregando un elemento de **Conjunto de datos** a través del comando **Agregar nuevo elemento** del menú **Proyecto**.  Para obtener más información, vea [Cómo: Crear un conjunto de datos con tipo](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
 Los conjuntos de datos sin tipo se crean arrastrando elementos del **Conjunto de datos** desde el **Cuadro de herramientas** hasta el [Windows Forms Designer](http://msdn.microsoft.com/es-es/3c3d61f8-f36c-4d41-b9c3-398376fabb15) o el [Component Designer](../Topic/Component%20Designer.md).  
  
 Después de crear los conjuntos de datos, edítelos en el [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md).  
  
 Para crear y trabajar con conjuntos de datos con y sin tipo, use las partes siguientes de los espacios de nombres de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 ![Espacio de nombres del conjunto de datos de datos del sistema](../data-tools/media/vbdatasetnamspace.png "vbDataSetNamspace")  
Los conjuntos de datos están en el espacio de nombres System.Data  
  
 Los objetos de un conjunto de datos se exponen mediante construcciones de programación estándar, tales como propiedades y colecciones.  Por ejemplo:  
  
-   La clase <xref:System.Data.DataSet> incluye la colección <xref:System.Data.DataTableCollection> de tablas de datos y la colección <xref:System.Data.DataRelationCollection> de los objetos <xref:System.Data.DataRelation>.  
  
-   La clase <xref:System.Data.DataTable> incluye la colección <xref:System.Data.DataRowCollection> de filas de la tabla, la colección <xref:System.Data.DataColumnCollection> de columnas de datos, y las colecciones <xref:System.Data.DataTable.ChildRelations%2A> y <xref:System.Data.DataTable.ParentRelations%2A> de relaciones de datos.  
  
-   La clase <xref:System.Data.DataRow> incluye la propiedad <xref:System.Data.DataRow.RowState%2A>, cuyos valores indican si la fila se ha cambiado, y de qué modo, desde que la tabla de datos se cargó por primera vez desde la base de datos.  Los valores posibles para la propiedad <xref:System.Data.DataRow.RowState%2A> incluyen <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState>.  
  
## Rellenar los conjuntos de datos con datos  
 De forma predeterminada, un conjunto de datos no contiene datos reales.  Rellenar un conjunto de datos significa, en realidad, cargar datos en los objetos <xref:System.Data.DataTable> individuales que constituyen el conjunto de datos.  Rellene las tablas de datos ejecutando consultas de TableAdapter o comandos del adaptador de datos \(por ejemplo, <xref:System.Data.SqlClient.SqlDataAdapter>\).  Cuando se llena un conjunto de datos, se producen diversos eventos, se comprueban las restricciones, etc.  Para obtener más información sobre la carga de datos en un conjunto de datos, vea [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md).  
  
 El código para rellenar un conjunto de datos se agrega automáticamente al controlador de eventos de carga del formulario cuando se arrastran elementos desde la [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) hasta un formulario de su aplicación para Windows.  Para obtener más información, realice el siguiente tutorial: [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
 Un ejemplo de cómo rellenar un conjunto de datos de un TableAdapter:  
  
 [!code-cs[VbRaddataDatasets#1](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataDatasets#1](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_1.vb)]  
  
 Para llenar un conjunto de datos se pueden seguir varios procedimientos:  
  
-   Si creó el conjunto de datos utilizando las herramientas en tiempo de diseño como uno de los asistentes para datos, llame al método `Fill` de un TableAdapter.  \(Los TableAdapters se crean con un método `Fill` predeterminado, pero se le permite cambiar el nombre, por lo que el nombre real del método puede ser diferente.\) Para obtener más información, vea la sección "Rellenar un conjunto de datos utilizando un TableAdapter" de [Cómo: Llenar un conjunto de datos con datos](../data-tools/how-to-fill-a-dataset-with-data.md).  
  
-   Llamar al método `Fill` de un objeto <xref:System.Data.Common.DataAdapter>.  Para obtener más información, vea [Llenar un DataSet desde un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
-   Llenar manualmente las tablas del conjunto de datos; para ello, cree objetos <xref:System.Data.DataRow> y agréguelos a la colección <xref:System.Data.DataRowCollection> de la tabla.  \(Esto sólo se puede hacer en tiempo de ejecución; no se puede establecer la colección <xref:System.Data.DataRowCollection> en tiempo de diseño.\) Para obtener más información, vea [Agregar datos a DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).  
  
-   Leer un documento o una secuencia XML para el conjunto de datos.  Para obtener más información, vea el método <xref:System.Data.DataSet.ReadXml%2A>.  Para obtener un ejemplo, vea [Tutorial: Leer datos XML e introducirlos en un conjunto de datos](../data-tools/read-xml-data-into-a-dataset.md).  
  
-   Combinar \(copiar\) el contenido de un conjunto de datos con otro.  Este escenario puede ser útil si la aplicación obtiene conjuntos de datos de diferentes orígenes \(por ejemplo, diferentes servicios Web XML\), pero necesita consolidarlos en un solo conjunto de datos.  Para obtener más información, vea [Combinar contenido de DataSet](../Topic/Merging%20DataSet%20Contents.md).  
  
-   Combinar \(copiar\) el contenido de un <xref:System.Data.DataTable> con otro.  
  
## Guardar los datos de un conjunto de datos en una base de datos  
 Cuando se realizan cambios en los registros de un conjunto de datos, es necesario escribir los cambios en la base de datos.  Para escribir los cambios de un conjunto de datos en la base de datos, deberá llamar al método `Update` de TableAdapter o <xref:System.Data.Common.DataAdapter> a través del cual se comunican el conjunto de datos y su correspondiente base de datos.  
  
 Cuando se utilizan las herramientas de diseño de datos de Visual Studio, los datos se devuelven a la base de datos llamando al método Update del TableAdapter y pasando la tabla de datos que desea guardar.  Por ejemplo:  
  
 [!code-cs[VbRaddataDatasets#2](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataDatasets#2](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_2.vb)]  
  
 Para un control más preciso del proceso de actualización, llame a uno de los métodos DBDirect de TableAdapter con los que puede pasar valores individuales para cada fila de datos.  Para obtener más información, vea [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) y [Tutorial: Guardar datos con los métodos DBDirect de un TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md).  
  
 La clase <xref:System.Data.DataRow>, que solía manipular registros individuales, incluye la propiedad <xref:System.Data.DataRow.RowState%2A>, cuyos valores indican si la fila se ha cambiado, y de qué modo, desde que la tabla de datos se cargó por primera vez desde la base de datos.  Los valores posibles incluyen <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> y <xref:System.Data.DataRowState>.  Los métodos `Update` de TableAdapter y <xref:System.Data.Common.DataAdapter> examina el valor de la propiedad <xref:System.Data.DataRow.RowState%2A> para determinar qué registros deben escribirse en la base de datos y qué comando específico de la base de datos \(`InsertCommand`, `UpdateCommand` y `DeleteCommand`\) debe invocarse.  
  
 Para obtener más información sobre la actualización de datos, vea [Guardar datos](../data-tools/saving-data.md).  
  
## Navegar por registros en los conjuntos de datos  
 Dado que un conjunto de datos es un contenedor de datos totalmente desconectado, los conjuntos de datos \(a diferencia de los conjuntos de registros ADO\) no admiten el concepto de registro actual.  Por el contrario, todos los registros del conjunto de datos están disponibles en cualquier momento.  
  
 Dado que no existe un registro actual, no hay ninguna propiedad específica que apunte al registro actual, ni existen métodos y propiedades para desplazarse de un registro a otro \(vea la nota siguiente\).  Puede tener acceso a tablas individuales del conjunto de datos como objetos; cada tabla expone una colección de filas.  Puede tratarla como cualquier colección, tener acceso a las filas por medio del índice de la colección o utilizar instrucciones específicas de la colección en el lenguaje de programación.  
  
 Por ejemplo, puede obtener la fila cuarta de la tabla `Customers` con el código siguiente:  
  
 [!code-cs[VbRaddataDatasets#3](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataDatasets#3](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_3.vb)]  
  
> [!NOTE]
>  Si está enlazando los controles de un formulario a un conjunto de datos, puede utilizar el componente <xref:System.Windows.Forms.BindingNavigator> para simplificar el acceso a los registros individuales.  Para obtener más información, vea [Cómo: Desplazarse por datos en formularios Windows Forms](../Topic/How%20to:%20Navigate%20Data%20in%20Windows%20Forms.md).  
  
## LINQ to DataSet  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] habilita [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sobre los datos en un objeto <xref:System.Data.DataSet>.  Para obtener más información, vea [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Conjuntos de datos y XML  
 Un conjunto de datos es una vista de datos relacional que se puede representar en XML.  Esta relación entre los conjuntos de datos y XML permite aprovechar las siguientes características de los conjuntos de datos:  
  
-   La estructura de un conjunto de datos, sus tablas, columnas, relaciones y restricciones, puede definirse en un esquema XML.  Los conjuntos de datos pueden leer y escribir esquemas que almacenan información estructurada por medio de los métodos <xref:System.Data.DataSet.ReadXmlSchema%2A> y <xref:System.Data.DataSet.WriteXmlSchema%2A>.  Si no hay ningún esquema disponible, el conjunto de datos puede deducir uno \(mediante el método <xref:System.Data.DataSet.InferXmlSchema%2A>\) a partir de los datos de un documento XML estructurado de forma relacional.  Para obtener más información sobre los esquemas XML, vea [Compilar esquemas XML](../Topic/Building%20XML%20Schemas.md).  
  
-   Puede generar una clase de conjunto de datos que incorpora información del esquema para definir su estructura de datos.  Esto se conoce como un conjunto de datos *con tipo*.  Para obtener información sobre cómo crear un conjunto de datos con tipo, vea [Cómo: Crear un conjunto de datos con tipo](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Puede leer un documento o secuencia XML para un conjunto de datos por medio del método <xref:System.Data.DataSet.ReadXml%2A> del conjunto de datos y escribir un conjunto de datos como XML por medio del método <xref:System.Data.DataSet.WriteXml%2A> del conjunto de datos.  Debido a que XML es un formato estándar para el intercambio de datos entre diferentes aplicaciones, se puede cargar un conjunto de datos con información en formato XML enviada por otra aplicación.  De forma similar, se pueden escribir los datos en forma de documento o secuencia XML para compartirlos con otras aplicaciones o almacenarlos simplemente en un formato estándar.  
  
-   Puede crear una vista XML \(un objeto <xref:System.Xml.XmlDataDocument>\) del contenido de un conjunto de datos o tabla de datos y, a continuación, ver y manipular los datos mediante métodos relacionales \(a través del conjunto de datos\) o métodos XML.  Las dos vistas se sincronizan automáticamente cuando sufren modificaciones.  
  
## Conjuntos de datos con tipo y sin tipo  
 Un conjunto de datos con tipo es un conjunto de datos que se deriva primero de la clase <xref:System.Data.DataSet> de base y, a continuación, utiliza información del **Diseñador de Dataset**, que se almacena en un archivo .xsd, para generar una nueva clase de conjunto de datos fuertemente tipada.  La información del esquema \(tablas, columnas, etc.\) se genera y compila en esta nueva clase de conjunto de datos como un conjunto de objetos y propiedades de primera clase.  Dado que un conjunto de datos con tipo hereda de la clase <xref:System.Data.DataSet> de base, la clase con tipo asume toda la funcionalidad de la clase <xref:System.Data.DataSet> y se puede utilizar con métodos que toman una instancia de una clase <xref:System.Data.DataSet> como un parámetro  
  
 Por el contrario, un conjunto de datos sin tipo no tiene el esquema integrado correspondiente.  Al igual que un conjunto de datos con tipo, un conjunto de datos sin tipo contiene tablas, columnas, etc., pero sólo se exponen como colecciones.  \(No obstante, después de crear manualmente las tablas y otros elementos de datos de un conjunto de datos sin tipo, se puede exportar la estructura del conjunto de datos en forma de esquema por medio del método <xref:System.Data.DataSet.WriteXmlSchema%2A> del conjunto de datos.\)  
  
### Comparación del acceso a datos en conjuntos de datos con tipo y sin tipo  
 La clase para un conjunto de datos con tipo tiene un modelo de objetos en el que sus propiedades asumen los nombres reales de las tablas y columnas.  Por ejemplo, si está trabajando con un conjunto de datos con tipo, puede hacer referencia a una columna utilizando código similar al siguiente:  
  
 [!code-cs[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_4.vb)]  
  
 Por el contrario, si está trabajando con un conjunto de datos sin tipo, el código equivalente es el siguiente:  
  
 [!code-cs[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/dataset-tools-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/dataset-tools-in-visual-studio_5.vb)]  
  
 El acceso con tipo no es sólo más fácil de leer, sino que es totalmente compatible con IntelliSense en el **Editor de código** de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Además de ser más cómodo para trabajar, la sintaxis para el conjunto de datos con tipo proporciona comprobación de tipos en tiempo de compilación, lo que reduce en gran medida la posibilidad de cometer errores al asignar valores a los miembros del conjunto de datos.  Si cambia el nombre de una columna en <xref:System.Data.DataSet> y, a continuación, compila su aplicación, recibirá un error de compilación.  Si hace doble clic en el error de compilación en la **Lista de tareas**, puede ir directamente a la línea o líneas de código que hace referencia al nombre de columna anterior.  El acceso a las tablas y las columnas de un conjunto de datos con tipo también es algo más rápido en tiempo de ejecución porque el acceso se determina en tiempo de compilación, no a través de colecciones en tiempo de ejecución.  
  
 Aunque el uso de conjuntos de datos con tipo tiene muchas ventajas, hay circunstancias en las que es útil utilizar un conjunto de datos sin tipo.  El escenario más evidente es aquél en el que no hay un esquema disponible para el conjunto de datos.  Esto puede ocurrir, por ejemplo, si la aplicación interacciona con un componente que devuelve un conjunto de datos, pero no se conoce previamente cuál es la estructura.  De forma similar, hay ocasiones en que se trabaja con datos que no tienen una estructura estática y previsible; en este caso, no es práctico utilizar un conjunto de datos con tipo, porque habría que volver a generar la clase del conjunto de datos con tipo después de cada cambio de la estructura de datos.  
  
 En general, hay muchas ocasiones en que se podría crear un conjunto de datos dinámicamente, sin disponer de un esquema.  En este caso, el conjunto de datos no es más que una estructura práctica para conservar la información, mientras los datos puedan representarse de forma relacional.  Al mismo tiempo, se pueden aprovechar las ventajas del conjunto de datos, por ejemplo la capacidad de serializar la información que se pasa a otro proceso o de escribir un archivo XML.  
  
## Distinguir mayúsculas de minúsculas en un conjunto de datos  
 Dentro de un conjunto de datos, los nombres de las tablas y columnas no distinguen entre mayúsculas y minúsculas de forma predeterminada; es decir, a una tabla denominada "Customers" en un conjunto de datos se puede hacer referencia también como "customers". Esto satisface las convenciones de denominación de muchas bases de datos, incluido el comportamiento predeterminado de SQL Server, donde los nombres de los elementos de datos no pueden distinguirse sólo por su grafía.  
  
> [!NOTE]
>  A diferencia de los conjuntos de datos, los documentos XML distinguen entre mayúsculas y minúsculas, de modo que los nombres de los elementos de datos definidos en los esquemas distinguen mayúsculas de minúsculas.  Por ejemplo, el protocolo de esquema permite al esquema definir una tabla denominada "Customers" y otra denominada "customers". Esto puede producir colisiones de nombre cuando un esquema que contiene elementos que sólo difieren en el uso de mayúsculas y minúsculas se utiliza para generar una clase de conjunto de datos.  
  
 Sin embargo, la capacidad de distinguir entre mayúsculas y minúsculas puede ser un factor importante para la interpretación de los datos dentro del conjunto de datos.  Por ejemplo, si filtra los datos de una tabla de un conjunto de datos, los criterios de búsqueda podrían devolver resultados diferentes dependiendo de que la comparación distinga o no entre mayúsculas y minúsculas.  Para controlar la capacidad de distinguir mayúsculas de minúsculas al filtrar, buscar y ordenar, establezca el valor de la propiedad <xref:System.Data.DataSet.CaseSensitive%2A> del conjunto de datos.  Todas las tablas del conjunto de datos heredan el valor de esta propiedad de forma predeterminada.  \(Puede reemplazar esta propiedad para cada tabla individual si establece la propiedad <xref:System.Data.DataTable.CaseSensitive%2A> de la tabla.\)  
  
## Tablas relacionadas y objetos DataRelation  
 Si tiene varias tablas en un conjunto de datos, es posible que la información de las tablas esté relacionada.  Un conjunto de datos no posee un conocimiento intrínseco de dichas relaciones; en consecuencia, para trabajar con datos de tablas relacionadas, puede crear objetos <xref:System.Data.DataRelation> que describan las relaciones existentes entre las tablas del conjunto de datos.  Para obtener más información, vea [Cómo: Obtener acceso a registros en tablas de datos relacionadas](../Topic/How%20to:%20Access%20Records%20in%20Related%20DataTables.md).  Los objetos <xref:System.Data.DataRelation> pueden utilizarse para obtener mediante programación registros secundarios relacionados con un registro primario y un registro primario a partir de un registro secundario.  Para obtener más información, vea [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md).  Si su base de datos contiene las relaciones entre dos o más tablas, las herramientas de diseño crearán automáticamente los objetos <xref:System.Data.DataRelation> para el usuario.  
  
 Por ejemplo, imagine datos de clientes y pedidos como los de la base de datos Northwind.  La tabla `Customers` podría contener registros como los siguientes:  
  
```  
CustomerID   CompanyName               City  
ALFKI        Alfreds Futterkiste       Berlin  
ANTON        Antonio Moreno Taquerias  Mexico D.F.  
AROUT        Around the Horn           London  
```  
  
 El conjunto de datos podría contener también otra tabla con información de pedidos.  La tabla `Orders` contiene un identificador de cliente como columna de clave externa.  Si se seleccionaran sólo algunas columnas de la tabla `Orders`, el aspecto podría ser el siguiente:  
  
```  
OrderId    CustomerID    OrderDate  
10692      ALFKI         10/03/1997  
10702      ALFKI         10/13/1997  
10365      ANTON         11/27/1996  
10507      ANTON         4/15/1997  
```  
  
 Dado que cada cliente puede tener más de un pedido, existe una relación uno a varios entre clientes y pedidos.  Por ejemplo, en la tabla anterior, el cliente ALFKI tiene dos pedidos.  
  
 Puede utilizar un objeto <xref:System.Data.DataRelation> para obtener registros relacionados procedentes de una tabla secundaria o primaria.  Por ejemplo, cuando trabaje con el registro que describe al cliente ANTON, puede obtener la colección de registros que describen los pedidos de este cliente.  Para obtener más información, vea <xref:System.Data.DataRow.GetChildRows%2A>.  De forma similar, al trabajar con el registro que describe el OrderId 10507, puede navegar hasta el objeto de relación para obtener el registro para su primario, ANTON.  Para obtener más información, vea <xref:System.Data.DataRow.GetParentRow%2A>.  
  
## Restricciones  
 Como sucede en la mayoría de las bases de datos, los conjuntos de datos admiten restricciones como un medio para garantizar la integridad de los datos.  Las restricciones son reglas que se aplican cuando se insertan, actualizan o eliminan filas en una tabla.  Puede definir dos tipos de restricciones:  
  
-   Una restricción *UNIQUE* que comprueba si los nuevos valores de una columna son únicos en la tabla.  
  
-   Una restricción *FOREIGN\-KEY* que define reglas sobre cómo deben actualizarse los registros secundarios relacionados cuando se actualiza o se elimina un registro de una tabla principal.  Por ejemplo, una restricción FOREIGN\-KEY comprueba que hay un registro primario antes de permitir la creación de cualquier registro secundario.  
  
 En un conjunto de datos, las restricciones se asocian a tablas individuales \(restricciones FOREIGN KEY\) o columnas \(restricción UNIQUE, que garantiza que los valores de la columna son únicos\).  Las restricciones se implementan como objetos de tipo <xref:System.Data.UniqueConstraint> o <xref:System.Data.ForeignKeyConstraint>.  A continuación se agregan a la colección <xref:System.Data.DataTable.Constraints%2A> de <xref:System.Data.DataTable>.  Una restricción UNIQUE puede especificarse alternativamente estableciendo simplemente la propiedad <xref:System.Data.DataColumn.Unique%2A> de <xref:System.Data.DataColumn> en `true`.  
  
 El propio conjunto de datos admite una propiedad <xref:System.Data.DataSet.EnforceConstraints%2A> de tipo Boolean que especifica si se exigirá o no el cumplimiento de las restricciones.  De forma predeterminada, esta propiedad está establecida en `true`.  Sin embargo, hay ocasiones en que es útil desactivar temporalmente las restricciones.  Normalmente, esto sucede cuando se modifica un registro de modo que provoca temporalmente un estado no válido.  Después de completar el cambio \(y, por tanto, de volver a un estado válido\), puede habilitar de nuevo las restricciones.  
  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], se crean restricciones de forma implícita al definir un conjunto de datos.  Al agregar una clave principal a un conjunto de datos, se crea de forma implícita una restricción UNIQUE para la columna de clave principal.  Para especificar una restricción UNIQUE para otras columnas, puede establecer su propiedad <xref:System.Data.DataColumn.Unique%2A> en `true`.  
  
 Para crear restricciones FOREIGN KEY, cree un objeto <xref:System.Data.DataRelation> en un conjunto de datos.  Además de permitir que se obtenga información mediante programación sobre los registros relacionados, un objeto <xref:System.Data.DataRelation> permite definir reglas de restricción FOREIGN KEY.  
  
## Propiedades extendidas de los conjuntos de datos  
 Las propiedades extendidas proporcionan asignaciones de nombre cuando aparecen conflictos de nomenclatura durante el proceso de compilación del conjunto de datos a partir de un archivo .xsd.  Cuando un identificador del archivo .xsd es distinto del nombre automático creado por el generador de conjuntos de datos, se agrega una propiedad extendida al conjunto de datos del espacio de nombres `msprop`.  La tabla siguiente muestra las posibles propiedades extendidas que se pueden generar:  
  
|Objeto.|Propiedad extendida|  
|-------------|-------------------------|  
|<xref:System.Data.DataSet>|msprop:Generator\_UserDSName|  
||msprop:Generator\_DataSetName|  
|<xref:System.Data.DataTable>|msprop:Generator\_UserTableName|  
||msprop:Generator\_TablePropName|  
||msprop:Generator\_TableVarName|  
||msprop:Generator\_TableClassName|  
||msprop:Generator\_RowClassName|  
||msprop:Generator\_RowEvHandlerName|  
||msprop:Generator\_RowEvArgName|  
|<xref:System.Data.DataColumn>|msprop:Generator\_UserColumnName|  
||msprop:Generator\_ColumnPropNameInTable|  
||msprop:Generator\_ColumnVarNameInTable|  
||msprop:Generator\_ColumnPropNameInRow|  
  
## Vea también  
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)