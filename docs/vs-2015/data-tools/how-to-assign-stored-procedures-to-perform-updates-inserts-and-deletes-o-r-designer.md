---
title: Filtrar Asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 957c1fe49d222a691160eadc4b2cf08f8a20a65a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996654"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Filtrar Asignación de procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Los procedimientos almacenados se pueden agregar a Object Relational Designer y ejecutar como métodos de <xref:System.Data.Linq.DataContext> normales. También se puede usar para invalidar el valor predeterminado [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] comportamiento en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando los cambios se guardan las clases de entidad en una base de datos (por ejemplo, al llamar a la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).  
  
> [!NOTE]
>  Si el procedimiento almacenado devuelve valores que se deben devolver al cliente (por ejemplo, los valores calculados en el procedimiento almacenado), cree parámetros de salida en los procedimientos almacenados. Si no puede usar parámetros de salida, escriba una implementación de método parcial en lugar de confiar en las invalidaciones generadas por Object Relational Designer. Los miembros asignados a los valores generados por la base de datos deben establecerse en valores adecuados después de que se ejecuten correctamente las operaciones de INSERCIÓN o ACTUALIZACIÓN. Para obtener más información, consulte [responsabilidades de los desarrolladores invalidar un comportamiento predeterminado](http://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] procesa automáticamente los valores generados por la base de datos para columnas identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y columnas con marca de tiempo. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurar el comportamiento de actualización de una clase de entidad  
 De forma predeterminada, el motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] proporciona la lógica para actualizar una base de datos (inserciones, actualizaciones y eliminaciones) con los cambios realizados en los datos de las clases de entidad de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. El tiempo de ejecución crea de forma predeterminada los comandos Insert, Update y Delete que se basan en el esquema de la tabla (la columna y la información de clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización asignando procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder manipular los datos en la tabla. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Por último, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para asignar procedimientos almacenados con el fin de invalidar el comportamiento predeterminado de una clase de entidad  
  
1.  Abra el archivo de **LINQ to SQL** en el diseñador. (Haga doble clic en el archivo .dbml en **el Explorador de soluciones**.)  
  
2.  En **Explorador de servidores**/**Database Explorer**, expanda **procedimientos almacenados** y busque los procedimientos almacenados que desea usar para la inserción, actualización, o eliminación de los comandos de la clase de entidad.  
  
3.  Arrastre el procedimiento almacenado hasta Object Relational Designer.  
  
     El procedimiento almacenado se agrega al panel de métodos como un método de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Seleccione la clase de entidad para la que desee usar el procedimiento almacenado para realizar las actualizaciones.  
  
5.  En la ventana **Propiedades**, seleccione el comando que desee invalidar (**Insertar**, **Actualizar** o **Eliminar**).  
  
6.  Haga clic en los puntos suspensivos (...) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.  
  
7.  Seleccione **Personalizar**.  
  
8.  Seleccione el procedimiento almacenado que desee en la lista **Personalizar**.  
  
9. Examine la lista de **Argumentos de método** y **Propiedades de clase** para comprobar que los **Argumentos de método** se asignan a las **Propiedades de clase** adecuadas. Asigne los argumentos de método originales (Original_*Nombredeargumento*) a las propiedades originales (*PropertyName* (Original)) para los comandos Update y Delete.  
  
    > [!NOTE]
    >  De forma predeterminada, los argumentos de método se asignan a las propiedades de clase cuando los nombres coinciden. Si los nombres de propiedad modificados ya no coinciden entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el diseñador no puede determinar la asignación correcta.  
  
10. Haga clic en **Aceptar** o en **Aplicar**.  
  
    > [!NOTE]
    >  Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic **aplicar**, que proporciona una oportunidad para aplicar cualquier cambio aparecerá un cuadro de diálogo de advertencia.  
  
     Para volver a usar la lógica de tiempo de ejecución predeterminado para las actualizaciones, haga clic en el botón de puntos suspensivos situado junto a la inserción, actualización, o eliminar comandos en el **propiedades** ventana y, a continuación, seleccione **usar en tiempo de ejecución** en el  **Configurar el comportamiento de** cuadro de diálogo.  
  
## <a name="see-also"></a>Vea también  
 [LINQ to SQL Tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Tutorial: Crear clases LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Operaciones de inserción, actualización y eliminación](http://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
