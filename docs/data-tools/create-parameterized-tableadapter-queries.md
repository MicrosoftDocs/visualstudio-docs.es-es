---
title: "C&#243;mo: Crear consultas parametrizadas de TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "datos [Visual Studio], buscar datos"
  - "datos [Visual Studio], TableAdapters"
  - "consultas [Visual Studio], crear"
  - "consultas [Visual Studio], TableAdapters"
  - "TableAdapters, consultas parametrizadas"
  - "TableAdapters, buscar datos"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Crear consultas parametrizadas de TableAdapter
Una consulta parametrizada devuelve datos que cumplen las condiciones de una cláusula WHERE dentro de la consulta.  Por ejemplo, puede parametrizar una lista de clientes para mostrar solo los clientes de una determinada ciudad; para ello, agrega `WHERE City = @City` al final de la instrucción SQL que devuelve una lista de clientes.  
  
 Las consultas de TableAdapter parametrizadas se crean en el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md) o durante la creación de formularios de enlace a datos en una aplicación de Windows, con el comando **Parametrizar origen de datos** en el menú **Datos**.  El comando **Parametrizar origen de datos** también crea controles en el formulario para especificar los valores de los parámetros y ejecutar la consulta.  Para obtener más información, vea [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
> [!NOTE]
>  Para construir una consulta parametrizada, use la notación de parámetros específica de la base de datos para la que está codificando.  Por ejemplo, los orígenes de datos de Access y Oledb usan el signo de interrogación '?' para denotar los parámetros, por lo que la cláusula WHERE tendría esta apariencia: `WHERE City = ?`.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Crear una consulta de TableAdapter parametrizada  
  
#### Para crear una consulta parametrizada en el Diseñador de Dataset  
  
-   Cree un nuevo TableAdapter y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.  Para obtener más información, vea [Cómo: Crear TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     O bien  
  
-   Agregue una consulta a un TableAdapter existente, y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.  Para obtener más información, vea [Cómo: Crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### Para crear una consulta parametrizada durante el diseño de un formulario enlazado a datos  
  
1.  Seleccione en el formulario un control que ya esté enlazado a un conjunto de datos.  Para obtener más información, vea [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  En el menú **Datos**, haga clic en **Agregar consulta**.  
  
3.  Complete el cuadro de diálogo **Generador de criterios de búsqueda** y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL.  Para obtener más información, vea [Generador de criterios de búsqueda \(cuadro de diálogo\)](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Vea también  
 [TableAdapters](../Topic/TableAdapters.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Tutoriales sobre datos](../Topic/Data%20Walkthroughs.md)