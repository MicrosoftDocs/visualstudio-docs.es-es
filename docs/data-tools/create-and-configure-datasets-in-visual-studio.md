---
title: Creación y configuración de conjuntos de datos
description: Crear y configurar conjuntos de valores en Visual Studio. Un conjunto de datos es un conjunto de objetos que almacenan datos de una base de datos en memoria y admite operaciones CRUD en esos datos.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: how-to
helpviewer_keywords:
- typed datasets, creating
- datasets, creating
- datasets, configuring
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5a9a10d68b5b0617b5c4e2152cbbbb920a7c683f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435409"
---
# <a name="how-to-create-and-configure-datasets-in-visual-studio"></a>Cómo: crear y configurar conjuntos de objetos en Visual Studio

Un conjunto de datos es un conjunto de objetos que almacenan datos de una base de datos en memoria y admiten el seguimiento de cambios para habilitar las operaciones de creación, lectura, actualización y eliminación (CRUD) en esos datos sin necesidad de estar siempre conectados a la base de datos. Los conjuntos de datos se diseñaron para formularios sencillos sobre aplicaciones empresariales de *datos* . En el caso de las aplicaciones nuevas, considere la posibilidad de usar Entity Framework para almacenar y modelar los datos en la memoria. Para trabajar con conjuntos de datos, debe tener un conocimiento básico de los conceptos de base de datos.

Puede crear una clase con tipo <xref:System.Data.DataSet> en Visual Studio en tiempo de diseño mediante el **Asistente para la configuración de orígenes de datos**. Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [crear un conjunto de datos (ADO.net)](/dotnet/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Crear un nuevo conjunto de datos mediante el Asistente para la configuración de orígenes de datos

1. Abra el proyecto en Visual Studio y, después, elija **proyecto**  >  **Agregar nuevo origen de datos** para iniciar el **Asistente para la configuración de orígenes de datos**.

2. Elija el tipo de origen de datos al que se va a conectar.

     ![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png)

3. Elija las bases de datos que serán el origen de datos del conjunto de datos.

     ![Origen de datos, elegir una conexión](../data-tools/media/data-source-choose-a-connection.png)

4. Elija las tablas (o columnas individuales), procedimientos almacenados, funciones y vistas de la base de datos que desea que se representen en el conjunto de datos.

     ![Selección de objetos de la base de datos](../data-tools/media/raddata-chose-objects.png)

5. Haga clic en **Finalizar**

   El conjunto de DataSet aparece como un nodo en **Explorador de soluciones**.

   ![Conjunto de Explorador de soluciones](../data-tools/media/dataset-in-solution-explorer.png)

6. Haga clic en el nodo DataSet en **Explorador de soluciones** para abrir el conjunto de DataSet en el **Diseñador de DataSet**. Cada tabla del conjunto de objetos tiene un `TableAdapter` objeto asociado, que se representa en la parte inferior. El adaptador de tabla se utiliza para rellenar el conjunto de datos y, opcionalmente, para enviar comandos a la base de datos.

   ![Diseñador de DataSet](../data-tools/media/dataset-designer.png)

7. Las líneas de relación que conectan las tablas representan relaciones de tabla, tal como se define en la base de datos. De forma predeterminada, las restricciones de clave externa en una base de datos se representan solo como una relación, con las reglas de actualización y eliminación establecidas en ninguno. Normalmente, eso es lo que desea. Sin embargo, puede hacer clic en las líneas para abrir el cuadro de diálogo de **relación** , donde puede cambiar el comportamiento de las actualizaciones jerárquicas. Para obtener más información, vea [relaciones en conjuntos de](../data-tools/relationships-in-datasets.md) datos y [actualización jerárquica](../data-tools/hierarchical-update.md).

     ![Cuadro de diálogo relación de DataSet](../data-tools/media/raddata-relation-dialog.png)

8. Haga clic en un nombre de tabla, adaptador de tabla o columna de una tabla para ver sus propiedades en la ventana **propiedades** . Puede modificar algunos de los valores aquí. Simplemente Recuerde que está modificando el conjunto de datos, no la base de datos de origen.

     ![Propiedades de la columna DataSet](../data-tools/media/dataset-column-properties.png)

9. Puede agregar nuevas tablas o adaptadores de tabla al conjunto de elementos, o agregar nuevas consultas para los adaptadores de tabla existentes o especificar nuevas relaciones entre las tablas arrastrando esos elementos desde la pestaña **cuadro de herramientas** . Esta pestaña aparece cuando el **Diseñador de DataSet** tiene el foco.

     ![Cuadro de herramientas de conjunto de](../data-tools/media/raddata-dataset-toolbox.png)

A continuación, es posible que desee especificar cómo rellenar el conjunto de datos con datos. Para ello, use el **Asistente para la configuración de TableAdapter**. Para obtener más información, vea [rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Agregar una tabla de base de datos u otro objeto a un conjunto de datos existente

En este procedimiento se muestra cómo agregar una tabla de la misma base de datos que usó para crear primero el conjunto de datos.

1. Haga clic en el nodo conjunto de los **Explorador de soluciones** para poner el **Diseñador de DataSet** en el foco.

2. Haga clic en la pestaña **orígenes de datos** en el margen izquierdo de Visual Studio o escriba los **orígenes de datos** en el cuadro de búsqueda.

3. Haga clic con el botón secundario en el nodo conjunto de datos y seleccione **Configurar origen de datos con el asistente**.

     ![Menú contextual de origen de datos](../data-tools/media/data-source-context-menu.png)

4. Use el Asistente para especificar qué tablas, procedimientos almacenados u otros objetos de base de datos adicionales se van a agregar al conjunto de datos.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Agregar una tabla de datos independiente a un conjunto de datos

1. Abra su conjunto de datos en el **Diseñador de Dataset**.

2. Arrastre una <xref:System.Data.DataTable> clase desde la pestaña **DataSet** del **cuadro de herramientas** hasta el **Diseñador de DataSet**.

3. Agregue columnas para definir su tabla de datos. Haga clic con el botón derecho en la tabla y elija **Agregar**  >  **columna**. Utilice la ventana **propiedades** para establecer el tipo de datos de la columna y una clave, si es necesario.

Las tablas independientes deben implementar la `Fill` lógica en tablas independientes para que pueda rellenarlas con datos. Para obtener información sobre cómo rellenar tablas de datos independientes, vea [rellenar un conjunto de datos desde un DataAdapter](/dotnet/framework/data/adonet/populating-a-dataset-from-a-dataadapter).

## <a name="see-also"></a>Consulte también

- [Herramientas de conjunto de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)
