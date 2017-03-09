---
title: "C&#243;mo: Separar conjuntos de datos y TableAdapters en proyectos diferentes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "aplicaciones con n capas, separar conjuntos de datos y TableAdapters"
  - "TableAdapters, aplicaciones con n capas"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Separar conjuntos de datos y TableAdapters en proyectos diferentes
Los conjuntos de datos con tipo se han mejorado de forma que [TableAdapters](../Topic/TableAdapters.md) y las clases de conjunto de datos se puedan generar en proyectos independientes.  Esto permite separar rápidamente los niveles de la aplicación y generar aplicaciones de datos con n niveles.  
  
 El procedimiento siguiente describe el proceso del uso del [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md) para generar código del conjunto de datos en un proyecto que es independiente del proyecto que contiene el código `TableAdapter` generado.  
  
## Separar conjuntos de datos y TableAdapters  
 Al separar el código del conjunto de datos del código de `TableAdapter`, el proyecto que contendrá el código del conjunto de datos se debe encontrar en la solución actual.  Si este proyecto no se encuentra en la solución actual, no estará disponible en la lista **DataSet Project** en la ventana **Propiedades**.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para separar el conjunto de datos en un proyecto diferente  
  
1.  Abra una solución que contenga un conjunto de datos \(archivo .xsd\).  
  
    > [!NOTE]
    >  Si la solución no contiene el proyecto en el que desea separar el código del conjunto de datos, créelo o agregue un proyecto existente a la solución.  
  
2.  Haga doble clic en un archivo de conjunto de datos con tipo \(un archivo .xsd\) en el **Explorador de soluciones** para abrir el conjunto de datos en el **Diseñador de DataSet**.  
  
3.  Haga clic en una área vacía del **Diseñador de DataSet**.  
  
4.  Busque el nodo **DataSet Project** en la ventana **Propiedades**.  
  
5.  En la lista **DataSet Project**, haga clic en el nombre del proyecto en el que desea generar el código del conjunto de datos.  
  
     Después de hacer clic en el proyecto en el que desea generar el código del conjunto de datos, la propiedad **DataSet File** se rellena con un nombre de archivo predeterminado.  Si tiene que cambiar este nombre, puede cambiarlo.  Además, si desea generar el código del conjunto de datos en un directorio concreto, puede establecer la propiedad **Carpeta de proyecto** con el nombre de una carpeta.  
  
    > [!NOTE]
    >  Cuando los conjuntos de datos se separan de los TableAdapters \(estableciendo la propiedad **DataSet Project**\), las clases de conjunto de datos parciales existentes no se trasladarán automáticamente.  Las clases de conjunto de datos parciales existentes se deberán trasladar manualmente al proyecto de conjunto de datos.  
  
6.  Guarde el conjunto de datos.  
  
     El código del conjunto de datos se genera en el proyecto seleccionado en la propiedad **DataSet Project**, y el código de **TableAdapter** se genera en el proyecto actual.  
  
 De forma predeterminada, después de separar el conjunto de datos y el código de `TableAdapter`, el resultado es un archivo de clase adicional en cada proyecto.  El proyecto original tiene un archivo que se denomina DatasetName.Designer.vb \(o DatasetName.Designer.cs\) que contiene el código de `TableAdapter`.  El proyecto designado en la propiedad **DataSet Project** tiene un archivo que se denomina DatasetName.DataSet.Designer.vb \(o DatasetName.DataSet.Designer.cs\) que contiene el código del conjunto de datos.  
  
> [!NOTE]
>  Con el conjunto de datos o el proyecto `TableAdapter` seleccionado, haga clic en **Mostrar todos los archivos** en el **Explorador de soluciones** para ver el archivo de clase generado.  
  
## Vea también  
 [Información general sobre aplicaciones de datos con n capas](../data-tools/n-tier-data-applications-overview.md)   
 [Tutorial: Crear una aplicación de datos con n niveles](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Actualización jerárquica](../data-tools/hierarchical-update.md)   
 [Obtener acceso a los datos en Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)