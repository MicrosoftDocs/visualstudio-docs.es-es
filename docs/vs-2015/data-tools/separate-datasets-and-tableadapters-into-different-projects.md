---
title: Separar conjuntos de objetos y TableAdapters en proyectos diferentes | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f6ec76e79cc1c4759cbe05d8bdcacc1297b655b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655428"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separar conjuntos de datos y TableAdapters en proyectos diferentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los conjuntos de valores de tipos se han mejorado para que las clases [TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) y DataSet se puedan generar en proyectos independientes. Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.

 En el procedimiento siguiente se describe el proceso de uso de la Diseñador de DataSet para generar código de conjunto de elementos en un proyecto independiente del proyecto que contiene el código `TableAdapter` generado.

## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets y TableAdapters
 Al separar el código de conjunto de los conjuntos de código de `TableAdapter`, el proyecto que contiene el código del conjunto de los mismos debe estar ubicado en la solución actual. Si este proyecto no se encuentra en la solución actual, no estará disponible en la lista **conjunto de proyectos** de la ventana **propiedades** .

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar el conjunto de datos en un proyecto diferente

1. Abra una solución que contenga un conjunto de datos (archivo .xsd).

   > [!NOTE]
   > Si la solución no contiene el proyecto en el que desea separar el código del conjunto de información, cree el proyecto o agregue un proyecto existente a la solución.

2. Haga doble clic en un archivo de conjunto de archivos con tipo (un archivo. xsd) en **Explorador de soluciones** para abrir el conjunto de información en el **Diseñador de DataSet**.

3. Seleccione un área vacía de la **Diseñador de DataSet**.

4. En la ventana **propiedades** , busque el nodo del **proyecto DataSet** .

5. En la lista **conjunto de proyectos** , seleccione el nombre del proyecto en el que desea generar el código del conjunto de código.

    Después de seleccionar el proyecto en el que desea generar el código del conjunto de archivos, la propiedad del **archivo de conjunto de archivos** se rellena con un nombre de archivo predeterminado. Puede cambiar este nombre si es necesario. Además, si desea generar el código del conjunto de datos en un directorio concreto, puede establecer la propiedad **Carpeta de proyecto** con el nombre de una carpeta.

   > [!NOTE]
   > Cuando se separan los conjuntos de objetos y TableAdapters (estableciendo la propiedad **DataSet Project** ), las clases de conjunto de tipos parciales existentes en el proyecto no se moverán automáticamente. Las clases parciales de conjunto de los conjuntos de los existentes deben moverse manualmente al proyecto de conjunto de DataSet.

6. Guarde el conjunto de datos.

    El código del conjunto de objetos se genera en el proyecto seleccionado en la propiedad **DataSet Project** y el código **TableAdapter** se genera en el proyecto actual.

   De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado DatasetName. Designer. VB (o DatasetName.Designer.cs) que contiene el código `TableAdapter`. El proyecto designado en la propiedad **DataSet Project** tiene un archivo denominado DataSetName. DataSet. Designer. VB (o DataSetName.DataSet.Designer.CS) que contiene el código del conjunto de archivos.

> [!NOTE]
> Para ver el archivo de clase generado, seleccione el conjunto de información o `TableAdapter` proyecto. A continuación, en **Explorador de soluciones**, seleccione **Mostrar todos los archivos** .

## <a name="see-also"></a>Vea también
 [Información general sobre las aplicaciones de datos de n niveles](../data-tools/n-tier-data-applications-overview.md) [Tutorial: crear una aplicación de datos de n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [Actualizar jerárquicamente](../data-tools/hierarchical-update.md) [obtener acceso a datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md) [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)
