---
title: Extender el sistema de proyectos de SharePoint | Microsoft Docs
description: Extienda el sistema de proyectos de SharePoint. Obtenga información acerca de cómo extender el sistema de proyectos de SharePoint. Comprender las tareas comunes de desarrollo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5a81fef67cc6816f16a074494005a61d647abeab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889686"
---
# <a name="extend-the-sharepoint-project-system"></a>Extensión del sistema de proyectos de SharePoint
  Puede crear soluciones de SharePoint mediante un conjunto de plantillas de proyecto y plantillas de elemento en Visual Studio. Estas plantillas cumplen los requisitos de muchos escenarios de desarrollo, pero es posible que Descubra algunos casos en los que no proporcionan la funcionalidad que necesita. En estos casos, puede extender el sistema de proyectos de SharePoint.

## <a name="overview-of-the-sharepoint-project-system"></a>Información general sobre el sistema de proyectos de SharePoint
 El sistema de proyectos de SharePoint se basa en el componente fundamental de *los elementos de proyecto de SharePoint*. Un elemento de proyecto de SharePoint representa una única personalización de SharePoint, como una definición de lista, un elemento Web o un tipo de contenido.

 Un proyecto de SharePoint es un proyecto de Visual Studio que incluye uno o más elementos de proyecto de SharePoint. Los proyectos de SharePoint también contienen componentes adicionales que definen cómo se agrupan los elementos de proyecto en características y paquetes para la implementación.

 Para obtener más información sobre el contenido de los elementos de proyecto de SharePoint y los proyectos de SharePoint, vea [crear plantillas de elemento y plantillas de proyecto para los elementos de proyecto de SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>Cómo extender el sistema de proyectos de SharePoint
 Puede extender el sistema de proyectos de SharePoint de las siguientes maneras:

- Definir sus propios tipos de elemento de proyecto de SharePoint y asociarlos a nuevas plantillas de elementos o plantillas de proyecto en Visual Studio. Por ejemplo, puede definir un tipo de elemento de proyecto de SharePoint para crear una acción personalizada o un campo. Para obtener más información, vea [definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Extienda los tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio. Por ejemplo, puede Agregar un elemento de menú contextual a un elemento de proyecto en **Explorador de soluciones** y personalizar el elemento de proyecto cuando un desarrollador elige el elemento de menú. Para obtener más información, vea [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).

- Extender proyectos de SharePoint. Por ejemplo, puede agregar controladores de eventos para realizar tareas concretas cuando se agregan o quitan elementos de proyectos de SharePoint. Para obtener más información, vea [extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md).

- Extienda el comportamiento de empaquetado e implementación de los elementos de proyecto de SharePoint y los proyectos de SharePoint. Por ejemplo, puede crear sus propios pasos de implementación para que se ejecuten al implementar o retirar un proyecto, o puede realizar tareas personalizadas adicionales cuando Visual Studio ejecute determinados pasos de implementación. Para obtener más información, vea [extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Tareas comunes de desarrollo
 Puede realizar las siguientes tareas comunes en las extensiones del sistema de proyectos de SharePoint:

- Guardar datos de cadena personalizados con elementos de proyecto y en varios tipos diferentes de archivos de proyecto. Para obtener más información, vea [guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- Convertir un objeto del sistema de proyectos de SharePoint en un objeto correspondiente en el modelo de objetos de automatización de Visual Studio o en el modelo de objetos de integración, o viceversa. Para obtener más información, vea [conversar entre los tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Vea también
- [Definir tipos de elementos de proyecto personalizados de SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Guardar datos en extensiones del sistema de proyectos de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Extensión de las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Conceptos y características de programación para las extensiones de herramientas de SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
