---
title: Usar procedimientos almacenados en LINQ to SQL para actualizar datos
description: Use procedimientos almacenados en el LINQ to SQL Object Relational Designer (Object Relational Designer) para realizar actualizaciones, inserciones y eliminaciones de datos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f0b7ab161a252e1d3a89ef856325963bddffdc56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866858"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Procedimiento para asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)

Los procedimientos almacenados se pueden agregar a **Object Relational Designer** y ejecutar como métodos de <xref:System.Data.Linq.DataContext> normales. También se pueden usar para invalidar el comportamiento predeterminado en tiempo de ejecución LINQ to SQL que realiza inserciones, actualizaciones y eliminaciones cuando se guardan los cambios de las clases de entidad en una base de datos (por ejemplo, al llamar al <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).

> [!NOTE]
> Si el procedimiento almacenado devuelve valores que se deben devolver al cliente (por ejemplo, los valores calculados en el procedimiento almacenado), cree parámetros de salida en los procedimientos almacenados. Si no puede usar parámetros de salida, escriba una implementación de método parcial en lugar de confiar en las invalidaciones generadas por Object Relational Designer. Los miembros asignados a los valores generados por la base de datos deben establecerse en valores adecuados después de que se ejecuten correctamente las operaciones de INSERCIÓN o ACTUALIZACIÓN. Para obtener más información, consulte [responsabilidades del Desarrollador en invalidar el comportamiento predeterminado](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL controla automáticamente los valores generados por la base de datos para las columnas IDENTITY (incremento automático), ROWGUIDCOL (GUID generado por la base de datos) y timestamp. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por la base de datos, debe establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> en **true** y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> en uno de los siguientes: [AutoSync. Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync. alinserte](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>)o [AutoSync. ALUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurar el comportamiento de actualización de una clase de entidad

De forma predeterminada, la lógica para actualizar una base de datos (inserciones, actualizaciones y eliminaciones) con los cambios que se realizaron en los datos de LINQ to SQL clases de entidad se proporciona mediante el tiempo de ejecución de LINQ to SQL. El motor en tiempo de ejecución crea los comandos predeterminados INSERT, UPDATE y DELETE basándose en el esquema de la tabla (información de columna y de clave principal). Cuando no se desea usar el comportamiento predeterminado, se puede configurar el comportamiento de actualización asignando procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder manipular los datos en la tabla. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Por último, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para asignar procedimientos almacenados con el fin de invalidar el comportamiento predeterminado de una clase de entidad

1. Abra el archivo de **LINQ to SQL** en el diseñador. (Haga doble clic en el archivo **.dbml** en el **Explorador de soluciones**).

2. En el **Explorador de servidores** o **Explorador de bases de datos**, expanda **Procedimientos almacenados** y busque los procedimientos almacenados que desee usar para los comandos Insertar, Actualizar y/o Eliminar de la clase de entidad.

3. Arrastre el procedimiento almacenado hasta **Object Relational Designer**.

     El procedimiento almacenado se agrega al panel de métodos como un método de <xref:System.Data.Linq.DataContext>. Para obtener más información, vea [métodos DataContext (Object](../data-tools/datacontext-methods-o-r-designer.md)Relational Designer).

4. Seleccione la clase de entidad para la que desee usar el procedimiento almacenado para realizar las actualizaciones.

5. En la ventana **Propiedades**, seleccione el comando que desee invalidar (**Insertar**, **Actualizar** o **Eliminar**).

6. Haga clic en los puntos suspensivos (...) junto a **Usar motor en tiempo de ejecución** para abrir el cuadro de diálogo **Configurar comportamiento**.

7. Seleccione **Personalizar**.

8. Seleccione el procedimiento almacenado que desee en la lista **Personalizar**.

9. Examine la lista de **Argumentos de método** y **Propiedades de clase** para comprobar que los **Argumentos de método** se asignan a las **Propiedades de clase** adecuadas. Asigne los argumentos de método originales ( `Original_<ArgumentName>` ) a las propiedades originales ( `<PropertyName> (Original)` ) para `Update` los `Delete` comandos y.

    > [!NOTE]
    > De forma predeterminada, los argumentos de método se asignan a las propiedades de clase cuando los nombres coinciden. Si los nombres de propiedad modificados ya no coinciden entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el diseñador no puede determinar la asignación correcta.

10. Haga clic en **Aceptar** o en **Aplicar**.

    > [!NOTE]
    > Puede seguir configurando el comportamiento de cada combinación de clase y comportamiento siempre que haga clic en **aplicar** después de hacer cada cambio. Si cambia la clase o el comportamiento antes de hacer clic en **aplicar**, aparece un cuadro de diálogo de advertencia que le ofrece la oportunidad de aplicar los cambios.

Para revertir a la lógica predeterminada del motor en tiempo de ejecución para las actualizaciones, haga clic en los puntos suspensivos junto a los comandos **Insertar**, **Actualizar** o **Eliminar** en la ventana **Propiedades** y después seleccione **Usar motor en tiempo de ejecución** en el cuadro de diálogo **Configurar comportamiento**.

## <a name="see-also"></a>Vea también

- [Herramientas de LINQ to SQL en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext (métodos)](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Operaciones de inserción, actualización y eliminación (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)
