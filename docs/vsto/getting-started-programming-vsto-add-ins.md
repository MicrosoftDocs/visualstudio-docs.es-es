---
title: Introducción a la programación de complementos de VSTO
description: Obtenga información sobre cómo puede usar complementos de VSTO para automatizar Microsoft Office aplicaciones, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848297"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introducción a la programación de complementos de VSTO
> [!IMPORTANT]
> VSTO se basa en el [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Los complementos COM también se pueden escribir con el .NET Framework. Los complementos de Office no se pueden crear con .NET Core y [.NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), las versiones más recientes de .NET. Esto se debe a que .NET Core/.NET 5+ no puede funcionar junto con .NET Framework en el mismo proceso y puede provocar errores de carga de complementos. Puede seguir usando .NET Framework para escribir complementos VSTO y COM para Office. Microsoft no actualizará VSTO ni la plataforma de complementos COM para usar .NET Core o .NET 5+. Puede aprovechar las ventajas de .NET Core y .NET 5+, incluido ASP.NET Core, para crear el lado servidor de los complementos [web de Office](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins).

  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación. Para obtener información sobre cómo se comparan los complementos de VSTO con otros tipos de soluciones de Office que se pueden crear mediante Visual Studio, vea Introducción al desarrollo de soluciones de [Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Creación de proyectos de complemento de VSTO
 Cree proyectos de complemento de VSTO mediante una de las plantillas de proyecto del complemento de VSTO en el **cuadro de diálogo** Nuevo proyecto. Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto. Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.

 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, vea [Cómo:](../vsto/how-to-create-office-projects-in-visual-studio.md)Crear proyectos de Office en Visual Studio . Para obtener más información sobre las plantillas de proyecto, vea Introducción [a las plantillas de proyecto de Office.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Desarrollo de proyectos de complemento de VSTO
 Al crear un proyecto de complemento de VSTO, Visual Studio crea automáticamente un archivo de código *ThisAddIn.vb* (en ) o [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (en C#). Este archivo contiene la `ThisAddIn` clase , que proporciona la base para el complemento de VSTO. Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación. Para obtener más información, [vea Program VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatización de aplicaciones mediante los modelos de objetos
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO. Puede usar estos tipos para automatizar la aplicación. Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación. Para obtener más información sobre cómo acceder al modelo de objetos de la aplicación host en el código, vea [Program VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:

- [Introducción al modelo de objetos de Excel](../vsto/excel-object-model-overview.md)

- [Introducción al modelo de objetos de Word](../vsto/word-object-model-overview.md)

- [Introducción al modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)

- [Soluciones de InfoPath](../vsto/infopath-solutions.md)

- [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluciones de proyecto](../vsto/project-solutions.md)

- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalización de la interfaz de usuario de las aplicaciones
 Hay varias maneras diferentes de personalizar la interfaz de usuario de la aplicación host mediante un complemento de VSTO:

- Para Excel y Word, puede agregar controles administrados a documentos. Para obtener más información, vea Extender documentos de Word y libros de Excel en [complementos vsTO en tiempo de ejecución.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

- Puede personalizar la cinta de opciones si la aplicación lo admite. Para obtener más información, vea Información [general de la cinta de opciones.](../vsto/ribbon-overview.md)

- Puede crear un panel de tareas personalizado si la aplicación lo admite. Para obtener más información, vea [Paneles de tareas personalizados.](../vsto/custom-task-panes.md)

- Para Outlook, puede crear un área de formulario personalizada. Para obtener más información, vea [Crear regiones de formulario de Outlook.](../vsto/creating-outlook-form-regions.md)

- Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.

  Para obtener más información sobre cómo personalizar la interfaz de usuario de Microsoft Office, vea Personalización de la interfaz [de usuario de Office.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Pasos siguientes
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:

- [Tutorial: Creación del primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Tutorial: Creación de la primera aplicación vsto Add-In para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Tutorial: Creación del primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Tutorial: Creación del primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Tutorial: Creación del primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.

  Para obtener una lista de temas que le ayudarán a realizar algunas de las tareas comunes de los proyectos de Office, consulte [Tareas comunes en la programación de Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Consulte también
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introducción al &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Escritura de código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Programas de complementos VSTO](../vsto/programming-vsto-add-ins.md)
