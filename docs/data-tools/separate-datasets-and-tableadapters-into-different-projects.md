---
title: Error de uso de proyectos independientes
description: Separar conjuntos de datos y TableAdapters en proyectos diferentes
ms.date: 11/04/2016
ms.topic: how-to
ms.custom: SEO-VS-2020
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4ed815b73cade73c38b52528d918b4af4de2a618
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036280"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separar conjuntos de datos y TableAdapters en proyectos diferentes
Los conjuntos de valores de tipos se han mejorado para que las clases [TableAdapter](create-and-configure-tableadapters.md) y DataSet se puedan generar en proyectos independientes. Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.

En el procedimiento siguiente se describe el proceso de uso de la **Diseñador de DataSet** para generar código de conjunto de elementos en un proyecto independiente del proyecto que contiene el código de TableAdapter generado.

## <a name="separate-datasets-and-tableadapters"></a>Separar conjuntos de objetos y TableAdapters
Al separar el código del conjunto de objetos del código de TableAdapter, el proyecto que contiene el código del conjunto de los conjuntos de pruebas debe encontrarse en la solución actual. Si este proyecto no se encuentra en la solución actual, no estará disponible en la lista **conjunto de proyectos** de la ventana **propiedades** .

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar el conjunto de datos en un proyecto diferente

1. Abra una solución que contenga un conjunto de datos (archivo *.xsd*).

    > [!NOTE]
    > Si la solución no contiene el proyecto en el que desea separar el código del conjunto de información, cree el proyecto o agregue un proyecto existente a la solución.

2. Haga doble clic en un archivo de conjunto de datos con tipo (un archivo *.xsd*) en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.

3. Seleccione un área vacía de la **Diseñador de DataSet**.

4. En la ventana **propiedades** , busque el nodo del **proyecto DataSet** .

5. En la lista **conjunto de proyectos** , seleccione el nombre del proyecto en el que desea generar el código del conjunto de código.

     Después de seleccionar el proyecto en el que desea generar el código del conjunto de archivos, la propiedad del **archivo de conjunto de archivos** se rellena con un nombre de archivo predeterminado. Puede cambiar este nombre si es necesario. Además, si desea generar el código del conjunto de datos en un directorio concreto, puede establecer la propiedad **Carpeta de proyecto** con el nombre de una carpeta.

    > [!NOTE]
    > Cuando se separan los conjuntos de objetos y TableAdapters (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de tipos parciales existentes en el proyecto no se moverán automáticamente. Las clases de conjunto de tipos parciales existentes deben moverse manualmente al proyecto de conjunto de DataSet.

6. Guarde el conjunto de datos.

     El código del conjunto de objetos se genera en el proyecto seleccionado en la propiedad **DataSet Project** y el código **TableAdapter** se genera en el proyecto actual.

De forma predeterminada, después de separar el código de conjunto de datos y TableAdapter, el resultado es un archivo de clase discreto en cada proyecto. El proyecto original tiene un archivo denominado *DatasetName. Designer. VB* (o *DatasetName.Designer.CS*) que contiene el código de TableAdapter. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado *DatasetName. DataSet. Designer. vb* (o *DatasetName.DataSet.Designer.CS*) que contiene el código del conjunto de archivos.

> [!NOTE]
> Para ver el archivo de clase generado, seleccione el proyecto de conjunto de archivos o TableAdapter. A continuación, en **Explorador de soluciones**, seleccione **Mostrar todos los archivos**.

## <a name="see-also"></a>Consulte también

- [Introducción a las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md)
- [Tutorial: crear una aplicación de datos de N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Actualización jerárquica](../data-tools/hierarchical-update.md)
- [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [ADO.NET](/dotnet/framework/data/adonet/index)
