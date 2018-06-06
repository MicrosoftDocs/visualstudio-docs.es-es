---
title: Crear y configurar conjuntos de datos en Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b47df77b9666b46f24665e9c99cbf9a0c52593cd
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746577"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Crear y configurar conjuntos de datos en Visual Studio

A *conjunto de datos* es un conjunto de objetos que almacenar los datos de una base de datos en memoria y admitir el seguimiento de cambios para permitir crear, leer, actualizar y eliminar operaciones (CRUD) en los datos sin necesidad de estar siempre conectado a la base de datos. Conjuntos de datos se diseñaron para simple *formularios sobre datos* aplicaciones empresariales. Para las aplicaciones nuevas, considere el uso de Entity Framework para almacenar y los datos en memoria del modelo. Para trabajar con conjuntos de datos, debe tener conocimientos básicos sobre conceptos de base de datos.

Se crea un tipo <xref:System.Data.DataSet> clase en Visual Studio en tiempo de diseño mediante la **Asistente para configuración de orígenes de datos**. Para obtener información acerca de cómo crear conjuntos de datos mediante programación, vea [crear un conjunto de datos (ADO.NET)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Crear un nuevo conjunto de datos mediante el Asistente para configuración de orígenes de datos

1.  En el **proyecto** menú, haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de orígenes de datos**.

2.  Elija el tipo de origen de datos que se va a conectar a.

     ![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

3.  Bases de datos, elija la base de datos o bases de datos que serán el origen de datos para el conjunto de datos.

     ![Elegir la conexión de origen de datos](../data-tools/media/data-source-choose-a-connection.png)

4.  Elija las tablas (o columnas individuales), procedimientos almacenados, funciones y vistas de la base de datos que desee representar en el conjunto de datos.

     ![Seleccione los objetos de base de datos](../data-tools/media/raddata-chose-objects.png)

5.  Haga clic en **Finalizar**.

6.  El conjunto de datos aparece como un nodo en **el Explorador de soluciones**:

     ![Conjunto de datos en el Explorador de soluciones](../data-tools/media/dataset-in-solution-explorer.png)

     Haga clic en ese nodo y el conjunto de datos aparece en la **Diseñador de DataSet**. Tenga en cuenta que cada tabla del conjunto de datos tiene un objeto TableAdapter asociado, que se representa en la parte inferior. El adaptador de la tabla se utiliza para rellenar el conjunto de datos y, opcionalmente, para enviar comandos a la base de datos.

     ![Diseñador de DataSet](../data-tools/media/dataset-designer.png)

7.  Las líneas de relación que conecta las tablas representan relaciones de tabla, tal como se define en la base de datos. De forma predeterminada, las restricciones de clave externa en una base de datos se representan como una relación, con la actualización y eliminación las reglas establecidas en none. Por lo general, es lo que desea. Sin embargo, puede hacer clic en las líneas para que aparezca el **relación** cuadro de diálogo, donde puede cambiar el comportamiento de las actualizaciones jerárquicas. Para obtener más información, consulte [relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md) y [actualización jerárquica](../data-tools/hierarchical-update.md).

     ![Cuadro de diálogo relación de conjunto de datos](../data-tools/media/raddata-relation-dialog.png)

8.  Haga clic en una tabla, el adaptador de la tabla o el nombre de columna en una tabla para ver sus propiedades en el **propiedades** ventana. Puede modificar algunos de los valores aquí. Recuerde que va a modificar el conjunto de datos, no la base de datos de origen.

     ![Propiedades de columna de conjunto de datos](../data-tools/media/dataset-column-properties.png)

9. Puede agregar nuevas tablas o adaptadores de tablas al conjunto de datos, o agregar nuevas consultas para los adaptadores de tabla existente o especificar nuevas relaciones entre tablas arrastrando los elementos desde la **cuadro de herramientas** ficha. Esta ficha aparece cuando la **Diseñador de DataSet** tiene el foco.

     ![Cuadro de herramientas del conjunto de datos](../data-tools/media/raddata-dataset-toolbox.png)

10. A continuación, probablemente desee especificar cómo rellenar el conjunto de datos con datos. Para ello, use la **Asistente para configuración de TableAdapter**. Para obtener más información, consulte [rellenar conjuntos de datos mediante el uso de los TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Agregar una tabla de base de datos u otro objeto a un conjunto de datos existente

Este procedimiento muestra cómo agregar una tabla de la misma base de datos que usó para crear el conjunto de datos.

1.  Haga clic en el nodo de conjunto de datos en **el Explorador de soluciones** para abrir el Diseñador de dataset en foco.

2.  Haga clic en el **orígenes de datos** ficha en el margen izquierdo de Visual Studio, o bien escriba `Data Sources` en **inicio rápido**.

3.  Haga clic en el nodo de conjunto de datos y seleccione **Configurar origen de datos con el Asistente para**.

     ![Menú contextual de origen de datos](../data-tools/media/data-source-context-menu.png)

4.  Use el Asistente para especificar qué tablas adicionales, o procedimientos almacenados u otro objeto de base de datos, para agregar al conjunto de datos.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Agregar una tabla de datos independiente a un conjunto de datos

1.  Abra su conjunto de datos en el **Diseñador de Dataset**.

2.  Arrastre un <xref:System.Data.DataTable> clase desde el **conjunto de datos** pestaña de la **cuadro de herramientas** en el **Diseñador de Dataset**.

3.  Agregue columnas para definir su tabla de datos. Haga doble clic en la tabla y elija **Agregar > columna**. Use la **propiedades** ventana para establecer el tipo de datos de la columna y una clave si es necesario.

4.  Tablas independientes necesitan para implementar `Fill` lógica en tablas independientes para que se puede rellenar con datos. Para obtener información sobre cómo rellenar tablas de datos independiente, consulte [llenar un DataSet desde un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Vea también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)