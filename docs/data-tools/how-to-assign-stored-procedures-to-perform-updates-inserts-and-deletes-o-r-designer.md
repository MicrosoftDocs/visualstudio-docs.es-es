---
title: "C&#243;mo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)
Los procedimientos almacenados se pueden agregar a Object Relational Designer y ejecutar como métodos de <xref:System.Data.Linq.DataContext> normales.Se pueden usar también con el fin de invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] en tiempo de ejecución para realizar inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos \(por ejemplo, cuando se llama al método <xref:System.Data.Linq.DataContext.SubmitChanges%2A>\).  
  
> [!NOTE]
>  Si el procedimiento almacenado devuelve valores que se deben devolver al cliente \(por ejemplo, los valores calculados en el procedimiento almacenado\), cree parámetros de salida en los procedimientos almacenados.Si no puede usar parámetros de salida, escriba una implementación de método parcial en lugar de confiar en las invalidaciones generadas por Object Relational Designer.Los miembros asignados a los valores generados por la base de datos deben establecerse en valores adecuados después de que se ejecuten correctamente las operaciones de INSERCIÓN o ACTUALIZACIÓN.Para obtener más información, consulte [Responsabilidades del desarrollador en la invalidación del comportamiento predeterminado](../Topic/Responsibilities%20of%20the%20Developer%20In%20Overriding%20Default%20Behavior.md).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] procesa automáticamente los valores generados por la base de datos para columnas identidad \(incremento automático\), rowguidcol \(GUID generado por la base de datos\) y columnas con marca de tiempo.Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo.Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Configurar el comportamiento de actualización de una clase de entidad  
 De forma predeterminada, el motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] proporciona la lógica para actualizar una base de datos \(inserciones, actualizaciones y eliminaciones\) con los cambios realizados en los datos de las clases de entidad de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].El motor en tiempo de ejecución crea comandos predeterminados de inserción, actualización y eliminación basándose en el esquema de la tabla \(información de columna y de clave principal\).Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización asignando procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder manipular los datos en la tabla. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas.Por último, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para asignar procedimientos almacenados con el fin de invalidar el comportamiento predeterminado de una clase de entidad  
  
1.  Abra el archivo de **LINQ to SQL** en el diseñador.\(Haga doble clic en el archivo .dbml en el **Explorador de soluciones**.\)  
  
2.  En el **Explorador de servidores**\/**Explorador de bases de datos**, expanda **Procedimientos almacenados** y busque los procedimientos almacenados que desee usar para los comandos Insertar, Actualizar y\/o Eliminar de la clase de entidad.  
  
3.  Arrastre el procedimiento almacenado hasta Object Relational Designer.  
  
     El procedimiento almacenado se agrega al panel de métodos como un método de <xref:System.Data.Linq.DataContext>.Para obtener más información, vea [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione la clase de entidad para la que desee usar el procedimiento almacenado para realizar las actualizaciones.  
  
5.  En la ventana **Propiedades**, seleccione el comando que desee invalidar \(**Insertar**, **Actualizar** o **Eliminar**\).  
  
6.  Haga clic en los puntos suspensivos \(...\) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.  
  
7.  Seleccione **Personalizar**.  
  
8.  Seleccione el procedimiento almacenado que desee en la lista **Personalizar**.  
  
9. Examine la lista de **Argumentos de método** y **Propiedades de clase** para comprobar que los **Argumentos de método** se asignan a las **Propiedades de clase** adecuadas.Asigne los argumentos de método originales \(Original\_*ArgumentName*\) a las propiedades originales \(*PropertyName* \(Original\)\) de los comandos Actualizar y Eliminar.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignan a las propiedades de clase cuando los nombres coinciden.Si los nombres de propiedad modificados ya no coinciden entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el diseñador no puede determinar la asignación correcta.  
  
10. Haga clic en **Aceptar** o en **Aplicar**.  
  
    > [!NOTE]
    >  Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación.Si cambia la clase o el comportamiento antes de hacer clic en **Aplicar**, aparecerá un cuadro de diálogo de advertencia en el que podrá aplicar los cambios.  
  
     Para revertir a la lógica predeterminada del motor en tiempo de ejecución para las actualizaciones, haga clic en los puntos suspensivos junto a los comandos Insertar, Actualizar o Eliminar en la ventana **Propiedades** y, a continuación, seleccione **Usar motor en tiempo de ejecución** en el cuadro de diálogo **Configurar comportamiento**.  
  
## Vea también  
 [Object Relational Designer](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext \(Object Relational Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [Tutorial: Crear procedimientos almacenados de actualización para la tabla Customers de Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md)   
 [LINQ a SQL](../Topic/LINQ%20to%20SQL.md)   
 [Operaciones de actualización, inserción y eliminación](../Topic/Insert,%20Update,%20and%20Delete%20Operations.md)