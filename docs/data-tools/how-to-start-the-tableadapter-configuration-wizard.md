---
title: "C&#243;mo: Iniciar el Asistente para la configuraci&#243;n de TableAdapter | Microsoft Docs"
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
  - "Asistente para la configuración de TableAdapter"
  - "TableAdapters, Asistente para configuración"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Iniciar el Asistente para la configuraci&#243;n de TableAdapter
El **Asistente para configuración de TableAdapter** crea y edita adaptadores TableAdapter en conjuntos de datos fuertemente tipados.  El asistente crea TableAdapters basados en las instrucciones SQL especificadas en el asistente o en los procedimientos almacenados existentes en la base de datos.  El asistente también puede crear nuevos procedimientos almacenados en la base de datos de acuerdo con las instrucciones SQL que se especifican en el asistente.  
  
### Para iniciar el Asistente para configuración de TableAdapter para crear un nuevo TableAdapter  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
    > [!NOTE]
    >  Si no tiene un conjunto de datos en su proyecto, vea [Cómo: Crear un conjunto de datos con tipo](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Si está creando un nuevo TableAdapter, arrastre un objeto **TableAdapter** desde la pestaña **DataSet** del **Cuadro de herramientas** al **Diseñador de DataSet**.  
  
3.  En la página **Elegir la conexión de datos**, seleccione una conexión de datos de la lista de conexiones disponibles o seleccione **Nueva conexión** para crear una conexión nueva.  
  
### Para iniciar el Asistente para configuración de TableAdapter para editar un TableAdapter existente  
  
1.  Abra su conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Haga clic con el botón secundario en TableAdapter en el **Diseñador de DataSet** y elija **Configurar**.  El asistente se abre en la página **Generar las instrucciones SQL** o en la página **Enlazar comandos con procedimientos almacenados**, según cómo se configurara originalmente el TableAdapter.  
  
3.  Complete el asistente.  
  
## Vea también  
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Cómo: Ordenar y filtrar datos ADO.NET con el componente BindingSource de formularios Windows Forms](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Cómo: Crear una tabla de búsqueda con el componente BindingSource de formularios Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)