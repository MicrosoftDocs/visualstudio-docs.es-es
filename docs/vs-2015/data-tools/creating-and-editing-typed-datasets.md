---
title: Crear y Editar DataSet con tipo | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0147a114dff7144116e52f6fabe72f92e0885c4f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581582"
---
# <a name="creating-and-editing-typed-datasets"></a>Crear y editar conjuntos de datos con tipo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El**Diseñador de Dataset** es un conjunto de herramientas visuales que puede usar para crear y editar conjuntos de datos y los elementos individuales que contienen.  
  
 El **Diseñador de Dataset** proporciona representaciones visuales de los objetos contenidos en conjuntos de datos con tipo. Crear y modificar [TableAdapters](../data-tools/tableadapter-overview.md), [consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, y <xref:System.Data.DataRelation>s con el **Diseñador de Dataset**.  
  
 Para abrir el **Diseñador de Dataset**, haga doble clic en un conjunto de datos en **el Explorador de soluciones**, o haga clic en un conjunto de datos en el **orígenes de datos** ventana y haga clic en **editar Conjunto de datos con el diseñador**. Para obtener más información, consulte [Cómo: abrir un conjunto de datos en el Diseñador de Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Agregar un nuevo <xref:System.Data.DataSet> de elemento con el **Agregar nuevo elemento** se abrirá el cuadro de diálogo el **Diseñador de Dataset** con un conjunto de datos vacío listo para su edición.  
  
> [!NOTE]
>  El **Diseñador de Dataset** puede usarse para ampliar la funcionalidad de un conjunto de datos. Haga doble clic en la superficie de diseño o haga clic en y elija **ver código** para crear un archivo de clase parcial, donde puede agregar código al conjunto de datos que no modificará ni eliminará el diseñador. Para obtener información sobre cómo extender la funcionalidad de un TableAdapter, vea [amplían la funcionalidad de un TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 La tabla siguiente enumeran las tareas comunes que puede realizar con el **Diseñador de Dataset**.  
  
|En|Vea|  
|--------|---------|  
|Crear un TableAdapter|[Crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Editar un TableAdapter|[Cómo: editar TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Crear una consulta de TableAdapter|[Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Editar una consulta de TableAdapter|[Cómo: Editar consultas de TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Cree un control <xref:System.Data.DataTable>|[Cómo: Crear tablas de datos](../data-tools/how-to-create-data-tables.md)|  
|Editar un control <xref:System.Data.DataTable>|[Diseñar DataTables](../data-tools/designing-datatables.md)|  
|Cree un control <xref:System.Data.DataColumn>|[Cómo: agregar columnas a un objeto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Crear una relación entre dos controles <xref:System.Data.DataTable>|[Cómo: Crear DataRelations con el Diseñador de Dataset](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Extender la funcionalidad del conjunto de datos|[Cómo: Extender la funcionalidad de un conjunto de datos](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Agregar la validación al evento <xref:System.Data.DataTable.ColumnChanging> de una tabla de datos|[Cómo: validar datos durante los cambios de columna](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Agregar la validación al evento <xref:System.Data.DataTable.RowChanging> de una tabla de datos|[Cómo: validar datos durante los cambios de fila](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Crear objetos en la superficie de diseño  
 Puede crear los conjuntos de datos agregando y editando los objetos individuales que constituyen un conjunto de datos. En la tabla siguiente proporciona una explicación de los distintos objetos en el **DataSet** ficha la **cuadro de herramientas** que se pueden arrastrar a la superficie de diseño:  
  
|Object|Descripción|  
|------------|-----------------|  
|TableAdapter|Contiene una colección de comandos de datos y una conexión de datos que se utilizan para comunicar con la base de datos subyacente y rellenar una tabla de datos. Para obtener más información, consulte [información general sobre TableAdapter](../data-tools/tableadapter-overview.md) y [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Consulta|Las consultas de TableAdapter son métodos fuertemente tipados que ejecutan instrucciones SQL y procedimientos almacenados. Al ejecutar una consulta de TableAdapter se rellenan una tabla de datos con datos o se llevan a cabo otras tareas de base de datos. Para obtener más información, consulte [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). Arrastrar una consulta a una tabla agrega la columna a una tabla, mientras que, arrastrando una consulta en un área vacía de la **Diseñador de Dataset** crea una consulta global. Para obtener más información, consulte [Cómo: agregar consultas globales a un TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Representa una colección en memoria de las filas devueltas de una base de datos.|  
|Relación (<xref:System.Data.DataRelation>) |Representa una relación primaria--secundaria entre dos objetos <xref:System.Data.DataTable>. Para obtener más información, consulte [Introducción a los objetos DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) y [Tutorial: crear una relación entre las tablas de datos](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  El **Diseñador de Dataset** se conecta a una base de datos subyacente se crea solo cuando un conjunto de datos; el diseñador no detecta automáticamente los cambios posteriores en la base de datos. Para actualizar un archivo .xsd existente, vuelva a ejecutar el **Asistente para configuración**. Si las relaciones de tabla han cambiado, quite y vuelva a agregar las tablas correspondientes a los .xsd.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] permite [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sobre los datos en un <xref:System.Data.DataSet> objeto. Para más información, vea [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear un conjunto de datos con el Diseñador de Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Tutorial: Crear un objeto TableAdapter con varias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Tutorial: Crear un DataTable en el Diseñador de Dataset](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Tutorial: Crear una relación entre tablas de datos](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Tutorial: Mostrar datos en un formulario de Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Ventana Orígenes de datos](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Herramientas de conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparar su aplicación para recibir datos](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Captura de datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Edición de datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validación de datos](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Guardar datos](../data-tools/saving-data.md)