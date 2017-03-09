---
title: "C&#243;mo: Guardar los datos de un objeto en una base de datos | Microsoft Docs"
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
  - "datos [Visual Studio], guardar"
  - "acceso a datos [Visual Studio], objetos"
  - "guardar datos"
ms.assetid: efd6135a-40cf-4b0d-8f8b-41a5aaea7057
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Guardar los datos de un objeto en una base de datos
Puede guardar datos de objetos en una base de datos pasando los valores del objeto a uno de los métodos DBDirect del TableAdapter \(por ejemplo, `TableAdapter.Insert`\).  Para obtener más información, vea [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md).  
  
 Para guardar datos de una colección de objetos, recorra la colección \(por ejemplo, utilizando un bucle for\-next\) y envíe los valores de cada objeto a la base de datos con uno de los métodos DBDirect del TableAdapter.  
  
 De forma predeterminada, los métodos DBDirect se crean en un TableAdapter que se puede ejecutar directamente en la base de datos.  Estos métodos se pueden llamar directamente y no requieren objetos <xref:System.Data.DataSet> ni <xref:System.Data.DataTable> para reconciliar cambios y enviar actualizaciones a una base de datos.  
  
> [!NOTE]
>  Cuando configuran un TableAdapter, la consulta principal debe proporcionar información suficiente para los métodos DBDirect que se van a crear.  Por ejemplo, si un TableAdapter está configurado para consultar datos de una tabla que no dispone de una columna de clave principal definida, no genera métodos DBDirect.  
  
|Método DBDirect de TableAdapter|Descripción|  
|-------------------------------------|-----------------|  
|`TableAdapter.Insert`|Agrega nuevos registros a una base de datos, permitiendo pasar valores de columna individuales como parámetros de método.|  
|`TableAdapter.Update`|Actualiza registros existentes en una base de datos.  El método `Update` toma los valores originales y nuevos de la columna como parámetros de método.  Los valores originales se utilizan para buscar el registro original y los nuevos valores se utilizan para actualizar ese registro.<br /><br /> El método `TableAdapter.Update` también se utiliza para reconciliar los cambios de un conjunto de datos en la base de datos, tomando <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow> o una matriz de <xref:System.Data.DataRow>s como parámetros del método.|  
|`TableAdapter.Delete`|Elimina registros existentes de la base de datos basándose en los valores de columna originales pasados como parámetros de método.|  
  
### Para guardar nuevos registros de un objeto a una base de datos  
  
-   Cree los registros pasando los valores al método `TableAdapter.Insert`.  
  
     El ejemplo siguiente crea un nuevo registro de cliente en la tabla `Customers` pasando los valores del objeto `currentCustomer` al método `TableAdapter.Insert`.  
  
     [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_1.cs)]
     [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_1.vb)]  
  
### Para actualizar registros existentes de un objeto en una base de datos  
  
-   Modifique los registros llamando al método `TableAdapter.Update` y pasando los nuevos valores para actualizar el registro y los valores originales para localizarlo.  
  
    > [!NOTE]
    >  El objeto necesita mantener los valores originales para pasarlos al método `Update`.  Este ejemplo utiliza propiedades con un prefijo `orig` para almacenar los valores originales.  
  
     El ejemplo siguiente actualiza un registro existente de la tabla `Customers` pasando los valores nuevos y originales del objeto `Customer` al método `TableAdapter.Update`.  
  
     [!code-cs[VbRaddataSaving#24](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_2.cs)]
     [!code-vb[VbRaddataSaving#24](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_2.vb)]  
  
### Para eliminar registros existentes de una base de datos  
  
-   Elimine los registros llamando al método `TableAdapter.Delete` y pasando los valores originales para buscar el registro.  
  
    > [!NOTE]
    >  El objeto necesita mantener los valores originales para pasarlos al método `Delete`.  Este ejemplo utiliza propiedades con un prefijo `orig` para almacenar los valores originales.  
  
     El ejemplo siguiente elimina un registro de la tabla `Customers` pasando los valores originales del objeto `Customer` al método `TableAdapter.Delete`.  
  
     [!code-cs[VbRaddataSaving#25](../data-tools/codesnippet/CSharp/save-data-from-an-object-to-a-database_3.cs)]
     [!code-vb[VbRaddataSaving#25](../data-tools/codesnippet/VisualBasic/save-data-from-an-object-to-a-database_3.vb)]  
  
## Seguridad de .NET Framework  
 Debe tener permiso para realizar la operación INSERT, UPDATE o DELETE en la tabla de la base de datos.  
  
## Vea también  
 [Enlace de objetos en Visual Studio](../data-tools/bind-objects-in-visual-studio.md)   
 [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)   
 [Tutorial: Conectar a los datos en objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md)   
 [Cómo: Obtener acceso directamente a la base de datos con un TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)