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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c84105387c708fa16e0b1d5c3294ef909466524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72631204"
---
# <a name="create-and-configure-datasets-in-visual-studio"></a>Crear y configurar conjuntos de datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *conjunto* de datos es un conjunto de objetos que almacenan datos de una base de datos en memoria y admiten el seguimiento de cambios para habilitar operaciones de creación, lectura, actualización y eliminación (CRUD) en esos datos sin necesidad de estar siempre conectados a la base de datos. Los conjuntos de datos se diseñaron para formularios sencillos sobre aplicaciones empresariales de *datos* . En el caso de las aplicaciones nuevas, considere la posibilidad de usar Entity Framework para almacenar y modelar los datos en la memoria. Para trabajar con conjuntos de datos, debe tener un conocimiento básico de los conceptos de base de datos.

 En tiempo de diseño, se crea una clase con tipo <xref:System.Data.DataSet> en Visual Studio mediante el **Asistente para la configuración de orígenes de datos**. Para obtener información sobre cómo crear conjuntos de datos mediante programación, vea [crear un conjunto de](https://msdn.microsoft.com/library/57629d8f-393e-4677-8b83-29ffde27f5fc)datos.

## <a name="create-a-new-dataset-by-using-the-data-source-configuration-wizard"></a>Crear un nuevo conjunto de datos mediante el Asistente para la configuración de orígenes de datos

1. En el menú **proyecto** , haga clic en **Agregar nuevo origen de datos** para iniciar el Asistente para la configuración de orígenes de **datos**.

2. Elija el tipo de origen de datos al que se va a conectar.

     ![Asistente para configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png "Asistente para configuración de orígenes de datos")

3. En el caso de las bases de datos, elija las bases de datos que serán el origen de datos del conjunto de datos.

     ![Origen de datos, elegir una conexión](../data-tools/media/data-source-choose-a-connection.png "Origen de datos, elegir una conexión")

4. Elija las tablas (o columnas individuales), procedimientos almacenados, funciones y vistas de la base de datos que desea que se representen en el conjunto de datos.

     ![Selección de objetos de la base de datos](../data-tools/media/raddata-chose-objects.png "raddata elegir objetos")

5. Haga clic en **Finalizar**

6. El conjunto de DataSet aparece como un nodo en **Explorador de soluciones**:

     ![Conjunto de Explorador de soluciones](../data-tools/media/dataset-in-solution-explorer.png "Conjunto de Explorador de soluciones")

     Haga clic en ese nodo y el conjunto de DataSet aparecerá en el **Diseñador de DataSet**. Tenga en cuenta que cada tabla del conjunto de resultados tiene un objeto TableAdapter asociado, que se representa en la parte inferior. El adaptador de tabla se utiliza para rellenar el conjunto de datos y, opcionalmente, para enviar comandos a la base de datos.

     ![Diseñador de DataSet](../data-tools/media/dataset-designer.png "Diseñador de DataSet")

7. Las líneas de relación que conectan las tablas representan relaciones de tabla, tal como se define en la base de datos. De forma predeterminada, las restricciones de clave externa en una base de datos se representan solo como una relación, con las reglas de actualización y eliminación establecidas en ninguno. Normalmente, eso es lo que desea. Sin embargo, puede hacer clic en las líneas para abrir el cuadro de diálogo de **relación** , donde puede cambiar el comportamiento de las actualizaciones jerárquicas. Para obtener más información, vea [relaciones en conjuntos de](../data-tools/relationships-in-datasets.md) datos y [actualización jerárquica](../data-tools/hierarchical-update.md).

     ![Cuadro de diálogo relación de DataSet](../data-tools/media/raddata-relation-dialog.png "cuadro de diálogo relación raddata")

8. Haga clic en un nombre de tabla, adaptador de tabla o columna de una tabla para ver sus propiedades en la ventana **propiedades** . Puede modificar algunos de los valores aquí. Simplemente Recuerde que está modificando el conjunto de datos, no la base de datos de origen.

     ![Propiedades de la columna DataSet](../data-tools/media/dataset-column-properties.png "Propiedades de la columna DataSet")

9. Puede agregar nuevas tablas o adaptadores de tabla al conjunto de elementos, o agregar nuevas consultas para los adaptadores de tabla existentes o especificar nuevas relaciones entre las tablas arrastrando esos elementos desde la pestaña **cuadro de herramientas** . Esta pestaña aparece cuando el **Diseñador de DataSet** tiene el foco.

     ![Cuadro de herramientas de conjunto de](../data-tools/media/raddata-dataset-toolbox.png "Cuadro de herramientas de raddata DataSet")

10. A continuación, es probable que desee especificar cómo rellenar el conjunto de datos con datos. Para ello, use el **Asistente para la configuración de TableAdapter**. Para obtener más información, vea [rellenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md) .

## <a name="add-a-database-table-or-other-object-to-an-existing-dataset"></a>Agregar una tabla de base de datos u otro objeto a un conjunto de datos existente
 En este procedimiento se muestra cómo agregar una tabla de la misma base de datos que usó para crear primero el conjunto de datos.

1. Haga clic en el nodo conjunto de los **Explorador de soluciones** para poner el diseñador de DataSet en el foco.

2. Haga clic en la pestaña **orígenes de datos** en el margen izquierdo de Visual Studio o escriba `Data Sources` en el **Inicio rápido**.

3. Haga clic con el botón secundario en el nodo conjunto de datos y seleccione **Configurar origen de datos con el asistente** .

     ![Menú contextual de origen de datos](../data-tools/media/data-source-context-menu.png "Menú contextual de origen de datos")

4. Use el Asistente para especificar qué tablas adicionales, o procedimientos almacenados u otro objeto de base de datos, desea agregar al conjunto de datos.

## <a name="add-a-stand-alone-data-table-to-a-dataset"></a>Agregar una tabla de datos independiente a un conjunto de datos

1. Abra su conjunto de datos en el **Diseñador de Dataset**.

2. Arrastre una <xref:System.Data.DataTable> clase desde la pestaña **DataSet** del **cuadro de herramientas** hasta el **Diseñador de DataSet**.

3. Agregue columnas para definir su tabla de datos. Para obtener más información, vea [Cómo: Agregar columnas a un objeto DataTable](https://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).

4. Las tablas independientes deben implementar la `Fill` lógica en tablas independientes para que pueda rellenarlas con datos. Para obtener información sobre cómo rellenar tablas de datos independientes, vea [rellenar un conjunto de datos desde un DataAdapter](https://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).
