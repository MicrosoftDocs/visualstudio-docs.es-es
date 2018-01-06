---
title: "Introducción a la programación de personalizaciones de nivel de documento para Word | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 12265c725480324c396d59d848e5269432bb5d6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-document-level-customizations-for-word"></a>Introducción a la programación de personalizaciones de nivel de documento para Word
  Si acaba de empezar a crear personalizaciones de nivel de documento para Microsoft Office Word mediante Visual Studio, aquí es lo que necesita saber.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-word-work"></a>Descripción de las personalizaciones de nivel de documento cómo para el trabajo de Word  
 Cada personalización de Word que cree se basa en un solo documento. Para empezar a usar la personalización, el usuario final abre el documento o se crea a partir de una plantilla de Word. Eventos en el documento, por ejemplo, mueva el cursor a áreas específicas o hacer clic en botones y elementos de menú, pueden llamar a métodos de control de eventos en el ensamblado. Cuando se cierra el documento, las características proporcionadas por la personalización dejan de estar disponibles en Word.  
  
 Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-word"></a>Crear proyectos de nivel de documento para Word  
 Para crear una personalización de nivel de documento para Word, use la plantilla de proyecto de documento de Word o plantilla de Word en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.  
  
 Para obtener más información acerca de cómo crear un proyecto de nivel de documento para Word, consulte [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-word-documents-by-using-host-items-host-controls"></a>Programación de documentos de Word mediante el uso de elementos y controles Host  
 *Elementos host* y *controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento.  
  
 Elementos host proporcionan un punto de entrada para el código y también puede actúan como contenedores para los controles host y controles de formularios Windows Forms. En los proyectos de nivel de documento para Word, el elemento de host está representado por la `ThisDocument` clase.  
  
 Controles host se basan en objetos nativos de Word, como controles de contenido, marcadores y nodos XML. Controles host proporcionan una funcionalidad similar a los objetos nativos de Word, pero también tienen nuevos eventos, compatibilidad con el diseñador y capacidad de enlace de datos. Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que resulta más sencillo hacer referencia a objetos específicos directamente en el código sin tener que navegar por el modelo de objetos de Word.  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-word"></a>Personalización de la interfaz de usuario de Word  
 La mayoría de soluciones de Microsoft Office modificar la interfaz de usuario (UI) de la aplicación de Office para proporcionar alguna manera para que los usuarios interactuar con la solución. Hay muchas maneras en que puede modificar la interfaz de usuario de Word mediante una personalización de nivel de documento. Por ejemplo, puede agregar controles a la cinta de opciones, y puede mostrar un panel de acciones. Para obtener más información, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 También puede abrir el documento que está asociado al proyecto directamente en Visual Studio. Cuando el documento está abierto en Visual Studio, puede modificar el documento mediante la interfaz de usuario de Word. También puede usar el documento como una superficie de diseño, que le permite arrastrar controles en él. Para obtener más información, consulte [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="binding-controls-to-data"></a>Enlazar controles a los datos  
 Los controles de contenido y la <xref:Microsoft.Office.Tools.Word.Bookmark> control están en la lista de controles que puede arrastrar desde el **orígenes de datos** ventana. Agregar controles de contenido y marcadores de esta manera automáticamente, enlaza al origen de datos que configura mediante la ventana. Sin escribir ningún código, puede mostrar datos de bases de datos, servicios y objetos comerciales. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo crear una personalización de nivel de documento para Word, consulte [Tutorial: crear el primer nivel de documento Customization For Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). En este tutorial se presenta las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento de Word.  
  
 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Word, consulte [tareas comunes de programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programación de personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Soluciones de Word](../vsto/word-solutions.md)   
 [Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Tutoriales para Word](../vsto/walkthroughs-using-word.md)   
 [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  