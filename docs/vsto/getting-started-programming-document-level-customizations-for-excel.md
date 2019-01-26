---
title: Empezar a programar personalizaciones de nivel de documento para Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 47762c781b24a31b90c75e5f8d9f0d00a6d3363d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870144"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Empezar a programar personalizaciones de nivel de documento para Excel
  Si acaba de empezar a crear personalizaciones de nivel de documento para Microsoft Office Excel mediante el uso de Visual Studio, aquí es lo que necesita saber.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprender las personalizaciones de nivel de documento cómo para el trabajo de Excel  
 Una personalización de nivel de documento para Excel se basa en un único libro. Para empezar a usar la personalización, el usuario final abre el libro o se crea a partir de una plantilla de Excel. Los eventos en el libro, por ejemplo, escribir en las celdas o al hacer clic en botones y elementos de menú, pueden llamar a métodos de control de eventos en el ensamblado. Cuando se cierra el libro, las características proporcionadas por la personalización ya no están disponibles en Excel, solo en el documento que los contenía.  
  
 Para obtener más información, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Crear proyectos de nivel de documento para Excel  
 Para crear una personalización de nivel de documento para Excel, use la plantilla de proyecto de libro de Excel o plantilla de Excel en el **nuevo proyecto** cuadro de diálogo. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.  
  
 Para obtener más información sobre cómo crear un proyecto de nivel de documento para Excel, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programar los libros de Excel mediante los elementos host y controles host  
 *Elementos host* y *controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento creadas mediante Visual Studio.  
  
 Los elementos host proporcionan un punto de entrada para el código, y puede también actúan como contenedores para los controles host y controles de formularios Windows Forms. En proyectos de nivel de documento para Excel, estos elementos se representan mediante el `ThisWorkbook`, `Sheet1`, `Sheet2`, y `Sheet3` clases.  
  
 Los controles host se basan en objetos nativos de Excel, como los objetos de lista y rangos. Los controles host proporcionan una funcionalidad similar a los objetos nativos de Excel, pero también tienen nuevos eventos, compatibilidad con el diseñador y capacidad de enlace de datos. Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que resulta más fácil hacer referencia a objetos específicos directamente en el código sin tener que navegar por el modelo de objetos de Excel.  
  
 Para obtener más información, vea los temas siguientes:  
  
-   [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)  
  
-   [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Personalizar la interfaz de usuario de Excel  
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario (UI) de la aplicación de Office para ofrecer alguna forma para que los usuarios interactuar con la solución. Hay muchas maneras en que puede modificar la interfaz de usuario de Excel mediante una personalización de nivel de documento. Por ejemplo, puede agregar controles a la cinta de opciones, o puede mostrar un panel de acciones. Para obtener más información, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
 También puede abrir el libro que está asociado directamente al proyecto en Visual Studio. Cuando el libro se abre en Visual Studio, puede modificar el libro mediante la interfaz de usuario de Excel. También puede usar el libro como una superficie de diseño, lo que permite arrastrar controles a hojas de cálculo. Para obtener más información, consulte [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Usar el enlace de datos  
 Los controles host también están en la lista de controles que se pueden arrastrar desde el **orígenes de datos** ventana. Agregar controles host de esta manera automáticamente, enlaza al origen de datos que ha configurado mediante la ventana. Sin escribir ningún código, puede mostrar datos de bases de datos, servicios web y objetos de negocios. Para obtener más información, consulte [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Pasos siguientes  
 Para obtener información sobre cómo crear una personalización de nivel de documento para Excel, vea [Tutorial: Crear la primera personalización en el nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). Este tutorial presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento de Excel.  
  
 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Excel, vea [tareas comunes de programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md)   
 [Soluciones de Excel](../vsto/excel-solutions.md)   
 [Tutorial: Crear la primera personalización en el nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Tutoriales para Excel](../vsto/walkthroughs-using-excel.md)   
 [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)  
