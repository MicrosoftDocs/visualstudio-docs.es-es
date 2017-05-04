---
title: "Introducci&#243;n a la programaci&#243;n de personalizaciones de nivel de documento para Word | Microsoft Docs"
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
  - "proyectos de Word [desarrollo de Office en Visual Studio], introducción"
  - "soluciones de Word en Visual Studio"
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Introducci&#243;n a la programaci&#243;n de personalizaciones de nivel de documento para Word
  Si ha empezado recientemente a crear personalizaciones de nivel de documento para Microsoft Office Word con Visual Studio, esto es lo que necesita saber.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## Introducción al funcionamiento de las personalizaciones de nivel de documento para Word  
 Cada personalización de Word que crea se basa en un documento único.  Para empezar a utilizar la personalización, el usuario final abre el documento o lo crea a partir de una plantilla de Word.  Los eventos del documento, como por ejemplo desplazar el cursor a áreas específicas o hacer clic en botones y elementos de menús, pueden llamar a métodos de control de eventos del ensamblado.  Cuando se cierra el documento, las características proporcionadas por la personalización dejan de estar disponibles en Word.  
  
 Para obtener más información, vea [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Crear proyectos de nivel de documento para Word  
 Para crear un proyecto de personalización de nivel de documento para Word, use las plantillas de proyecto Documento de Word o Plantilla de Word que están disponibles en el cuadro de diálogo **Nuevo proyecto** de Visual Studio.  Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.  
  
 Para obtener más información sobre cómo crear un proyecto de nivel de documento para Word, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Para obtener más información sobre las plantillas de proyecto, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
## Programar documentos de Word mediante elementos y controles host  
 Los *elementos host* y *controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento.  
  
 Los elementos host proporcionan un punto de entrada para el código, y también pueden actuar como contenedores para los controles host y controles de formularios Windows Forms.  En proyectos de nivel de documento para Word, la clase `ThisDocument` representa el elemento host.  
  
 Los controles host se basan en objetos nativos de Word, como controles de contenido, marcadores y nodos XML.  Los controles host proporcionan una funcionalidad similar a los objetos nativos de Word, pero también disponen de nuevos eventos, compatibilidad con diseñadores y capacidad de enlace de datos.  Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que facilita las referencias a objetos específicos directamente en el código sin necesidad de navegar por el modelo de objetos de Word.  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
## Personalizar la interfaz de usuario de Word  
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario de la aplicación de Office para proporcionar formas en las que los usuarios puedan interactuar con la solución.  Hay muchas maneras en las que se puede modificar la interfaz de usuario de Word mediante una personalización de nivel de documento.  Por ejemplo, puede agregar controles a la cinta de opciones, y puede mostrar un panel de acciones.  Para obtener más información, vea [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 También puede abrir el documento que está asociado directamente al proyecto en Visual Studio.  Una vez abierto el documento en Visual Studio, puede modificarlo mediante la interfaz de usuario de Word.  También puede utilizar el documento como superficie de diseño, lo que permite al usuario arrastrar controles hasta el mismo.  Para obtener más información, vea [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Enlazar controles a los datos  
 Los controles de contenido y el control <xref:Microsoft.Office.Tools.Word.Bookmark> se encuentran en la lista de controles que se pueden arrastrar desde la ventana **Orígenes de datos**.  Al agregar controles de contenido y marcadores de esta manera, se enlazan automáticamente con el origen de datos que se configure mediante la ventana.  Sin escribir ningún código, puede mostrar los datos contenidos en bases de datos, servicios y objetos de negocios.  Para obtener más información, vea [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Pasos siguientes  
 Para obtener información sobre cómo crear una personalización de nivel de documento para Word, vea [Tutorial: Crear la primera personalización en el nivel del documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md).  En este tutorial se presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento para Word.  
  
 Para obtener una lista de temas en los que se describen algunas de las tareas comunes en los proyectos de Word, vea [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Tutorial: Crear la primera personalización en el nivel del documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  