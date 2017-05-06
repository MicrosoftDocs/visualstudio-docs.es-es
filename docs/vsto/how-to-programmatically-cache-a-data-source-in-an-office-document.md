---
title: "C&#243;mo: Almacenar en memoria cach&#233; un origen de datos de un documento de Office mediante programaci&#243;n"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "datos [desarrollo de Office en Visual Studio], almacenar en caché"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], mediante programación"
  - "conjuntos de datos [desarrollo de Office en Visual Studio], almacenar en caché"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], datos"
  - "StartCaching (método)"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Almacenar en memoria cach&#233; un origen de datos de un documento de Office mediante programaci&#243;n
  Se puede agregar mediante programación un objeto de datos a la caché de datos de un documento llamando al método `StartCaching` de un elemento de host, como <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> o <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Quite un objeto de datos de la memoria caché de datos llamando al método `StopCaching` de un elemento host.  
  
 Los métodos `StartCaching` y `StopCaching` son privados pero aparecen en IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Cuando se utiliza el método `StartCaching` para agregar un objeto de datos a la caché de datos, no es necesario declarar el objeto de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Sin embargo, el objeto de datos debe cumplir ciertos requisitos para poder agregarse a la caché de datos.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
### Para almacenar en memoria caché un objeto de datos mediante programación  
  
1.  Declare el objeto de datos en el nivel de clase, no dentro de un método.  Este ejemplo supone que está declarando un objeto <xref:System.Data.DataSet> denominado `dataSet1` que desea almacenar en memoria caché mediante programación.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  Cree una instancia del objeto de datos y, a continuación, llame al método `StartCaching` de la instancia del documento o la hoja de cálculo y pase el nombre del objeto de datos.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### Para dejar de almacenar en memoria caché un objeto de datos  
  
1.  Llame al método `StopCaching` de la instancia del documento o la hoja de cálculo y pase el nombre del objeto de datos.  En este ejemplo, se supone que tiene un <xref:System.Data.DataSet> denominado `dataSet1` en el que desea detener el almacenamiento en caché.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  No llame a `StopCaching` desde el controlador del evento `Shutdown` de un documento o una hoja de cálculo.  Para cuando se inicie el evento `Shutdown`, será demasiado tarde para modificar la caché de datos.  Para obtener más información sobre el evento `Shutdown`, vea [Eventos de los proyectos de Office](../vsto/events-in-office-projects.md).  
  
## Vea también  
 [Almacenar datos en caché](../vsto/caching-data.md)   
 [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Guardar datos](../data-tools/saving-data.md)  
  
  