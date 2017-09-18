---
title: "C&#243;mo: Crear TableAdapters | Microsoft Docs"
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
  - "crear TableAdapters"
  - "datos [Visual Studio], crear componentes de datos"
  - "datos [Visual Studio], crear adaptadores de tablas"
  - "datos [Visual Studio], TableAdapters"
  - "adaptadores de tablas, crear"
ms.assetid: 08630d69-0d6c-4e8f-b42d-2922f45f8415
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear TableAdapters
Los TableAdapters comunican la aplicación con una base de datos.  Más específicamente, un TableAdapter se conecta con una base de datos, ejecuta consultas o procedimientos almacenados, y devuelve una nueva tabla de datos rellena con los datos devueltos o rellena una <xref:System.Data.DataTable> existente con los datos devueltos.  Los TableAdapters también se utilizan para devolver los datos actualizados desde la aplicación a la base de datos.  
  
 Puede crear TableAdapters realizando una de estas acciones:  
  
-   Ejecutar el [Asistente para la configuración de TableAdapter](../Topic/TableAdapter%20Configuration%20Wizard.md) desde el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md).  
  
-   Ejecutar el [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png), seleccionando el tipo de origen de datos **Base de datos** o **Servicio Web**.  
  
-   Arrastrar objetos de base de datos desde el [Explorador de servidores](../Topic/Server%20Explorer.md) hasta el **Diseñador de Dataset**.  
  
 Para obtener una introducción a TableAdapters, vea [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Crear TableAdapters con el Asistente para la configuración de TableAdapter  
 El **Asistente para la configuración de TableAdapter** crea un TableAdapter único basado en la información que se proporciona al asistente.  
  
#### Para crear un TableAdapter con el Asistente para la configuración de TableAdapter  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arrastre un **TableAdapter** desde la ficha **DataSet** del **Cuadro de herramientas** a la superficie de diseño.  
  
     Se abrirá el **Asistente para la configuración de TableAdapter**.  
  
3.  Complete el asistente; se agregará una tabla de datos y un TableAdapter al conjunto de datos.  Para obtener más información, vea [Asistente para la configuración de TableAdapter](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
## Crear TableAdapters con el Asistente para la configuración de orígenes de datos  
 El **Asistente para la configuración de orígenes de datos** creará un TableAdapter para cada objeto de base de datos seleccionado durante el funcionamiento del asistente.  Una vez finalizado el **Asistente para la configuración de orígenes de datos**, puede ver los TableAdapters creados abriendo el conjunto de datos del **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
#### Para crear un TableAdapter con el Asistente para la configuración de orígenes de datos  
  
1.  Seleccione **Agregar nuevo origen de datos** en [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  Elija la opción **Mostrar orígenes de datos** del menú **Datos** para abrir la ventana **Orígenes de datos**.  
  
     Se abrirá el **Asistente para la configuración de orígenes de datos**.  
  
2.  Finalice el asistente, seleccionando el tipo de origen de datos de una **Base de datos** o **Servicio Web**.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md) o [Cómo: Conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Crear TableAdapters a partir de objetos de base de datos del Explorador de servidores  
 Se crea un solo TableAdapter por cada objeto de base de datos que arrastre hasta el **Diseñador de Dataset**.  
  
#### Para crear un TableAdapter a partir de los objetos de base de datos del Explorador de servidores  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arrastre un objeto de base de datos desde una conexión de datos en el [Explorador de servidores](../Topic/Server%20Explorer.md) a la superficie del **Diseñador de DataSet**.  
  
     Se agregarán una tabla de datos y un TableAdapter al conjunto de datos.  
  
## Vea también  
 [Cómo: Actualizar datos utilizando un TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)