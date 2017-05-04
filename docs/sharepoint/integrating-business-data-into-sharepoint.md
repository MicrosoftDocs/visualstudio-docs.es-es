---
title: "Integrar Datos profesionales en SharePoint | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar datos"
  - "BDC [desarrollo de SharePoint en Visual Studio], datos profesionales"
  - "BDC [desarrollo de SharePoint en Visual Studio], crear un modelo"
  - "BDC [desarrollo de SharePoint en Visual Studio], datos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar datos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], datos profesionales"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], crear un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], datos"
ms.assetid: e092e3d6-2c5f-4060-ae86-d37db8967559
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Integrar Datos profesionales en SharePoint
  Puede integrar datos profesionales en SharePoint.  Los datos profesionales pueden proceder de las aplicaciones de servidor back\-end, como [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel y SAP o un servicio Web.  Los usuarios pueden ver, agregar, actualizar o eliminar los datos profesionales utilizando listas externas o elementos web de datos profesionales en SharePoint. Los usuarios también pueden obtener acceso a estos datos sin conexión en una aplicación de Microsoft Office como Microsoft Outlook.  Para obtener más información, vea[Donde puede mostrar datos externos](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Para integrar datos en SharePoint, cree un modelo para el servicio Conectividad a datos profesionales \(BDC\).  El servicio BDC es una aplicación en SharePoint que almacena información sobre datos de aplicaciones empresariales.  Para obtener más información, vea [Servicio de \(BDC\) de conectividad a datos profesionales](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## Los modelos en Visual Studio  
 Los modelos en Visual Studio permiten escribir código personalizado para recuperar y actualizar datos de los orígenes de datos back\-end.  También puede agregar datos de varios orígenes de datos.  Por ejemplo, puede mostrar una lista de clientes que contenga los datos de una base de datos de [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] y un servicio Web.  
  
 También puede importar modelos que ya se implementan en SharePoint.  Después de importar un modelo, puede agregar código personalizado o simplemente usar Visual Studio para empaquetar e implementar el modelo en varias granjas de servidores de SharePoint.  Para obtener más información, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Diseñar un modelo en Visual Studio  
 Puede diseñar un modelo utilizando un diseñador y varias ventanas de herramientas.  Cuando diseña el modelo, Visual Studio genera el XML modelo.  Para obtener más información, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modelo contiene entidades y métodos.  
  
### Entidades  
 Una entidad describe una colección de campos.  Por ejemplo, una entidad puede representar una tabla en una base de datos.  Una entidad aparece como un tipo de contenido externo en SharePoint.  Para obtener más información sobre los tipos de contenido externo, vea [¿Cuáles son los tipos de contenido externo?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### Métodos  
 Un método permite a los consumidores de un tipo de contenido externo realizar una acción con los campos de una entidad.  Por ejemplo, un método Updater podría permitir a los usuarios cambiar la dirección y fecha de nacimiento de un cliente donde `Address` y `BirthDate` son campos de la entidad `Customer`.  
  
 Visual Studio genera un archivo de código del servicio para cada entidad del modelo.  Cuando agregue un método al modelo, Visual Studio genera un método correspondiente en el archivo de código del servicio.  Agregue código a cada método para realizar la tarea adecuada.  Por ejemplo, si agrega un método Creator al modelo, Visual Studio genera un método Creator en el archivo de código del servicio.  El servicio BDC llama a este método cuando un usuario hace clic en el botón **Nuevo elemento** en una lista que está basada en el modelo.  Por consiguiente, agregue el código al método Creator que agrega los nuevos datos a un origen de datos.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)|Muestra cómo crear un nuevo modelo o importa un modelo que se exporta de SharePoint.|  
|[Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)|Explica cómo diseñar los elementos de un modelo utilizando las herramientas de diseño de Visual Studio.|  
|[Cuándo utilizar SharePoint Designer con Visual Studio cuando compila las Soluciones Mediante BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Le ayuda a decidir si debe usar Visual Studio o SharePoint Designer para crear un modelo para el BDC.|  
  
  