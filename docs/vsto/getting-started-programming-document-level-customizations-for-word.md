---
title: Introducción a la programación de personalizaciones de nivel de documento para Word
description: Obtenga información sobre lo que necesita saber para empezar a crear personalizaciones de nivel de documento para Microsoft Office Word con Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9420ab02b5f402dd39e5ca1713b911a10932dfb
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845185"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Introducción a la programación de personalizaciones de nivel de documento para Word
  Si acaba de empezar a crear personalizaciones de nivel de documento para Microsoft Office Word con Visual Studio, aquí tiene todo lo que necesita saber.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Comprender cómo funcionan las personalizaciones de nivel de documento para Word
 Cada personalización de Word que se crea se basa en un solo documento. Para empezar a usar la personalización, el usuario final abre el documento o crea el documento a partir de una plantilla de Word. Los eventos del documento, por ejemplo, mover el cursor a áreas específicas o hacer clic en botones y elementos de menú, pueden llamar a métodos de control de eventos en el ensamblado. Cuando se cierra el documento, las características proporcionadas por la personalización ya no están disponibles en Word.

 Para obtener más información, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-word"></a>Crear proyectos de nivel de documento para Word
 Para crear una personalización de nivel de documento para Word, use la plantilla de proyecto de documento de Word o de plantilla de Word en el cuadro de diálogo **nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.

 Para obtener más información sobre cómo crear un proyecto de nivel de documento para Word, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, consulte [información general](../vsto/office-project-templates-overview.md)sobre las plantillas de proyecto de Office.

## <a name="program-word-documents-by-using-host-items-host-controls"></a>Programar documentos de Word mediante controles host de elementos host
 *Los elementos host* y *los controles host* son clases que proporcionan el modelo de programación para las personalizaciones de nivel de documento.

 Los elementos host proporcionan un punto de entrada para el código y también pueden actuar como contenedores de controles host y controles de Windows Forms. En los proyectos de nivel de documento de Word, la clase representa el elemento host `ThisDocument` .

 Los controles host se basan en objetos nativos de Word, como controles de contenido, marcadores y nodos XML. Los controles host proporcionan una funcionalidad similar a los objetos nativos de Word, pero también tienen nuevos eventos, compatibilidad con el diseñador y capacidad de enlace de datos. Aparecen como objetos de primera clase en el código del proyecto y en IntelliSense, lo que facilita la referencia a objetos específicos directamente en el código sin tener que navegar por el modelo de objetos de Word.

 Para obtener más información, vea los temas siguientes:

- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)

- [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)

- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Personalización de la interfaz de usuario de Word
 La mayoría de las soluciones de Microsoft Office modifican la interfaz de usuario (UI) de la aplicación de Office para proporcionar a los usuarios una manera de interactuar con la solución. Hay muchas maneras en las que puede modificar la interfaz de usuario de Word mediante una personalización de nivel de documento. Por ejemplo, puede Agregar controles a la cinta de opciones y puede mostrar un panel de acciones. Para obtener más información, consulte [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

 También puede abrir el documento que está asociado al proyecto directamente en Visual Studio. Cuando el documento se abre en Visual Studio, puede modificarlo mediante la interfaz de usuario de Word. También puede utilizar el documento como una superficie de diseño, lo que le permite arrastrar controles hacia él. Para obtener más información, vea [proyectos de Office en el entorno de Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="bind-controls-to-data"></a>Enlazar controles a datos
 Los controles de contenido y el <xref:Microsoft.Office.Tools.Word.Bookmark> control están en la lista de controles que puede arrastrar desde la ventana **orígenes de datos** . La adición de controles de contenido y marcadores de esta manera los enlaza automáticamente al origen de datos que se configura mediante la ventana de. Sin escribir ningún código, puede mostrar datos de bases de datos, servicios y objetos de negocio. Para obtener más información, vea [enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Pasos siguientes
 Para obtener información sobre cómo crear una personalización de nivel de documento para Word, vea [Tutorial: crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). En este tutorial se presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación para las personalizaciones de nivel de documento de Word.

 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes de los proyectos de Word, vea [tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vea también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Personalizaciones de nivel de documento de programa](../vsto/programming-document-level-customizations.md)
- [Soluciones de Word](../vsto/word-solutions.md)
- [Tutorial: crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Tutoriales de uso de Word](../vsto/walkthroughs-using-word.md)
- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
