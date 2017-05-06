---
title: "Introducci&#243;n a la programaci&#243;n de personalizaciones de nivel de documento para Excel"
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
  - "proyectos de Excel [desarrollo de Office en Visual Studio], introducción"
  - "soluciones de Excel en Visual Studio"
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Introducci&#243;n a la programaci&#243;n de personalizaciones de nivel de documento para Excel
  Si ha empezado recientemente a crear personalizaciones de nivel de documento para Microsoft Office Excel con Visual Studio, esto es lo que necesita saber.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## Introducción al funcionamiento de las personalizaciones de nivel de documento para Excel  
 Una personalización de nivel de documento para Excel está basada en un solo libro.  Para empezar a utilizar la personalización, el usuario final abre el libro o lo crea a partir de una plantilla de Excel.  Los eventos del libro, como por ejemplo escribir en las celdas o hacer clic en botones y elementos de menús, pueden llamar a métodos de control de eventos del ensamblado.  Cuando se cierra el libro, las características proporcionadas por la personalización dejan de estar disponibles en excel, solo en el documento que las contiene.  
  
 Para obtener más información, vea [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## Crear proyectos de nivel de documento para Excel  
 Si desea crear una personalización de nivel de documento para Excel, utilice la plantilla de proyecto Libro de Excel o Plantilla de Excel en el cuadro de diálogo **Nuevo proyecto**.  Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.  
  
 Para obtener más información sobre cómo crear un proyecto de nivel de documento para Excel, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Para obtener más información sobre las plantillas de proyecto, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
## Programar los libros de Excel mediante elementos host y controles host  
 *Los elementos host* y *controles host* son clases que proporcionan el modelo de programación para las personalizaciones de documento\- nivel creadas mediante Visual Studio.  
  
 Los elementos host proporcionan un punto de entrada para el código, y también pueden actuar como contenedores para los controles host y controles de formularios Windows Forms.  En los proyectos de nivel de documento para Excel, estos elementos host vienen representados por las clases `ThisWorkbook`, `Sheet1`, `Sheet2` y `Sheet3`.  
  
 Los controles host se basan en objetos nativos de Excel, como objetos de lista e intervalos.  Los controles host proporcionan una funcionalidad similar a los objetos nativos de Excel, pero también tienen nuevos eventos, compatibilidad con diseñadores y capacidad de enlace de datos.  Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que facilita las referencias a objetos específicos directamente en el código sin necesidad de navegar por el modelo de objetos de Excel.  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
## Personalizar la interfaz de usuario de Excel  
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario de la aplicación de Office para proporcionar formas en las que los usuarios puedan interactuar con la solución.  Hay muchas maneras en las que se puede modificar la interfaz de usuario de Excel mediante una personalización de nivel de documento.  Por ejemplo, puede agregar controles a la cinta de opciones, o puede mostrar un panel de acciones.  Para obtener más información, vea [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 También puede abrir el libro que está asociado directamente al proyecto en Visual Studio.  Una vez abierto el libro en Visual Studio, puede modificarlo mediante la interfaz de usuario de Excel.  También puede utilizar el libro como superficie de diseño, lo que permite arrastrar los controles hasta las hojas de cálculo.  Para obtener más información, vea [Proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Utilizar enlace de datos  
 Los controles host también se encuentran en la lista de controles que se pueden arrastrar desde la ventana **Orígenes de datos**.  Al agregar controles host de esta manera, se enlazan automáticamente con el origen de datos que se configure utilizando la ventana.  Sin escribir ningún código, puede mostrar los datos de las bases de datos, servicios web, y objetos de negocios.  Para obtener más información, vea [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## Pasos siguientes  
 Para obtener información sobre cómo crear una personalización de nivel de documento para Excel, vea [Tutorial: Crear la primera personalización en el nivel del documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md).  En este tutorial se presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento para Excel.  
  
 Para obtener una lista de temas en los que se describen algunas de las tareas comunes en los proyectos de Excel, vea [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Tutorial: Crear la primera personalización en el nivel del documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
  
  