---
title: Creación y configuración de conjuntos de datos
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b71d4b8ea58cbbe36e3fe48228789d4aee02af53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567797"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Crear y configurar conjuntos de datos en Visual Studio

Un conjunto de datos es crear un conjunto de objetos que almacenan datos de una base de datos en memoria y admite el seguimiento de cambios para habilitar, leer, actualizar y eliminar operaciones (CRUD) en los datos sin necesidad de estar siempre conectados a la base de datos. Los conjuntos de datos se diseñaron para simple *formularios sobre datos* aplicaciones empresariales. Para las aplicaciones nuevas, considere el uso de Entity Framework para almacenar y modelar los datos en memoria. Para trabajar con conjuntos de datos, debe tener conocimientos básicos sobre conceptos de base de datos.

Puede crear un tipo <xref:System.Data.DataSet> clase en Visual Studio en tiempo de diseño mediante el uso de la **Asistente para configuración de origen de datos**. Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [crear un objeto dataset (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Crear un nuevo conjunto de datos mediante el Asistente para configuración de orígenes de datos

1. Abra el proyecto en Visual Studio y, a continuación, elija **proyecto** > **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.

2. Elija el tipo de origen de datos a la que se va a conectar.

     ![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

3. Elija la base de datos o bases de datos que serán el origen de datos para el conjunto de datos.

     ![Seleccione la conexión de origen de datos](../data-tools/media/data-source-choose-a-connection.png)

4. Elija las tablas (o columnas individuales), procedimientos almacenados, funciones y vistas desde la base de datos que desea que se puede representar en el conjunto de datos.

     ![Selección de objetos de la base de datos](../data-tools/media/raddata-chose-objects.png)

5. Haga clic en **Finalizar**.

   El conjunto de datos aparece como un nodo en **el Explorador de soluciones**.

   ![Conjunto de datos en el Explorador de soluciones](../data-tools/media/dataset-in-solution-explorer.png)

6. Haga clic en el nodo de conjunto de datos **el Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**. Cada tabla del conjunto de datos tiene asociado un `TableAdapter` objeto, que se representa en la parte inferior. El adaptador de tabla se utiliza para rellenar el conjunto de datos y, opcionalmente, para enviar comandos a la base de datos.

   ![Diseñador de DataSet](../data-tools/media/dataset-designer.png)

7. Las líneas de relación que conecta las tablas representan las relaciones entre tablas, tal como se define en la base de datos. De forma predeterminada, restricciones foreign key en una base de datos se representan como sólo, una relación con la actualización y eliminación las reglas que se establece en none. Por lo general, es lo que desea. Sin embargo, puede hacer clic en las líneas para que aparezca el **relación** cuadro de diálogo, donde puede cambiar el comportamiento de las actualizaciones jerárquicas. Para obtener más información, consulte [relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md) y [actualización jerárquica](../data-tools/hierarchical-update.md).

     ![Cuadro de diálogo relación del conjunto de datos](../data-tools/media/raddata-relation-dialog.png)

8. Haga clic en una tabla, el adaptador de tabla o el nombre de columna en una tabla para ver sus propiedades en el **propiedades** ventana. Puede modificar algunos de los valores aquí. Sólo recuerde que va a modificar el conjunto de datos, no la base de datos de origen.

     ![Propiedades de columna del conjunto de datos](../data-tools/media/dataset-column-properties.png)

9. Puede agregar nuevas tablas o adaptadores de tabla al conjunto de datos, o agregar nuevas consultas para los adaptadores de tabla existente o especificar nuevas relaciones entre tablas arrastrando los elementos desde el **cuadro de herramientas** ficha. Esta pestaña aparece cuando el **Diseñador de DataSet** tiene el foco.

     ![Cuadro de herramientas del conjunto de datos](../data-tools/media/raddata-dataset-toolbox.png)

A continuación, puede especificar cómo rellenar el conjunto de datos con datos. Para ello, usa el **TableAdapter Configuration Wizard**. Para obtener más información, consulte [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Agregar una tabla de base de datos u otro objeto a un conjunto de datos existente

Este procedimiento muestra cómo agregar una tabla de la misma base de datos que usó para crear el conjunto de datos.

1. Haga clic en el nodo de conjunto de datos **el Explorador de soluciones** para poner el **Diseñador de DataSet** en foco.

2. Haga clic en el **orígenes de datos** ficha en el margen izquierdo de Visual Studio o tipo **orígenes de datos** en el cuadro de búsqueda.

3. Haga clic en el nodo de conjunto de datos y seleccione **Configurar origen de datos con el asistente**.

     ![Menú de contexto de origen de datos](../data-tools/media/data-source-context-menu.png)

4. Use el Asistente para especificar qué tablas adicionales, procedimientos almacenados u otros objetos de base de datos para agregar al conjunto de datos.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Agregar una tabla de datos independiente a un conjunto de datos

1. Abra su conjunto de datos en el **Diseñador de Dataset**.

2. Arrastre un <xref:System.Data.DataTable> clase desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta el **Diseñador de Dataset**.

3. Agregue columnas para definir su tabla de datos. Haga doble clic en la tabla y elija **agregar** > **columna**. Use la **propiedades** ventana para establecer el tipo de datos de la columna y una clave si es necesario.

Tablas independientes necesitan implementar `Fill` lógica en tablas independientes para que puede rellenar con datos. Para obtener información sobre cómo rellenar tablas de datos independiente, consulte [llenar un DataSet desde un objeto DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)