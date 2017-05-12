---
title: "Almacenar datos en cach&#233;"
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
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio]"
  - "almacenamiento de datos en caché [desarrollo de Office en Visual Studio], acerca del almacenamiento de datos en caché"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Almacenar datos en cach&#233;
  Puede almacenar en la memoria caché los objetos de datos de una personalización en el nivel del documento para tener acceso a los datos sin conexión o sin abrir Microsoft Office Word ni Microsoft Office Excel.  Para almacenar un objeto en la memoria caché, el objeto debe tener un tipo de datos que cumpla ciertos requisitos.  Muchos tipos de datos comunes en .NET Framework cumplen estos requisitos, incluyendo <xref:System.String>, <xref:System.Data.DataSet> y <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Hay dos maneras de agregar un objeto a la memoria caché de datos:  
  
-   Para agregar un objeto a la memoria caché de datos una vez compilada la solución, aplique el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> a la declaración del objeto.  Para obtener más información, vea [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Para agregar mediante programación un objeto a la memoria caché en tiempo de ejecución, use el método `StartCaching` de un elemento host, como las clases `ThisDocument` o `ThisWorkbook`.  Para obtener más información, vea [Cómo: Almacenar en memoria caché un origen de datos de un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Después de agregar un objeto a la memoria caché de datos, puede obtener acceso y modificar los datos almacenados en memoria caché sin iniciar Word ni Excel.  Para obtener más información, vea [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Requisitos para almacenar objetos de datos en caché  
 Para almacenar en memoria caché un objeto de datos de la solución, el objeto debe cumplir estos requisitos:  
  
-   Debe ser un campo o una propiedad públicos de lectura y escritura de un elemento host, como las clases `ThisDocument` o `ThisWorkbook`.  
  
-   No debe ser un indizador ni otra propiedad parametrizada.  
  
 Además, el objeto de datos debe ser serializable por la clase <xref:System.Xml.Serialization.XmlSerializer>, lo que significa que el tipo del objeto debe tener estas características:  
  
-   Debe ser un tipo público.  
  
-   Debe contar con un constructor público sin parámetros.  
  
-   No deje ejecutar código que requiera privilegios de seguridad adicionales.  
  
-   Sólo debe exponer propiedades públicas de lectura y escritura \(se omitirán otras propiedades\).  
  
-   No debe exponer matrices multidimensionales \(se aceptan matrices anidadas\).  
  
-   No debe devolver interfaces de propiedades y campos.  
  
-   No implemente <xref:System.Collections.IDictionary> si es una colección.  
  
 Cuando se almacena en la memoria caché un objeto de datos, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializa el objeto en una cadena XML que se almacena en un *elemento XML personalizado* del documento.  Para obtener más información, vea [Información general sobre los elementos XML personalizados](../vsto/custom-xml-parts-overview.md).  
  
## Límites de tamaño de los datos almacenados en memoria caché  
 Hay algunos límites para la cantidad total de datos que se puede agregar a la memoria caché de datos de un documento y para el tamaño de cualquier objeto individual en dicha memoria.  Si se superan estos límites, es posible que la aplicación se cierre inesperadamente al guardar los datos en la memoria caché de datos.  
  
 Para evitar estos límites, siga estas instrucciones:  
  
-   No agregue ningún objeto mayor que 10 MB a la memoria caché de datos.  
  
-   No agregue en total más de 100 MB de datos a la memoria caché de datos en un solo documento.  
  
 Estos valores son aproximados.  Los límites exactos dependen de varios factores, como la memoria RAM disponible y el número de procesos en ejecución.  
  
## Controlar el comportamiento de objetos almacenados en memoria caché  
 Para controlar mejor el comportamiento de un objeto almacenado en la memoria caché, puede implementar la interfaz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> en el tipo del objeto almacenado en la memoria caché.  Por ejemplo, puede implementar esta interfaz si desea controlar cómo se notifica al usuario un cambio en el objeto.  Para obtener ejemplos de código en los que se muestra cómo implementar <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, vea la clase `ControlCollection` en el ejemplo Excel Dynamic Controls y el ejemplo Word Dynamic Controls que se incluyen en el tema [Ejemplos y tutoriales del desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Conservar los cambios hechos en datos almacenados en memoria caché en documentos protegidos mediante contraseña  
 Si almacena en memoria caché los objetos de datos de un documento que está protegido con una contraseña, no se guardarán los cambios que se realicen en los datos almacenados en caché.  Dichos cambios podrán guardarse si se reemplazan dos métodos.  Invalide estos métodos para quitar temporalmente la protección cuando se guarda el documento y, a continuación, vuelva a aplicar la protección una vez completada la operación de guardado.  
  
 Para obtener más información, vea [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## Evitar la pérdida de datos cuando se agregan valores nulos a la memoria caché de datos  
 Cuando se agregan objetos a la memoria caché de datos, todos los objetos deben inicializarse en un valor que no sea **null** antes de guardar y cerrar el documento.  Si algún objeto de la memoria caché tiene un valor **null** cuando se guarda y se cierra el documento, el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quitará automáticamente todos los objetos de la memoria caché de datos.  
  
 Si agrega un objeto con un valor **null** a la memoria caché de datos mediante el atributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> en tiempo de diseño, puede usar la clase <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para inicializar los objetos de la memoria caché antes de abrir el documento.  Esto es útil si desea inicializar los datos almacenados en la memoria caché en un servidor donde no está instalado Word ni Excel, antes de que un usuario final abra el documento.  Para obtener más información, vea [Acceso a datos de documentos en el servidor](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Vea también  
 [Cómo: Almacenar datos en la memoria caché para el uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Cómo: Almacenar en memoria caché un origen de datos de un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Cómo: Almacenar datos en caché en un documento protegido por contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Tutorial: Crear una relación principal-detalle utilizando un conjunto de datos almacenado en caché](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  