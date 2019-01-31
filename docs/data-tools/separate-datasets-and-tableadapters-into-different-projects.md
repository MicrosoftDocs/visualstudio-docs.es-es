---
title: Separar conjuntos de datos y TableAdapters en proyectos diferentes
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: f5d3386cd6a379a1d38c40f97f3a9c4ef93e293d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947639"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separar conjuntos de datos y TableAdapters en proyectos diferentes
Objetos DataSet con tipo se han mejorado para que la [TableAdapters](create-and-configure-tableadapters.md) y clases de conjunto de datos se pueden generar en proyectos independientes. Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.

El siguiente procedimiento describe cómo usar el **Diseñador de Dataset** para generar código de conjunto de datos en un proyecto que es independiente del proyecto que contiene el código generado del TableAdapter.

## <a name="separate-datasets-and-tableadapters"></a>Conjuntos de datos independientes y TableAdapters
Al separar el código de conjunto de datos de código del TableAdapter, el proyecto que contiene el código del conjunto de datos debe estar ubicado en la solución actual. Si este proyecto no se encuentra en la solución actual, no estará disponible en el **DataSet Project** lista en el **propiedades** ventana.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar el conjunto de datos en un proyecto diferente

1.  Abra una solución que contenga un conjunto de datos (archivo *.xsd*).

    > [!NOTE]
    >  Si la solución no contiene el proyecto en el que desea separar el código del conjunto de datos, crear el proyecto, o agregar un proyecto existente a la solución.

2.  Haga doble clic en un archivo de conjunto de datos con tipo (un archivo *.xsd*) en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.

3.  Seleccione un área vacía de la **Diseñador de Dataset**.

4.  En el **propiedades** ventana, busque la **DataSet Project** nodo.

5.  En el **DataSet Project** lista, seleccione el nombre del proyecto en el que desea generar el código del conjunto de datos.

     Después de seleccionar el proyecto en el que desea generar el código del conjunto de datos, el **DataSet File** propiedad se rellena con un nombre de archivo predeterminado. Puede cambiar este nombre si es necesario. Además, si desea generar el código del conjunto de datos en un directorio concreto, puede establecer la propiedad **Carpeta de proyecto** con el nombre de una carpeta.

    > [!NOTE]
    >  Al separar conjuntos de datos y TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deben mover manualmente al proyecto de conjunto de datos.

6.  Guarde el conjunto de datos.

     Se genera el código de conjunto de datos en el proyecto seleccionado en el **DataSet Project** propiedad y el **TableAdapter** se genera el código en el proyecto actual.

De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase discretos en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName.Designer.vb* (o *DatasetName.Designer.cs*) que contiene el código del TableAdapter. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs*) que contiene el código del conjunto de datos.

> [!NOTE]
>  Para ver el archivo de clase generada, seleccione el conjunto de datos o proyecto de TableAdapter. A continuación, en **el Explorador de soluciones**, seleccione **mostrar todos los archivos**.

## <a name="see-also"></a>Vea también

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: Creación de una aplicación de datos de n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)