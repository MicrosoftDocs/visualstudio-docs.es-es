---
title: soluciones de Outlook
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07a7917e1c33da2151abaeba7dc4f684ca0d067b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572951"
---
# <a name="outlook-solutions"></a>soluciones de Outlook
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Outlook. Puede usar los complementos de VSTO para automatizar Outlook, ampliar las características de Outlook o personalizar la interfaz de usuario (UI) de Outlook. Para obtener más información sobre los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Crear un proyecto VSTO de Outlook en:  
 Crear proyectos de Outlook mediante la plantilla de proyecto **Complemento de Outlook** en el cuadro de diálogo **Nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Complemento de VSTO programación modelo de Outlook  
 Al crear un proyecto de complemento de VSTO de Outlook, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Outlook en el complemento de VSTO.  
  
 Para obtener más información sobre la `ThisAddIn` clase y otras características que puede usar en un complemento de VSTO, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Automatizar Outlook mediante el modelo de objetos de Outlook  
 El modelo de objetos de Outlook expone muchos tipos que puede usar para automatizar Outlook. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:  
  
-   Crear y enviar mensajes de correo electrónico mediante programación.  
  
-   Enviar nuevas convocatorias de reunión.  
  
-   Buscar elementos en las carpetas de Outlook.  
  
 Para obtener más información, consulte [información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Personalizar la interfaz de usuario de una aplicación de Outlook  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Agregar pestañas personalizadas a la cinta de un Inspector de Outlook.|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregar grupos personalizados a una pestaña integrada en un Inspector de Outlook.|[Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|  
|Agregar un panel de tareas personalizado que aparezca en un Inspector de Outlook|[Paneles de tareas personalizados](../vsto/custom-task-panes.md).|  
|Agregar un área de formulario que amplíe o sustituya los formularios de Outlook existentes.|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Para obtener más información acerca de cómo personalizar la interfaz de usuario de Outlook y otras aplicaciones de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)|Proporciona información general sobre los objetos que proporciona el modelo de objetos de Outlook.|  
|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|Explica las herramientas que proporciona Visual Studio que facilitan el diseño, el desarrollo y la depuración de las áreas de formulario.|  
|[Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Muestra cómo crear un complemento de VSTO para Microsoft Office Outlook.|  
|[Outlook 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Área de MSDN Library donde podrá encontrar artículos y documentación de referencia sobre el desarrollo de soluciones de Outlook (no específicos del desarrollo de Office mediante Visual Studio).|  
  
  