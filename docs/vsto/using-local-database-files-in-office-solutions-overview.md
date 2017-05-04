---
title: "Informaci&#243;n general sobre el uso de archivos de bases de datos locales en soluciones de Office | Microsoft Docs"
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
  - "datos [desarrollo de Office en Visual Studio], locales"
  - "datos locales [desarrollo de Office en Visual Studio]"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], datos"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Informaci&#243;n general sobre el uso de archivos de bases de datos locales en soluciones de Office
  Puede incluir un archivo de base de datos, como un archivo de SQL Server Express \(.mdf\) o de Microsoft Office Access \(.mdb\), en la solución de Office.  Esto permite a los usuarios finales mantener una base de datos local en situaciones donde no se requiere una base centralizada, por ejemplo, en una solución de inventario local utilizada en un único equipo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Importar el archivo de base de datos a un proyecto  
 Para importar, utilice el **Asistente para la configuración de orígenes de datos** para crear un origen de datos basado en el archivo de base de datos.  El asistente agregará al proyecto el archivo de base de datos y un conjunto de datos con tipo.  
  
## Implementar el archivo de base de datos  
 El **Asistente para la configuración de orígenes de datos** utiliza una ruta de acceso relativa para crear conexiones con el archivo de base de datos local.  Esto le permite copiar la solución de un equipo en otro si mantiene las posiciones relativas de los archivos.  
  
 Si se implementa la solución en un servidor y, a continuación, se distribuye el documento a cada usuario final, también se deberá distribuir manualmente el archivo de base de datos e instalarlo en la misma posición relativa del documento.  Esto implica que el usuario final no podrá mover el documento a una nueva ubicación del equipo a menos que también mueva el archivo de base de datos.  
  
## Archivos de base de datos locales y almacenamiento en caché del conjunto de datos  
 En soluciones de nivel de documento para Microsoft Office Excel y Microsoft Office Word, puede almacenar en memoria caché conjuntos de datos del documento marcando la instancia del conjunto de datos con el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Cuando se agrega un archivo de base de datos a un proyecto mediante el **Asistente para la configuración de orígenes de datos**, se agrega automáticamente al proyecto un conjunto de datos con tipo.  Es raro que deba aplicarse el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> en este conjunto de datos, puesto que los datos ya son locales al estar el equipo del usuario.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Almacenar datos en caché](../vsto/caching-data.md)  
  
  