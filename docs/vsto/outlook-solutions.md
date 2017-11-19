---
title: Soluciones de Outlook | Documentos de Microsoft
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
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e0784662a1c48602dd8f93f5ae97c0a69192c3a5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="outlook-solutions"></a>Soluciones de Outlook
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Outlook. Puede usar los complementos de VSTO para automatizar Outlook, ampliar las características de Outlook o personalizar la interfaz de usuario (UI) de Outlook. Para obtener más información sobre los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="creating-an-outlook-vsto-add-in-project"></a>Crear un proyecto de complemento de VSTO de Outlook  
 Crear proyectos de Outlook mediante la plantilla de proyecto **Complemento de Outlook** en el cuadro de diálogo **Nuevo proyecto** . Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento de VSTO, consulte [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información acerca de las plantillas de proyecto, vea [información general de plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Modelo de programación de complementos de VSTO de Outlook  
 Al crear un proyecto de complemento de VSTO de Outlook, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Outlook en el complemento de VSTO.  
  
 Para obtener más información sobre la `ThisAddIn` clase y otras características que puede usar en un complemento de VSTO, consulte [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automating-outlook-by-using-the-outlook-object-model"></a>Automatizar Outlook mediante el modelo de objetos de Outlook  
 El modelo de objetos de Outlook expone muchos tipos que puede usar para automatizar Outlook. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:  
  
-   Crear y enviar mensajes de correo electrónico mediante programación.  
  
-   Enviar nuevas convocatorias de reunión.  
  
-   Buscar elementos en las carpetas de Outlook.  
  
 Para obtener más información, consulta [Outlook Object Model Overview](../vsto/outlook-object-model-overview.md).  
  
## <a name="customizing-the-user-interface-of-an-outlook-application"></a>Personalizar la interfaz de usuario de una aplicación de Outlook  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Agregar pestañas personalizadas a la cinta de un Inspector de Outlook.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|  
|Agregar grupos personalizados a una pestaña integrada en un Inspector de Outlook.|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|  
|Agregar un panel de tareas personalizado que aparezca en un Inspector de Outlook|[Paneles de tareas personalizados](../vsto/custom-task-panes.md).|  
|Agregar un área de formulario que amplíe o sustituya los formularios de Outlook existentes.|[Creación de áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Para obtener más información acerca de cómo personalizar la interfaz de usuario de Outlook y otras aplicaciones de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Outlook Object Model Overview](../vsto/outlook-object-model-overview.md)|Proporciona información general sobre los objetos que proporciona el modelo de objetos de Outlook.|  
|[Creación de áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|Explica las herramientas que proporciona Visual Studio que facilitan el diseño, el desarrollo y la depuración de las áreas de formulario.|  
|[Tutorial: Creación del primer complemento VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Muestra cómo crear un complemento de VSTO para Microsoft Office Outlook.|  
|[Desarrollo de Outlook 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Área de MSDN Library donde podrá encontrar artículos y documentación de referencia sobre el desarrollo de soluciones de Outlook (no específicos del desarrollo de Office mediante Visual Studio).|  
  
  