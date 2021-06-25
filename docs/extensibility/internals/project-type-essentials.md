---
title: Project Type Essentials | Microsoft Docs
description: Obtenga información sobre cuándo debe crear un tipo de proyecto y cuándo puede ampliar un tipo de proyecto existente mediante subtipos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 051e7b76edd4559914307459fdcbdf1b7c0b600e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903564"
---
# <a name="project-type-essentials"></a>Conceptos básicos del tipo de proyecto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] incluye varios tipos de proyecto para lenguajes como [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] también le permite crear sus propios tipos de proyecto.

 Si solo desea agregar comandos personalizados, editores o ventanas de herramientas a , puede hacerlo sin crear un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nuevo tipo de proyecto. Para obtener más información, vea los temas siguientes:

- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)

- [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md)

  Del mismo modo, si desea personalizar el comportamiento de los tipos de proyecto y proporcionados, puede hacerlo mediante [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] subtipos de proyecto. Para obtener más información, vea [Subtipos de proyecto.](../../extensibility/internals/project-subtypes.md)

  Debe crear un nuevo tipo de proyecto para los proyectos basados en un lenguaje distinto de y si desea admitir uno [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o varios de los siguientes [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] elementos:

- Build

- Implementación

- Varias configuraciones

- Control de código fuente

- Depuración

- Elementos de proyecto en Explorador de soluciones

- Cuadros **de diálogo Abrir** proyecto **o** Nuevo proyecto

- Anidamiento de proyectos

- Para obtener más información sobre las funcionalidades de los tipos de proyecto, vea lo siguiente:

- Los tipos de proyecto son objetos de un VSPackage que implementan el conjunto de interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] espera. Si usa C# para desarrollar un tipo de proyecto, las clases de proyecto de Managed Package Framework implementan automáticamente las interfaces necesarias y le permiten heredar esa implementación. Para obtener más información, [vea Usar Managed Package Framework para implementar un tipo de proyecto (C#).](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md)

- Para los desarrolladores de C++, las clases de la biblioteca HierUtil funcionan de forma similar. Para obtener más información, vea No en la compilación: Usar clases de proyecto [HierUtil7 para implementar un tipo de proyecto (C++).](/previous-versions/bb166212(v=vs.100))

- Los tipos de proyecto pueden admitir datos distintos de los archivos de código fuente típicos que se compilan en un .exe o .dll ensamblado. Por ejemplo, los proyectos de base de datos contienen referencias a archivos de script y consulta almacenados en disco y agregan comandos a Explorador de soluciones para ejecutar los scripts y las consultas en una base de datos, pero los proyectos no admiten el comportamiento de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilación.  Para obtener más información, vea [Abrir y guardar elementos de proyecto.](../../extensibility/internals/opening-and-saving-project-items.md)

- Un tipo de proyecto no tiene que usar archivos en absoluto. Por ejemplo, un tipo de proyecto podría almacenar todos sus datos en una base de datos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona a los tipos de proyecto control total sobre cómo conservan los datos de los proyectos y los elementos del proyecto. Para obtener más información, vea [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

- Los tipos de proyecto deben proporcionar un generador de proyectos *,* que es un objeto que crea una instancia del tipo de proyecto cada vez que se le dice que abra o cree un proyecto basado en ese tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de proyecto. Para obtener más información, vea [Creating Project Instances By Using Project Factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

- Los tipos de proyecto deben proporcionar plantillas para proyectos y elementos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa las plantillas cuando los usuarios crean nuevos proyectos y agregan nuevos elementos a los proyectos existentes. Para obtener más información, vea [Adding Project and Project Item Templates](../../extensibility/internals/adding-project-and-project-item-templates.md).

- Los tipos de proyecto pueden admitir varias configuraciones, como Depurar y Versión. Los usuarios pueden cambiar las distintas configuraciones de un proyecto mediante las páginas de propiedades que proporcione. Para obtener más información, vea [Administración de opciones de configuración.](../../extensibility/internals/managing-configuration-options.md)

## <a name="see-also"></a>Consulta también
- [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)