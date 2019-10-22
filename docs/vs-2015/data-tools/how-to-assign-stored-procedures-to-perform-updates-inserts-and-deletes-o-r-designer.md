---
title: 'Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2054a55f0633d5d4add51fee2e933d9f4d829fcf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609979"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedimiento para asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los procedimientos almacenados se pueden agregar a Object Relational Designer y ejecutar como métodos de <xref:System.Data.Linq.DataContext> normales. También se pueden usar para invalidar el comportamiento predeterminado de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos (por ejemplo, al llamar al método <xref:System.Data.Linq.DataContext.SubmitChanges%2A>).

> [!NOTE]
> Si el procedimiento almacenado devuelve valores que se deben devolver al cliente (por ejemplo, los valores calculados en el procedimiento almacenado), cree parámetros de salida en los procedimientos almacenados. Si no puede usar parámetros de salida, escriba una implementación de método parcial en lugar de confiar en las invalidaciones generadas por Object Relational Designer. Los miembros asignados a los valores generados por la base de datos deben establecerse en valores adecuados después de que se ejecuten correctamente las operaciones de INSERCIÓN o ACTUALIZACIÓN. Para obtener más información, consulte [responsabilidades del Desarrollador en invalidar el comportamiento predeterminado](https://msdn.microsoft.com/library/c6909ddd-e053-46a8-980c-0e12a9797be1).

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] procesa automáticamente los valores generados por la base de datos para columnas identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y columnas con marca de tiempo. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debería establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en `true`, y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en una de las siguientes opciones: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> u <xref:System.Data.Linq.Mapping.AutoSync>.

## <a name="configuring-the-update-behavior-of-an-entity-class"></a>Configurar el comportamiento de actualización de una clase de entidad
 De forma predeterminada, el motor en tiempo de ejecución [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] proporciona la lógica para actualizar una base de datos (inserciones, actualizaciones y eliminaciones) con los cambios realizados en los datos de las clases de entidad de [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]. El motor en tiempo de ejecución crea comandos de inserción, actualización y eliminación predeterminados que se basan en el esquema de la tabla (la columna y la información de clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización asignando procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder manipular los datos en la tabla. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Por último, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para asignar procedimientos almacenados con el fin de invalidar el comportamiento predeterminado de una clase de entidad

1. Abra el archivo de **LINQ to SQL** en el diseñador. (Haga doble clic en el archivo. dbml en **Explorador de soluciones**).

2. En **Explorador de servidores** /**Explorador de bases de datos**, expanda **procedimientos almacenados** y busque los procedimientos almacenados que desea utilizar para los comandos de inserción, actualización y/o eliminación de la clase de entidad.

3. Arrastre el procedimiento almacenado hasta Object Relational Designer.

     El procedimiento almacenado se agrega al panel de métodos como un método de <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

4. Seleccione la clase de entidad para la que desee usar el procedimiento almacenado para realizar las actualizaciones.

5. En la ventana **Propiedades**, seleccione el comando que desee invalidar (**Insertar**, **Actualizar** o **Eliminar**).

6. Haga clic en los puntos suspensivos (...) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.

7. Seleccione **Personalizar**.

8. Seleccione el procedimiento almacenado que desee en la lista **Personalizar**.

9. Examine la lista de **Argumentos de método** y **Propiedades de clase** para comprobar que los **Argumentos de método** se asignan a las **Propiedades de clase** adecuadas. Asigne los argumentos de método originales (Original_*ArgumentName*) a las propiedades originales (*PropertyName* (original)) para los comandos Update y DELETE.

    > [!NOTE]
    > De forma predeterminada, los argumentos de método se asignan a las propiedades de clase cuando los nombres coinciden. Si los nombres de propiedad modificados ya no coinciden entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el diseñador no puede determinar la asignación correcta.

10. Haga clic en **Aceptar** o en **Aplicar**.

    > [!NOTE]
    > Puede continuar configurando las combinaciones de clase y comportamiento haciendo clic en **Aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic en **aplicar**, aparecerá un cuadro de diálogo de advertencia que le proporcionará la oportunidad de aplicar los cambios.

     Para revertir al uso de la lógica de tiempo de ejecución predeterminada para las actualizaciones, haga clic en los puntos suspensivos junto al comando Insertar, actualizar o eliminar en la ventana **propiedades** y, a continuación, seleccione **usar Runtime** en el cuadro de diálogo **configurar comportamiento** .

## <a name="see-also"></a>Vea también
 [LINQ to SQL herramientas en](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [los métodos DataContext](../data-tools/datacontext-methods-o-r-designer.md) de Visual Studio (Object Relational Designer) [Tutorial: crear clases LINQ to SQL (object relational Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [operaciones de inserción, actualización y eliminación](https://msdn.microsoft.com/library/26a43a4f-83c9-4732-806d-bb23aad0ff6b)
