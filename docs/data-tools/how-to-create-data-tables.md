---
title: "C&#243;mo: Crear tablas de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], crear tablas de datos"
  - "Diseñador de DataSet, crear tablas de datos"
  - "tablas [Visual Studio], crear"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Crear tablas de datos
Los datos se pueden almacenar en memoria en objetos <xref:System.Data.DataTable>. \(Los conjuntos de datos están formados por objetos <xref:System.Data.DataTable>.\) Normalmente, crea nuevas tablas con TableAdapters utilizando el [Asistente para la configuración de TableAdapter](../Topic/TableAdapter%20Configuration%20Wizard.md) o arrastrando objetos de base de datos desde el **Explorador de servidores** hasta el **Diseñador de Dataset**.  
  
 Asimismo las tablas de datos se crean como subproducto al crear nuevos TableAdapters en el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png), pero también se pueden crear independientemente.  Cree una tabla de datos independiente arrastrando un objeto <xref:System.Data.DataTable> desde la ficha **DataSet** del **Cuadro de herramientas** hasta el **Diseñador de DataSet**.  
  
> [!NOTE]
>  Para crear tablas de datos mediante programación, vea [Crear DataTable](../Topic/Creating%20a%20DataTable.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Creación de un DataTable con TableAdapter  
 Las tablas de datos con TableAdapters incluyen métodos que rellenan la tabla con datos y vuelven a escribir los cambios en la base de datos.  Se crea TableAdapters al ejecutar el **Asistente para la configuración de TableAdapter** o al arrastrar los objetos de la base de datos desde el **Explorador de servidores** al **Diseñador de DataSet**.  
  
#### Para crear una nueva tabla de datos con TableAdapter  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**.  Para obtener información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arrastre un **TableAdapter** desde la ficha **DataSet** del **Cuadro de herramientas** al **Diseñador de DataSet**.  
  
     Se abre el **Asistente para la configuración de TableAdapter**.  
  
3.  Complete el asistente.  Para obtener más información, vea [Asistente para la configuración de TableAdapter](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
#### Para crear una nueva tabla de datos con un TableAdapter desde el Explorador de servidores  
  
1.  Abra su conjunto de datos en el **Diseñador de origen de datos**.  
  
2.  Arrastre un objeto de la base de datos \(por ejemplo, una tabla\) desde el **Explorador de servidores** al **Diseñador de DataSet**.  
  
## Crear un DataTable independiente  
 Las tablas independientes necesitan tener la lógica `Fill` implementada para poder rellenarse con datos.  Para obtener más información sobre cómo rellenar tablas de datos independientes, vea [Llenar un DataSet desde un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
#### Para crear una nueva tabla de datos independiente  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**.  
  
2.  Arrastre una <xref:System.Data.DataTable> desde la ficha **DataSet** del **Cuadro de herramientas** hasta el **Diseñador de Dataset**.  
  
3.  Agregue columnas para definir su tabla de datos.  Para obtener más información, vea [Cómo: Agregar columnas a un DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md).  
  
## Vea también  
 <xref:System.Data.DataTable>   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validar datos](../Topic/Validating%20Data.md)