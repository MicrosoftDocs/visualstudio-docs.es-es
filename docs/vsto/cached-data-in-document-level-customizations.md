---
title: "Datos almacenados en cach&#233; en las personalizaciones de nivel de documento"
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
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], acerca del almacenamiento de datos en caché"
  - "datos [desarrollo de Office en Visual Studio], caché"
  - "datos [desarrollo de Office en Visual Studio], soluciones de nivel de documento"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], acerca del almacenamiento de datos en caché"
  - "islas de datos [desarrollo de Office en Visual Studio]"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], modelo de datos"
  - "ver [desarrollo de Office en Visual Studio]"
ms.assetid: 84808462-2c5d-4dc8-ab69-491d492b4a51
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Datos almacenados en cach&#233; en las personalizaciones de nivel de documento
  Uno de los principales objetivos de las personalizaciones de nivel de documento consiste en separar los datos de la vista en los documentos de Office.  Los datos se refieren a la información que se almacena en el documento, incluidos números y texto.  Con el término vista se hace referencia a la interfaz de usuario y al modelo de objetos de Microsoft Office Word y Microsoft Office Excel.  
  
 Visual Studio separa los datos de la vista en las personalizaciones de nivel de documento ya que permite incrustar los datos como una *isla de datos*, también denominada *memoria caché de datos*.  Puede leer o modificar los datos directamente sin iniciar Word ni Excel.  Esto resulta útil si necesita modificar datos de documentos incluidos en un servidor que no tiene Microsoft Office instalado.  Word y Excel se han diseñado para su uso en entornos de cliente, no para su ejecución en un servidor.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Para obtener más información sobre las personalizaciones de nivel de documento, vea [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Modelo de programación de los datos almacenados en memoria caché  
 La isla de datos puede contener cualquier objeto de la solución que cumpla ciertos requisitos.  Entre ellos se incluyen los objetos <xref:System.Data.DataSet>, los objetos <xref:System.Data.DataTable> y cualquier otro objeto que la clase <xref:System.Xml.Serialization.XmlSerializer> pueda serializar.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).  
  
 Para proporcionar la vista para los datos almacenados en memoria caché, puede enlazar los controles de formularios Windows Forms y los *controles host* del documento a los objetos de la isla de datos.  El enlace de datos entre la isla de datos y los controles enlazados a datos mantiene a ambos sincronizados.  También puede agregar a los datos código de validación independiente de los controles.  Para obtener más información, vea [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 Los controles host son versiones extendidas de objetos nativos de los modelos de objetos de Word y Excel.  A diferencia de los objetos nativos, los controles host se pueden enlazar directamente a los objetos de datos administrados.  Para obtener más información, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md) y [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
## Obtener acceso a datos almacenados en la memoria caché del servidor  
 Para tener acceso a los datos almacenados en la memoria caché de un documento, puede utilizar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>.  Esta clase forma parte del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y se puede utilizar en un servidor sin ejecutar Excel o Word.  Cuando el usuario abre el documento después de modificar los datos almacenados en la memoria caché, cualquier control enlazado a los datos se sincroniza automáticamente con los cambios y el usuario recibe los datos actualizados.  Para obtener más información, vea [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 No es necesario ejecutar Excel ni Word para escribir datos en el servidor, sólo para verlos en los equipos cliente.  Ni siquiera es necesario que Excel y Word estén instalados en el servidor.  Así se consigue una mayor escalabilidad y la capacidad de procesar por lotes rápidamente los documentos que contienen islas de datos.  
  
## Almacenamiento de datos en memoria caché para su uso sin conexión  
 El almacenamiento de datos en la isla de datos permite los escenarios sin conexión.  Cuando un usuario abre por primera vez un documento o solicita el documento del servidor, la isla de datos se rellena con los datos más recientes.  La isla de datos se almacena en la memoria caché del documento y, de esa forma, está disponible sin conexión.  El usuario \(y el código\) pueden manipular los datos, incluso aunque no haya disponible ninguna conexión activa.  Cuando el usuario vuelva a establecer conexión, los cambios realizados en los datos pueden propagarse en el origen de datos del servidor.  
  
## Comparación entre los datos almacenados en la memoria caché y los elementos XML personalizados  
 Los elementos XML personalizados partes se introdujeron en Microsoft Office System 2007 como una manera de almacenar elementos arbitrarios de XML en un documento.  Si bien los elementos XML personalizados son útiles en muchos de los mismos escenarios que la memoria caché de datos, hay algunas diferencias entre la isla de datos y los elementos XML personalizados.  Para obtener más información sobre los elementos XML personalizados, vea [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
 En la tabla siguiente se enumeran algunas de las diferencias y similitudes.  
  
||Caché de datos|Elementos XML personalizados|  
|-|--------------------|----------------------------------|  
|¿Qué aplicaciones de Office pueden utilizarlos?|Personalizaciones de nivel de documento para las aplicaciones siguientes:<br /><br /> -   Excel<br />-   Word|Soluciones de nivel de documento y de nivel de aplicación para las aplicaciones siguientes:<br /><br /> -   Excel<br />-   PowerPoint<br />-   Word|  
|¿Qué tipos de datos se pueden almacenar?|Cualquier objeto público del ensamblado de personalización que cumpla ciertos requisitos.  Para obtener más información, vea [Almacenar datos en caché](../vsto/caching-data.md).|Cualquier dato XML.|  
|¿Se puede tener acceso a los datos sin iniciar las aplicaciones de Microsoft Office?|Sí, mediante la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> proporcionada por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|Sí, mediante las clases del espacio de nombres <xref:System.IO.Packaging> o mediante el SDK del formato Open XML.|  
  
## Vea también  
 [Datos en las soluciones de Office](../vsto/data-in-office-solutions.md)   
 [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)  
  
  