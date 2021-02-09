---
title: Introducción a la programación de complementos de VSTO
description: Obtenga información sobre cómo puede usar los complementos de VSTO para automatizar Microsoft Office aplicaciones, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
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
ms.openlocfilehash: d7e6f891f8485d4e08734e59a11db8018eaa07b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860642"
---
# <a name="get-started-programming-vsto-add-ins"></a>Introducción a la programación de complementos de VSTO
  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación. Para obtener información sobre cómo se comparan los complementos de VSTO con otros tipos de soluciones de Office que puede crear con Visual Studio, vea [información general sobre el desarrollo de soluciones de office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Crear proyectos de complemento de VSTO
 Cree proyectos de complemento de VSTO mediante el uso de una de las plantillas de proyecto de complemento de VSTO en el cuadro de diálogo **nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto. Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.

 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, vea [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, consulte [información general](../vsto/office-project-templates-overview.md)sobre las plantillas de proyecto de Office.

## <a name="develop-vsto-add-in-projects"></a>Desarrollar proyectos de complementos de VSTO
 Al crear un proyecto de complemento de VSTO, Visual Studio crea automáticamente un archivo de código *ThisAddIn. VB* (en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) o *ThisAddIn.CS* (en C#). Este archivo contiene la `ThisAddIn` clase, que proporciona la base para el complemento de VSTO. Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación. Para obtener más información, vea [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatizar aplicaciones mediante los modelos de objetos
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO. Puede usar estos tipos para automatizar la aplicación. Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación. Para obtener más información sobre cómo obtener acceso al modelo de objetos de la aplicación host en el código, vea [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:

- [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md)

- [Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)

- [Información general del modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)

- [Soluciones de InfoPath](../vsto/infopath-solutions.md)

- [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)

- [Soluciones de proyecto](../vsto/project-solutions.md)

- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Personalización de la interfaz de usuario de las aplicaciones
 Hay varias maneras de personalizar la interfaz de usuario de la aplicación host mediante un complemento de VSTO:

- Para Excel y Word, puede agregar controles administrados a documentos. Para obtener más información, vea [ampliar documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Puede personalizar la cinta de opciones si la aplicación lo admite. Para obtener más información, vea [información general sobre la cinta](../vsto/ribbon-overview.md)de opciones.

- Puede crear un panel de tareas personalizado si la aplicación lo admite. Para obtener más información, consulte [paneles de tareas personalizados](../vsto/custom-task-panes.md).

- Para Outlook, puede crear un área de formulario personalizada. Para obtener más información, consulte [crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).

- Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.

  Para obtener más información sobre cómo personalizar la interfaz de usuario de Microsoft Office aplicaciones, consulte [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

## <a name="next-steps"></a>Pasos siguientes
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:

- [Tutorial: crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Tutorial: creación de la primera Add-In de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Tutorial: crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Tutorial: crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Tutorial: crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.

  Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes de los proyectos de Office, vea [tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Vea también
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
