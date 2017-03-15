---
title: "Enlace de objetos en Visual Studio | Microsoft Docs"
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
  - "enlace, a objetos"
  - "datos [Visual Studio], enlazar a objetos"
  - "datos [Visual Studio], enlace de objetos"
  - "enlace de objetos"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enlace de objetos en Visual Studio
Visual Studio proporciona herramientas en tiempo de diseño para trabajar con objetos personalizados \(en oposición a otros conjuntos de datos como entidades, conjuntos de datos y servicios\) como origen de datos de la aplicación.  
  
## Requisitos de los objetos  
 El único requisito para que los objetos personalizados trabajen con las herramientas de diseño de datos de Visual Studio es que deben contar al menos con una propiedad pública.  
  
 Generalmente, los objetos personalizados no exigen interfaces, constructores o atributos específicos que actúen como un origen de datos para una aplicación.  Sin embargo, si desea arrastrar el objeto de la ventana **Orígenes de datos** a una superficie de diseño para crear un control enlazado a datos, y si el objeto implementa la interfaz <xref:System.ComponentModel.IListSource> o <xref:System.ComponentModel.ITypedList>, el objeto debe tener un constructor predeterminado \(es decir, un constructor sin parámetros\).  De lo contrario, Visual Studio no puede crear instancias del objeto de origen de datos y mostrará un error al arrastrar el elemento a la superficie de diseño.  
  
## Ejemplos de utilizar objetos personalizados como orígenes de datos  
 Si bien existen innumerables formas de implementar la lógica de aplicación cuando se trabaja con objetos como origen de datos, existen algunas operaciones estándar que pueden simplificarse si se utilizan los objetos [TableAdapter](../data-tools/tableadapter-overview.md) generados por Visual Studio.  Esta página explica cómo implementar estos procesos estándar mediante TableAdapters; no está pensada como una guía para crear los objetos personalizados.  Por ejemplo, generalmente realizará las operaciones estándar siguientes sin tener en cuenta la implementación concreta de sus objetos ni la lógica de la aplicación:  
  
-   Cargar datos en objetos \(normalmente de una base de datos\).  
  
-   Crear una colección con tipo de objetos.  
  
-   Agregar y quitar objetos de una colección.  
  
-   Mostrar los datos de objeto a los usuarios en un formulario.  
  
-   Cambiar\/editar los datos de un objeto.  
  
-   Guardar datos de objetos en la base de datos.  
  
> [!NOTE]
>  Para entender mejor los ejemplos de esta página y proporcionar un contexto, sugerimos que realice el siguiente tutorial: [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  Este tutorial crea los objetos que se utilizan en esta página de Ayuda.  
  
### Cargar datos en objetos  
 Para este ejemplo, carga los datos en los objetos utilizando TableAdapters.  De forma predeterminada, los TableAdapters se crean con dos tipos de métodos que obtienen datos de una base de datos y rellenan tablas de datos.  
  
-   El método `TableAdapter.Fill` rellena una tabla de datos existente con los datos devueltos.  
  
-   El método `TableAdapter.GetData` devuelve una nueva tabla de datos rellenada con datos.  
  
 La forma más sencilla de cargar datos en los objetos personalizados consiste en llamar al método `TableAdapter.GetData`, recorrer la colección de filas de la tabla de datos devuelta y rellenar cada objeto con los valores de cada fila.  Puede crear un método `GetData` que devuelva una tabla de datos rellenada para cualquier consulta agregada a un TableAdapter.  
  
> [!NOTE]
>  Visual Studio denomina las consultas de TableAdapter `Fill` y `GetData` de forma predeterminada, pero estos nombres se pueden cambiar a cualquier nombre de método válido.  
  
 El ejemplo siguiente muestra cómo recorrer las filas de una tabla de datos y rellenar un objeto con datos:  
  
 Para obtener un ejemplo de código completo, vea [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### Crear una colección con tipo de objetos  
 Puede crear clases de colección para los objetos o utilizar las colecciones con tipo que proporciona automáticamente [BindingSource \(Componente\)](../Topic/BindingSource%20Component.md).  
  
 Cuando cree una clase de colección personalizada para los objetos, sugerimos que herede de <xref:System.ComponentModel.BindingList%601>.  Esta clase genérica proporciona funcionalidad para administrar la colección así como la posibilidad de iniciar eventos que envían notificaciones a la infraestructura de enlace de datos en formularios Windows Forms.  
  
 La colección generada automáticamente en <xref:System.Windows.Forms.BindingSource> utiliza <xref:System.ComponentModel.BindingList%601> para su colección con tipo.  Si la aplicación no requiere función adicional, puede mantener su colección dentro de <xref:System.Windows.Forms.BindingSource>.  Para obtener más información, vea la propiedad <xref:System.Windows.Forms.BindingSource.List%2A> de la clase <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Si la colección precisa funcionalidad que no proporciona la implementación base de <xref:System.ComponentModel.BindingList%601>, debe crear una colección personalizada para agregar a la clase cuando lo necesite.  
  
 En el código siguiente se muestra cómo crear la clase para una colección de objetos `Order` fuertemente tipada:  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### Agregar objetos a una colección  
 Para agregar objetos a una colección llama al método `Add` de su clase de colección personalizada o de <xref:System.Windows.Forms.BindingSource>.  
  
 Para obtener un ejemplo de cómo agregar a una colección utilizando <xref:System.Windows.Forms.BindingSource>, vea el método `LoadCustomers` en [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 Para obtener un ejemplo de cómo agregar objetos a una colección personalizada, vea el método `LoadOrders`, en [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  El método `Add` se proporciona automáticamente para la colección personalizada cuando hereda de <xref:System.ComponentModel.BindingList%601>.  
  
 En el código siguiente se muestra cómo agregar objetos a la colección con tipo en <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 En el código siguiente se muestra cómo agregar objetos a una colección con tipo que hereda de <xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  En este ejemplo, la colección `Orders` es una propiedad del objeto `Customer`.  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### Quitar objetos de una colección  
 Para quitar objetos de una colección llama al método `Remove` o al método `RemoveAt` de su clase de colección personalizada o de <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  Los métodos `Remove` y `RemoveAt` se proporcionan automáticamente para la colección personalizada cuando hereda de <xref:System.ComponentModel.BindingList%601>.  
  
 En el código siguiente se muestra cómo buscar y quitar objetos de la colección con tipo en <xref:System.Windows.Forms.BindingSource> con el método <xref:System.Windows.Forms.BindingSource.RemoveAt%2A>:  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### Mostrar datos de objetos a los usuarios  
 Para mostrar los datos de los objetos a los usuarios, crea un origen de datos de objeto con [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png) y, a continuación, arrastra el objeto completo o propiedades individuales al formulario desde la ventana **Orígenes de datos**.  
  
 Para obtener más información sobre cómo crear un origen de datos de objeto, vea [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Para obtener más información sobre cómo mostrar datos de objetos en formularios Windows Forms, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
### Modificar los datos de objetos  
 Para editar datos en objetos personalizados enlazados con datos a controles de formularios Windows Forms, edite los datos en el control enlazado \(o directamente en las propiedades del objeto\).  La arquitectura de enlace de datos actualizará los datos en el objeto.  
  
 Si la aplicación requiere efectuar el seguimiento de los cambios y revertir los cambios propuestos, debe implementar esta funcionalidad en el modelo de objetos.  Para obtener ejemplos de cómo las tablas de datos mantienen el seguimiento de los cambios propuestos, vea <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A> y <xref:System.Data.DataTable.GetChanges%2A>.  
  
### Guardar datos de objetos en la base de datos  
 Los datos se vuelven a guardar en la base de datos pasando los valores del objeto a los métodos DBDirect de los TableAdapter.  
  
 Visual Studio crea métodos DBDirect que se pueden ejecutar directamente en la base de datos.  Estos métodos no requieren objetos DataSet ni DataTable.  
  
|Método DBDirect de TableAdapter|Descripción|  
|-------------------------------------|-----------------|  
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos, permitiendo pasar valores de columna individuales como parámetros de método.|  
|`TableAdapter.Update`|Actualiza registros existentes en una base de datos.  El método Update toma los valores originales y nuevos de la columna como parámetros de método.  Los valores originales se utilizan para buscar el registro original y los nuevos valores se utilizan para actualizar ese registro.<br /><br /> El método `TableAdapter.Update` también se utiliza para reconciliar los cambios de un conjunto de datos en la base de datos, tomando <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> o una matriz de <xref:System.Data.DataRow>s como parámetros del método.|  
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos basándose en los valores de columna originales pasados como parámetros de método.|  
  
 Para guardar datos de una colección de objetos, recorra la colección \(por ejemplo, utilizando un bucle for\-next\) y envíe los valores de cada objeto a la base de datos con los métodos DBDirect del TableAdapter.  
  
 El ejemplo siguiente muestra cómo utilizar el método DBDirect `TableAdapter.Insert` para agregar directamente un nuevo cliente en la base de datos:  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## Vea también  
 [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Cómo: Guardar los datos de un objeto en una base de datos](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Cómo: Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Tutorial: Guardar datos con los métodos DBDirect de un TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Guardar datos](../data-tools/saving-data.md)