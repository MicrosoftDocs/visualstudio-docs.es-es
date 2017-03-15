---
title: "C&#243;mo: Guardar un conjunto de datos como XML | Microsoft Docs"
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
  - "datos [Visual Studio], guardar como XML"
  - "conjuntos de datos [Visual Basic], guardar como XML"
  - "guardar datos"
  - "XML [Visual Basic], conjuntos de datos"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Guardar un conjunto de datos como XML
Se puede tener acceso a los datos XML de un conjunto de datos llamando a los métodos XML disponibles en el conjunto de datos.  Para guardar los datos en formato XML, puede llamar al método <xref:System.Data.DataSet.GetXml%2A> o al método <xref:System.Data.DataSet.WriteXml%2A> de <xref:System.Data.DataSet>.  
  
 Al llamar al método <xref:System.Data.DataSet.GetXml%2A> se devuelve una cadena que contiene los datos de todas las tablas de datos del conjunto de datos con formato XML.  
  
 Al llamar al método <xref:System.Data.DataSet.WriteXml%2A> se envían los datos con formato XML a un archivo que especifica.  
  
### Para guardar los datos de un conjunto de datos como XML en una variable  
  
-   El método <xref:System.Data.DataSet.GetXml%2A> devuelve <xref:System.String>, así que declare una variable de tipo <xref:System.String> y asígnele los resultados del método <xref:System.Data.DataSet.GetXml%2A>.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### Para guardar los datos de un conjunto de datos como XML en un archivo  
  
-   El método <xref:System.Data.DataSet.WriteXml%2A> tiene varias sobrecargas.  El código siguiente muestra cómo guardar los datos en un archivo; declare una variable y asígnele una ruta de acceso válida donde guardar el archivo.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## Vea también  
 [DataSets, DataTables y DataViews](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Herramientas XML en Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)