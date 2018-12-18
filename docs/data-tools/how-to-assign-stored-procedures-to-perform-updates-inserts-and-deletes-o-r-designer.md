---
title: Procedimientos almacenado de uso para realizar la actualización, inserción y eliminación en Linq to SQL Object Relational Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e88224ab-ff61-4a3a-b6b8-6f3694546cac
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7fd690997b7d7b58f8d1c1f84ea7f471d4fe496
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089781"
---
# <a name="how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-or-designer"></a>Cómo: asignar procedimientos almacenados para realizar actualizaciones, inserciones y eliminaciones (Object Relational Designer)

Los procedimientos almacenados se pueden agregar a la **Object Relational Designer** y se ejecuta como típico <xref:System.Data.Linq.DataContext> métodos. También se puede usar para invalidar el comportamiento predeterminado del LINQ to SQL en tiempo de ejecución que realiza inserciones, actualizaciones y eliminaciones cuando los cambios se guardan las clases de entidad en una base de datos (por ejemplo, al llamar a la <xref:System.Data.Linq.DataContext.SubmitChanges%2A> método).

> [!NOTE]
> Si el procedimiento almacenado devuelve valores que se deben devolver al cliente (por ejemplo, los valores calculados en el procedimiento almacenado), cree parámetros de salida en los procedimientos almacenados. Si no puede usar parámetros de salida, escriba una implementación de método parcial en lugar de confiar en las invalidaciones generadas por Object Relational Designer. Los miembros asignados a los valores generados por la base de datos deben establecerse en valores adecuados después de que se ejecuten correctamente las operaciones de INSERCIÓN o ACTUALIZACIÓN. Para obtener más información, consulte [responsabilidades de los desarrolladores invalidar un comportamiento predeterminado](/dotnet/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior).

> [!NOTE]
> LINQ to SQL controla valores base de datos generados automáticamente para la identidad (incremento automático), rowguidcol (GUID generado por la base de datos) y las columnas de marca de tiempo. Los valores generados por la base de datos de otros tipos de columna producirán inesperadamente un valor nulo. Para devolver los valores generados por base de datos, debe establecer manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> a **true** y <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> a uno de los siguientes: [AutoSync.Always](<xref:System.Data.Linq.Mapping.AutoSync.Always>), [AutoSync.OnInsert ](<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>), o [AutoSync.OnUpdate](<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>).

## <a name="configure-the-update-behavior-of-an-entity-class"></a>Configurar el comportamiento de actualización de una clase de entidad

De forma predeterminada, se proporciona la lógica para actualizar una base de datos (inserciones, actualizaciones y eliminaciones) con los cambios realizados en los datos de LINQ a las clases de entity SQL mediante LINQ to SQL en tiempo de ejecución. El tiempo de ejecución crea de forma predeterminada los comandos INSERT, UPDATE y DELETE que se basan en el esquema de la tabla (la columna y la información de clave principal). Cuando no se desea el comportamiento predeterminado, puede configurar el comportamiento de actualización asignando procedimientos almacenados concretos para realizar las inserciones, actualizaciones y eliminaciones necesarias para poder manipular los datos de la tabla. También se puede realizar esta acción cuando no se genera el comportamiento predeterminado, por ejemplo, cuando las clases de entidad se asignan a vistas. Por último, se puede invalidar el comportamiento de actualización predeterminado cuando la base de datos requiere el acceso a las tablas a través de procedimientos almacenados.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-assign-stored-procedures-to-override-the-default-behavior-of-an-entity-class"></a>Para asignar procedimientos almacenados con el fin de invalidar el comportamiento predeterminado de una clase de entidad

1.  Abra el **LINQ to SQL** archivo en el diseñador. (Haga doble clic en el **.dbml** archivo **el Explorador de soluciones**.)

2.  En **Explorador de servidores** o **Database Explorer**, expanda **procedimientos almacenados** y busque los procedimientos almacenados que desea usar para la inserción, actualización o eliminación comandos de la clase de entidad.

3.  Arrastre el procedimiento almacenado en el **Object Relational Designer**.

     El procedimiento almacenado se agrega al panel de métodos como un método de <xref:System.Data.Linq.DataContext>. Para obtener más información, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

4.  Seleccione la clase de entidad para la que desee usar el procedimiento almacenado para realizar las actualizaciones.

5.  En el **propiedades** ventana, seleccione el comando que desee invalidar (**insertar**, **actualización**, o **eliminar**).

6.  Haga clic en el botón de puntos suspensivos (...) junto a las palabras **en tiempo de ejecución Use** para abrir el **configurar comportamiento** cuadro de diálogo.

7.  Seleccione **personalizar**.

8.  Seleccione el procedimiento almacenado que desee en el **personalizar** lista.

9. Examine la lista de **argumentos de método** y **propiedades de la clase** para comprobar que la **argumentos de método** mapa correspondientes **propiedades de la clase**. Asigne los argumentos de método originales (`Original_<ArgumentName>`) a las propiedades originales (`<PropertyName> (Original)`) para el `Update` y `Delete` comandos.

    > [!NOTE]
    > De forma predeterminada, los argumentos de método se asignan a las propiedades de clase cuando los nombres coinciden. Si los nombres de propiedad modificados ya no coinciden entre la tabla y la clase de entidad, puede que tenga que seleccionar la propiedad de clase equivalente para la asignación si el diseñador no puede determinar la asignación correcta.

10. Haga clic en **Aceptar** o **aplicar**.

    > [!NOTE]
    >  Puede seguir configurar el comportamiento para cada combinación de clase y el comportamiento, siempre haga clic en **aplicar** después de realizar cada modificación. Si cambia la clase o el comportamiento antes de hacer clic **aplicar**, un cuadro de diálogo de advertencia aparece y proporciona una oportunidad para aplicar los cambios.

Para volver a usar la lógica de tiempo de ejecución predeterminado para las actualizaciones, haga clic en el botón de puntos suspensivos junto a la **insertar**, **actualización**, o **eliminar** comando en el **propiedades**  ventana y, a continuación, seleccione **usar en tiempo de ejecución** en el **configurar comportamiento** cuadro de diálogo.

## <a name="see-also"></a>Vea también

- [LINQ to SQL tools en Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [DataContext (métodos)](../data-tools/datacontext-methods-o-r-designer.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Insertar, actualizar y eliminar operaciones (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/insert-update-and-delete-operations)