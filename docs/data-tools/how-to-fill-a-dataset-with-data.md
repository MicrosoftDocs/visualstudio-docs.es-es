---
title: "C&#243;mo: Llenar un conjunto de datos con datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "datos [Visual Basic], cargar en conjuntos de datos"
  - "conjuntos de datos [Visual Basic], rellenar"
  - "objetos DataTable, cargar"
  - "TableAdapter.Fill"
  - "TableAdapter.GetData"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# C&#243;mo: Llenar un conjunto de datos con datos
La frase "rellenar un conjunto de datos con datos" hace referencia a la carga de datos en los objetos <xref:System.Data.DataTable> individuales que constituyen el conjunto de datos.  Rellene las tablas de datos ejecutando consultas de TableAdapter o comandos del adaptador de datos \(por ejemplo, <xref:System.Data.SqlClient.SqlDataAdapter>\).  
  
 Si debe utilizar TableAdapters o adaptadores de datos depende de cómo haya creado el conjunto de datos.  Si utilizó las herramientas de diseño en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] como [Asistente para la configuración de orígenes de datos](../data-tools/media/data-source-configuration-wizard.png), el conjunto de datos contendrá TableAdapters.  Para obtener más información sobre TableAdapters, vea [Información general sobre TableAdapter](../data-tools/tableadapter-overview.md).  Si creó el conjunto de datos mediante programación, necesitará crear adaptadores de datos para cargar datos en las tablas de datos.  
  
> [!NOTE]
>  Al arrastrar elementos desde [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md) a un formulario, el código para rellenar la tabla con datos se agrega automáticamente al controlador del evento `Form_Load`.  Abra el formulario en el editor de código para ver la sintaxis exacta que debe usar para rellenar tablas concretas.  Si no desea rellenar la tabla cuando se carga el formulario, puede mover este código a algún otro método o quitarlo completamente.  
  
## Rellenar un conjunto de datos mediante TableAdapter  
 Puede llamar a una consulta en el objeto TableAdapter para cargar datos en las tablas de datos de un conjunto de datos.  Pase el objeto <xref:System.Data.DataTable> que desee rellenar a la consulta de TableAdapter.  Si la consulta acepta parámetros, páselos también al método.  Si el conjunto de datos contiene varias tablas, debe tener objetos TableAdapters separados por tablas y, por consiguiente, debe rellenar cada tabla por separado.  
  
> [!NOTE]
>  De manera predeterminada, cada vez que ejecuta una consulta de TableAdapter, los datos de la tabla se borran antes de que se carguen los resultados de la consulta en la tabla.  Puede mantener los datos existentes en la tabla y anexar los resultados estableciendo la propiedad `ClearBeforeFill` de TableAdapter en `false`.  
  
#### Para rellenar un conjunto de datos mediante TableAdapter  
  
1.  Abra el formulario o componente en el **Editor de código**.  
  
2.  Agregue el código a cualquier parte de la aplicación donde necesite cargar una tabla con datos.  Si su consulta no acepta parámetros, pase el objeto <xref:System.Data.DataTable> que desea rellenar.  El código puede ser similar al siguiente:  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  Si la consulta acepta parámetros, pase el objeto <xref:System.Data.DataTable> que desee rellenar y los parámetros esperados por la consulta.  Dependiendo de los parámetros reales de su consulta, el código puede parecerse a los siguientes ejemplos:  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## Rellenar un conjunto de datos mediante DataAdapter  
 Llame al método `Fill` del adaptador de datos.  De este modo, el adaptador ejecuta una instrucción SQL o un procedimiento almacenado al que se hace referencia en su propiedad `SelectCommand` y guarda los resultados en una tabla del conjunto de datos.  Si el conjunto de datos contiene varias tablas, debe tener los adaptadores de datos separados por tablas y, por consiguiente, debe rellenar cada tabla por separado.  
  
#### Para rellenar un conjunto de datos mediante DataAdapter  
  
-   Llame al método <xref:System.Data.Common.DataAdapter.Fill%2A> de <xref:System.Data.Common.DataAdapter>, y pase el objeto <xref:System.Data.DataSet> o <xref:System.Data.DataTable> en el que se van a cargar los datos.  Por ejemplo:  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     Normalmente, debe proporcionar el nombre del objeto <xref:System.Data.DataTable> en el que se van a cargar los datos.  Si pasa el nombre de un <xref:System.Data.DataSet> en lugar de una tabla de datos concreta, se agrega un objeto <xref:System.Data.DataTable> denominado `Table1` al conjunto de datos y se carga con los resultados de la base de datos \(a diferencia de que se carguen los datos en un objeto <xref:System.Data.DataTable> existente en el conjunto de datos\).  Para obtener más información, vea [Llenar un DataSet desde un DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
## Vea también  
 [Rellenar los conjuntos de datos con datos](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)