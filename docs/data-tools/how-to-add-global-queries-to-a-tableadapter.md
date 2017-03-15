---
title: "C&#243;mo: Agregar consultas globales a un conjunto de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "datos [Visual Studio], TableAdapters"
  - "conjuntos de datos [Visual Basic], funciones globales"
  - "conjuntos de datos [Visual Basic], funciones escalares"
  - "funciones globales, conjuntos de datos"
  - "consultas [Visual Studio], TableAdapters"
  - "funciones escalares, conjuntos de datos"
  - "consultas TableAdapter"
  - "Asistente para la configuración de consultas de TableAdapter"
  - "TableAdapters, consultas globales"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Agregar consultas globales a un conjunto de datos
Las *consultas globales* son consultas SQL que devuelven un valor único \(escalar\) o ningún valor.  Normalmente, las funciones globales realizan operaciones de base de datos, como inserciones, actualizaciones, eliminaciones, y agregan información, por ejemplo, devuelven el recuento de clientes contenidos en una tabla o el costo total de todos los elementos de un pedido específico.  
  
 Las consultas globales se agregan ejecutando el **Asistente para la configuración de consultas de TableAdapter** desde el **Diseñador de Dataset**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para agregar una consulta global a un conjunto de datos  
  
1.  Abra un conjunto de datos en el **Diseñador de Dataset**.  Para obtener más información, vea [Cómo: Abrir un objeto Dataset en el Diseñador de Dataset](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arrastre una **Consulta** desde la ficha **DataSet** del **Cuadro de herramientas** a un área vacía del **Diseñador de DataSet**.  
  
     Se abre [Asistente para la configuración de consultas de TableAdapter](../data-tools/editing-tableadapters.md).  
  
3.  Elija una conexión para que la utilice la consulta.  Puede elegirla en la lista o crear una nueva.  Si crea una nueva, tendrá la opción de guardarla en el archivo de configuración de la aplicación.  Para obtener más información, vea [Cómo: Guardar y editar cadenas de conexión](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
4.  Elija si utilizar instrucciones SQL o procedimientos almacenados.  
  
5.  Elija el procedimiento almacenado que utilizar o, en la página **Elija un tipo de consulta** del asistente, elija el tipo de consulta que desea realizar y haga clic en **Siguiente**.  
  
6.  Proporcione una consulta que realice la tarea deseada, por ejemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Al arrastrar una consulta directamente al **Diseñador de DataSet**, se crea un método que devolverá sólo un valor escalar \(único\).  A pesar de que la consulta o procedimiento almacenado que selecciona puede devolver más de un valor único, el método creado por el asistente devolverá sólo un valor único.  Por ejemplo, la consulta podría devolver la primera columna de la primera fila de los datos devueltos.  
  
7.  Finalice el asistente; la consulta se agrega al **Diseñador de DataSet**.  Para obtener información sobre cómo ejecutar la consulta, vea [Cómo: Ejecutar consultas de TableAdapter](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md).  
  
## Vea también  
 [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Cómo: Explorar datos con el control BindingNavigator de formularios Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Tutorial: Mostrar datos en Windows Forms](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)