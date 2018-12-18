---
title: Separar conjuntos de datos y TableAdapters en proyectos diferentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e94c76254b14bdf82e4e7a219cbb0f35cb532f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824333"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Separar conjuntos de datos y TableAdapters en proyectos diferentes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Objetos DataSet con tipo se han mejorado para que la [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) y clases de conjunto de datos se pueden generar en proyectos independientes. Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.  
  
 El siguiente procedimiento describe cómo usar el[crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) para generar código de conjunto de datos en un proyecto que es independiente del proyecto que contiene el texto generado `TableAdapter` código.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets y TableAdapters  
 Al separar el código del conjunto de datos desde `TableAdapter` código, el proyecto que contiene el código del conjunto de datos debe estar ubicado en la solución actual. Si este proyecto no se encuentra en la solución actual, no estará disponible en el **DataSet Project** lista en el **propiedades** ventana.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Para separar el conjunto de datos en un proyecto diferente  
  
1. Abra una solución que contenga un conjunto de datos (archivo .xsd).  
  
   > [!NOTE]
   >  Si la solución no contiene el proyecto en el que desea separar el código del conjunto de datos, crear el proyecto, o agregar un proyecto existente a la solución.  
  
2. Haga doble clic en un archivo de conjunto de datos con tipo (archivo .xsd) en **el Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de Dataset**.  
  
3. Seleccione un área vacía de la **Diseñador de Dataset**.  
  
4. En el **propiedades** ventana, busque la **DataSet Project** nodo.  
  
5. En el **DataSet Project** lista, seleccione el nombre del proyecto en el que desea generar el código del conjunto de datos.  
  
    Después de seleccionar el proyecto en el que desea generar el código del conjunto de datos, el **DataSet File** propiedad se rellena con un nombre de archivo predeterminado. Puede cambiar este nombre si es necesario. Además, si desea generar el código de conjunto de datos en un directorio específico, puede establecer el **carpeta del proyecto** propiedad en el nombre de una carpeta.  
  
   > [!NOTE]
   >  Al separar conjuntos de datos y TableAdapters (estableciendo la **DataSet Project** propiedad), las clases de conjunto de datos parciales existentes en el proyecto no se moverá automáticamente. Las clases de conjunto de datos parciales existentes se deben mover manualmente al proyecto de conjunto de datos.  
  
6. Guarde el conjunto de datos.  
  
    Se genera el código de conjunto de datos en el proyecto seleccionado en el **DataSet Project** propiedad y el **TableAdapter** se genera el código en el proyecto actual.  
  
   De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto. El proyecto original tiene un archivo denominado DatasetName.Designer.vb (o DatasetName.Designer.cs) que contiene el `TableAdapter` código. El proyecto designado en el **Dataset Project** propiedad tiene un archivo denominado DatasetName.DataSet.Designer.vb (o DatasetName.DataSet.Designer.cs) que contiene el código del conjunto de datos.  
  
> [!NOTE]
>  Para ver el archivo de clase generada, seleccione el conjunto de datos o `TableAdapter` proyecto. A continuación, en **el Explorador de soluciones**, seleccione **mostrar todos los archivos** .  
  
## <a name="see-also"></a>Vea también  
 [Introducción a las aplicaciones de datos con N niveles](../data-tools/n-tier-data-applications-overview.md)   
 [Tutorial: Crear una aplicación de datos con N niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)

