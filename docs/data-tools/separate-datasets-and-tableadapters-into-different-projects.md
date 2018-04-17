---
title: Separar conjuntos de datos y TableAdapters en proyectos diferentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 304fa17ab036f868b8653efe64a59f68f0452723
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Conjuntos de datos independiente y TableAdapters en proyectos diferentes
Los conjuntos de datos se han mejorado para que la [TableAdapters](create-and-configure-tableadapters.md) y clases de conjunto de datos se puedan generar en proyectos independientes. Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.  
  
El siguiente procedimiento describe el proceso de uso de la **Diseñador de Dataset** para generar el código de conjunto de datos en un proyecto independiente desde el proyecto que contiene el código de TableAdapter generado.  
  
## <a name="separate-datasets-and-tableadapters"></a>Conjuntos de datos independiente y TableAdapters  
Al separar el código de conjunto de datos desde el código de TableAdapter, el proyecto que contiene el código de conjunto de datos debe encontrarse en la solución actual. Si este proyecto no se encuentra en la solución actual, no estarán disponible en la **DataSet Project** lista en la **propiedades** ventana.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar el conjunto de datos en un proyecto diferente  
  
1.  Abra una solución que contenga un conjunto de datos (archivo .xsd).  
  
    > [!NOTE]
    >  Si la solución no contiene el proyecto en el que desea separar el código del conjunto de datos, cree el proyecto, o agregar un proyecto existente a la solución.  
  
2.  Haga doble clic en un archivo de conjunto de datos con tipo (archivo .xsd) en **el Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de Dataset**.  
  
3.  Seleccione un área vacía de la **Diseñador de Dataset**.  
  
4.  En el **propiedades** ventana, busque la **DataSet Project** nodo.  
  
5.  En el **DataSet Project** lista, seleccione el nombre del proyecto en el que desea generar el código de conjunto de datos.  
  
     Después de seleccionar el proyecto en el que desea generar el código de conjunto de datos, el **archivo de conjunto de datos** propiedad se rellena con un nombre de archivo predeterminado. Puede cambiar este nombre si es necesario. Además, si desea generar el código de conjunto de datos en un directorio específico, puede establecer la **carpeta de proyecto** propiedad en el nombre de una carpeta.  
  
    > [!NOTE]
    >  Al separar conjuntos de datos y los TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se traslada automáticamente. Clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
6.  Guarde el conjunto de datos.  
  
     El código de conjunto de datos se genera en el proyecto seleccionado en el **DataSet Project** propiedad y el **TableAdapter** código se genera en el proyecto actual.  
  
De forma predeterminada, después de separar el conjunto de datos y el código de TableAdapter, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado DatasetName.Designer.vb (o DatasetName.Designer.cs) que contiene el código de TableAdapter. El proyecto designado en la **Dataset Project** propiedad tiene un archivo denominado DatasetName.DataSet.Designer.vb (o DatasetName.DataSet.Designer.cs) que contiene el código de conjunto de datos.  
  
> [!NOTE]
>  Para ver el archivo de clase generado, seleccione el conjunto de datos o un proyecto de TableAdapter. A continuación, en **el Explorador de soluciones**, seleccione **mostrar todos los archivos**.  
  
## <a name="see-also"></a>Vea también
[Información general sobre aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)   
[Tutorial: Crear una aplicación de datos con N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
[Actualización jerárquica](../data-tools/hierarchical-update.md)   
[Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
[ADO.NET](/dotnet/framework/data/adonet/index)