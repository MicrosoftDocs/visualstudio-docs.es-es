---
title: soluciones de Outlook
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b27f874766853fb5239c96ec178233935484d1b
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551485"
---
# <a name="outlook-solutions"></a>soluciones de Outlook
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Outlook. Puede usar los complementos de VSTO para automatizar Outlook, ampliar las características de Outlook o personalizar la interfaz de usuario (UI) de Outlook. Para obtener más información sobre los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Crear un proyecto de complemento de VSTO para Outlook
 Crear proyectos de Outlook mediante la plantilla de proyecto **Complemento de Outlook** en el cuadro de diálogo **Nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.

 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, consulte [cómo: Cree proyectos de Office en Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio. Para obtener más información acerca de las plantillas de proyecto, consulte [información general](../vsto/office-project-templates-overview.md)sobre las plantillas de proyecto de Office.

## <a name="outlook-vsto-add-in-programming-model"></a>Modelo de programación de complementos de VSTO de Outlook
 Al crear un proyecto de complemento de VSTO de Outlook, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Outlook en el complemento de VSTO.

 Para obtener más información sobre `ThisAddIn` la clase y otras características que puede usar en un complemento de VSTO, consulte [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizar Outlook mediante el modelo de objetos de Outlook
 El modelo de objetos de Outlook expone muchos tipos que puede usar para automatizar Outlook. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:

- Crear y enviar mensajes de correo electrónico mediante programación.

- Enviar nuevas convocatorias de reunión.

- Buscar elementos en las carpetas de Outlook.

  Para obtener más información, vea [información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personalización de la interfaz de usuario de una aplicación de Outlook

|Tarea|Para obtener más información|
|----------|--------------------------|
|Agregar pestañas personalizadas a la cinta de un Inspector de Outlook.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|
|Agregar grupos personalizados a una pestaña integrada en un Inspector de Outlook.|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|
|Agregar un panel de tareas personalizado que aparezca en un Inspector de Outlook|[Paneles de tareas personalizados](../vsto/custom-task-panes.md).|
|Agregar un área de formulario que amplíe o sustituya los formularios de Outlook existentes.|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|

 Para obtener más información sobre cómo personalizar la interfaz de usuario de Outlook y otras aplicaciones Microsoft Office, consulte Personalización de la [interfaz de usuario de Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>Temas relacionados

|Título|DESCRIPCIÓN|
|-----------|-----------------|
|[Información general del modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)|Proporciona información general sobre los objetos que proporciona el modelo de objetos de Outlook.|
|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|Explica las herramientas que proporciona Visual Studio que facilitan el diseño, el desarrollo y la depuración de las áreas de formulario.|
|[Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Muestra cómo crear un complemento de VSTO para Microsoft Office Outlook.|
|[Outlook 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Área de MSDN Library donde podrá encontrar artículos y documentación de referencia sobre el desarrollo de soluciones de Outlook (no específicos del desarrollo de Office mediante Visual Studio).|
