---
title: 'Excel: Introducción a la programación de personalizaciones de nivel de documento'
titleSuffix: ''
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
ms.openlocfilehash: cb3b27a4020e2b8947ca0868bb46b5945b5d89de
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585685"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Introducción a la programación de personalizaciones de nivel de documento para Excel
  Si acaba de empezar a crear personalizaciones de nivel de documento para Microsoft Office Excel con Visual Studio, aquí tiene todo lo que necesita saber.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Comprender cómo funcionan las personalizaciones de nivel de documento para Excel
 Una personalización de nivel de documento para Excel se basa en un único libro. Para empezar a usar la personalización, el usuario final abre el libro o crea el libro a partir de una plantilla de Excel. Los eventos del libro, como por ejemplo escribir en celdas o hacer clic en botones y elementos de menú, pueden llamar a métodos de control de eventos en el ensamblado. Cuando se cierra el libro, las características proporcionadas por la personalización ya no están disponibles en Excel, solo en el documento que los contiene.

 Para obtener más información, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Crear proyectos de nivel de documento para Excel
 Para crear una personalización de nivel de documento para Excel, use el libro de Excel o la plantilla de proyecto de plantilla de Excel en el cuadro de diálogo **nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.

 Para obtener más información sobre cómo crear un proyecto de nivel de documento para Excel, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, consulte [información general](../vsto/office-project-templates-overview.md)sobre las plantillas de proyecto de Office.

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Programar libros de Excel mediante elementos host y controles host
 *Los elementos host* y *los controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento creadas con Visual Studio.

 Los elementos host proporcionan un punto de entrada para el código y también pueden actuar como contenedores de controles host y controles de Windows Forms. En los proyectos de nivel de documento para Excel, estos elementos host se representan mediante las `ThisWorkbook` clases,, `Sheet1` `Sheet2` y `Sheet3` .

 Los controles host se basan en objetos nativos de Excel, como los objetos de lista y los intervalos. Los controles host proporcionan una funcionalidad similar a los objetos nativos de Excel, pero también tienen nuevos eventos, compatibilidad con el diseñador y capacidad de enlace de datos. Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que facilita la referencia a objetos específicos directamente en el código sin tener que navegar por el modelo de objetos de Excel.

 Para obtener más información, vea los temas siguientes:

- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)

- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)

- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Personalización de la interfaz de usuario de Excel
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario (UI) de la aplicación de Office para proporcionar a los usuarios una manera de interactuar con la solución. Hay muchas maneras en las que puede modificar la interfaz de usuario de Excel mediante una personalización de nivel de documento. Por ejemplo, puede Agregar controles a la cinta de opciones o puede mostrar un panel de acciones. Para obtener más información, consulte [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

 También puede abrir el libro que está asociado al proyecto directamente en Visual Studio. Cuando el libro está abierto en Visual Studio, puede modificar el libro mediante la interfaz de usuario de Excel. También puede utilizar el libro como una superficie de diseño, lo que le permite arrastrar controles a hojas de cálculo. Para obtener más información, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Usar el enlace de datos
 Los controles host también están en la lista de controles que puede arrastrar desde la ventana **orígenes de datos** . La adición de controles host de esta manera los enlaza automáticamente al origen de datos que se configura mediante la ventana de. Sin escribir ningún código, puede mostrar datos de bases de datos, servicios web y objetos comerciales. Para obtener más información, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Pasos siguientes
 Para obtener información sobre cómo crear una personalización de nivel de documento para Excel, vea [Tutorial: crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). En este tutorial se presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento de Excel.

 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes de los proyectos de Excel, vea [tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vea también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Soluciones de Excel](../vsto/excel-solutions.md)
- [Tutorial: crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Tutoriales de uso de Excel](../vsto/walkthroughs-using-excel.md)
- [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
