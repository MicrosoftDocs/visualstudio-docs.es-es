---
title: Extender el sistema de proyectos de SharePoint | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2a76a56eccb1d65e8b64b691d0da29e8b9d30637
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="extending-the-sharepoint-project-system"></a>Extender el sistema de proyectos de SharePoint
  Puede crear soluciones de SharePoint mediante un conjunto de plantillas de proyecto y plantillas de elementos en Visual Studio. Estas plantillas cumplen los requisitos de muchos escenarios de desarrollo, pero se pueden detectar algunos casos donde no proporcionan una funcionalidad que necesite. En estos casos, puede extender el sistema de proyecto de SharePoint.  
  
## <a name="overview-of-the-sharepoint-project-system"></a>Información general del sistema del proyecto de SharePoint  
 El sistema de proyectos de SharePoint se basa en el componente fundamental de *elementos de proyecto de SharePoint*. Un elemento de proyecto de SharePoint representa una personalización de SharePoint única, como una definición de lista, el elemento Web o el tipo de contenido.  
  
 Un proyecto de SharePoint es un proyecto de Visual Studio que incluye uno o varios elementos de proyecto de SharePoint. Proyectos de SharePoint también contienen componentes adicionales que definen cómo se agrupan los elementos de proyecto en características y paquetes para la implementación.  
  
 Para obtener más información sobre el contenido de elementos de proyecto de SharePoint y los proyectos de SharePoint, vea [crear plantillas de elementos y las plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="how-to-extend-the-sharepoint-project-system"></a>Cómo extender el sistema de proyectos de SharePoint  
 Puede extender el sistema de proyectos de SharePoint de las maneras siguientes:  
  
-   Definir sus propios tipos de elemento de proyecto de SharePoint y asociarlos con nuevas plantillas de elemento o plantillas de proyecto en Visual Studio. Por ejemplo, puede definir un tipo de elemento de proyecto de SharePoint para crear una acción personalizada o un campo. Para obtener más información, consulte [definir los tipos de elemento de proyecto de SharePoint de personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Extender tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio. Por ejemplo, puede agregar un elemento de menú contextual a un elemento de proyecto de **el Explorador de soluciones** y personalizar el elemento de proyecto cuando un programador elige el elemento de menú. Para obtener más información, consulte [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Extender los proyectos de SharePoint. Por ejemplo, puede agregar controladores de eventos para llevar a cabo tareas específicas cuando los elementos se agregan o quitan de los proyectos de SharePoint. Para obtener más información, consulte [extender los proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md).  
  
-   Extender el comportamiento de empaquetado e implementación de proyectos de SharePoint y elementos de proyecto de SharePoint. Por ejemplo, puede crear sus propios pasos de implementación que se ejecutan cuando se implementa o retracta un proyecto, o puede realizar tareas personalizadas adicionales cuando Visual Studio ejecute ciertos pasos de implementación. Para obtener más información, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## <a name="common-development-tasks"></a>Tareas comunes de desarrollo  
 Puede realizar las siguientes tareas comunes en las extensiones del sistema del proyecto de SharePoint:  
  
-   Guardar los datos de cadena personalizado con elementos de proyecto y en distintos tipos de archivos de proyecto. Para obtener más información, consulte [guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertir un objeto en el sistema de proyecto de SharePoint para un objeto correspondiente en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, o viceversa. Para obtener más información, consulte [convertir entre SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## <a name="see-also"></a>Vea también  
 [Definir tipos de elemento de proyecto personalizado de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Extensión de SharePoint de empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Conversión entre tipos de sistema de proyecto de SharePoint y otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Conceptos y características de programación para extensiones de las herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  