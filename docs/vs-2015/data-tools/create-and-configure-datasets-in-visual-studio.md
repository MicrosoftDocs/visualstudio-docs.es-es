---
title: Creación y configuración de conjuntos de datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- typed datasets, creating
- datasets [Visual Basic], creating
ms.assetid: 58f33b43-24e1-43b1-b08b-b74329960bd6
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b3073f79cc58296b6952d610384d06648aa6ce3d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093480"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Crear y configurar conjuntos de datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *dataset* es un conjunto de objetos que almacenar datos de una base de datos en memoria y admitir el seguimiento de cambios para permitir crear, leer, actualizar y eliminar operaciones (CRUD) en los datos sin necesidad de estar siempre conectados a la base de datos. Los conjuntos de datos se diseñaron para simple *formularios sobre datos* aplicaciones empresariales. Para las aplicaciones nuevas, considere el uso de Entity Framework para almacenar y modelar los datos en memoria. Para trabajar con conjuntos de datos, debe tener conocimientos básicos sobre conceptos de base de datos.

 Creación de un tipo <xref:System.Data.DataSet> clase en Visual Studio en tiempo de diseño mediante el uso de la **Asistente para configuración de origen de datos**. Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [creación de un conjunto de datos](http://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc).

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Crear un nuevo conjunto de datos mediante el Asistente para configuración de orígenes de datos

1. En el **proyecto** menú, haga clic en **Agregar nuevo origen de datos** para iniciar el **Asistente para configuración de origen de datos**.

2. Elija el tipo de origen de datos se va a conectar.

     ![Asistente para la configuración del origen de datos](../data-tools/media/data-source-configuration-wizard.png "Asistente para la configuración del origen de datos")

3. Para las bases de datos, elija la base de datos o bases de datos que serán el origen de datos para el conjunto de datos.

     ![Seleccione la conexión de origen de datos](../data-tools/media/data-source-choose-a-connection.png "seleccione la conexión de origen de datos")

4. Elija las tablas (o columnas individuales), procedimientos almacenados, funciones y vistas desde la base de datos que desea que se puede representar en el conjunto de datos.

     ![Elija los objetos de base de datos](../data-tools/media/raddata-chose-objects.png "raddata elegir objetos")

5. Haga clic en **Finalizar**.

6. El conjunto de datos aparece como un nodo en **el Explorador de soluciones**:

     ![Conjunto de datos en el Explorador de soluciones](../data-tools/media/dataset-in-solution-explorer.png "conjunto de datos en el Explorador de soluciones")

     Haga clic en ese nodo y el conjunto de datos aparece en el **Diseñador de DataSet**. Tenga en cuenta que cada tabla del conjunto de datos tiene un objeto TableAdapter asociado, que se representa en la parte inferior. El adaptador de tabla se utiliza para rellenar el conjunto de datos y, opcionalmente, para enviar comandos a la base de datos.

     ![Diseñador de DataSet](../data-tools/media/dataset-designer.png "Diseñador de DataSet")

7. Las líneas de relación que conecta las tablas representan las relaciones entre tablas, tal como se define en la base de datos. De forma predeterminada, restricciones foreign key en una base de datos se representan como sólo, una relación con la actualización y eliminación las reglas que se establece en none. Por lo general, es lo que desea. Sin embargo, puede hacer clic en las líneas para que aparezca el **relación** cuadro de diálogo, donde puede cambiar el comportamiento de las actualizaciones jerárquicas. Para obtener más información, consulte [relaciones en conjuntos de datos](../data-tools/relationships-in-datasets.md) y [actualización jerárquica](../data-tools/hierarchical-update.md).

     ![Cuadro de diálogo conjunto de datos relación](../data-tools/media/raddata-relation-dialog.png "raddata cuadro de diálogo relación")

8. Haga clic en una tabla, el adaptador de tabla o el nombre de columna en una tabla para ver sus propiedades en el **propiedades** ventana. Puede modificar algunos de los valores aquí. Sólo recuerde que va a modificar el conjunto de datos, no la base de datos de origen.

     ![Propiedades de columna del conjunto de datos](../data-tools/media/dataset-column-properties.png "propiedades de columna del conjunto de datos")

9. Puede agregar nuevas tablas o adaptadores de tabla al conjunto de datos, o agregar nuevas consultas para los adaptadores de tabla existente o especificar nuevas relaciones entre tablas arrastrando los elementos desde el **cuadro de herramientas** ficha. Esta pestaña aparece cuando el **Diseñador de DataSet** tiene el foco.

     ![Conjunto de datos de cuadro de herramientas](../data-tools/media/raddata-dataset-toolbox.png "raddata del cuadro de herramientas del conjunto de datos")

10. A continuación, probablemente desee especificar cómo rellenar el conjunto de datos con datos. Para ello, usa el **TableAdapter Configuration Wizard**. Para obtener más información, consulte [llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Agregar una tabla de base de datos u otro objeto a un conjunto de datos existente
 Este procedimiento muestra cómo agregar una tabla de la misma base de datos que usó para crear el conjunto de datos.

1. Haga clic en el nodo de conjunto de datos **el Explorador de soluciones** para poner el Diseñador de DataSet en el foco.

2. Haga clic en el **orígenes de datos** pestaña en el margen izquierdo de Visual Studio, o bien escriba `Data Sources` en **inicio rápido**.

3. Haga clic en el nodo de conjunto de datos y seleccione **Configurar origen de datos con el asistente** .

     ![Menú de contexto de origen de datos](../data-tools/media/data-source-context-menu.png "menú de contexto de origen de datos")

4. Use el Asistente para especificar qué tablas adicionales, o los procedimientos almacenados u otro objeto de base de datos, para agregar al conjunto de datos.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Agregar una tabla de datos independiente a un conjunto de datos

1. Abra su conjunto de datos en el **Diseñador de Dataset**.

2. Arrastre un <xref:System.Data.DataTable> clase desde el **conjunto de datos** pestaña de la **cuadro de herramientas** hasta el **Diseñador de Dataset**.

3. Agregue columnas para definir su tabla de datos. Para obtener más información, vea [Cómo: Agregar columnas a un objeto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Tablas independientes necesitan implementar `Fill` lógica en tablas independientes para que puede rellenar con datos. Para obtener información sobre cómo rellenar tablas de datos independiente, consulte [llenar un DataSet desde un objeto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
