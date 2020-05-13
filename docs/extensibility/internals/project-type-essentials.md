---
title: Elementos esenciales del proyecto ( Project Type Essentials) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b44da532207668d9526aec0ccdcab027b94184e6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706378"
---
# <a name="project-type-essentials"></a>Conceptos básicos del tipo de proyecto
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]incluye varios tipos de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyectos [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]para idiomas como o . [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]también le permite crear sus propios tipos de proyecto.

 Si solo desea agregar comandos personalizados, editores o ventanas de herramientas a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede hacerlo sin crear un nuevo tipo de proyecto. Para obtener más información, vea los temas siguientes:

- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

- [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)

- [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md)

  Del mismo modo, si desea personalizar [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] el [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] comportamiento de los tipos proporcionados y de proyecto, puede hacerlo utilizando subtipos de proyecto. Para obtener más información, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

  Debe crear un nuevo tipo de proyecto para proyectos [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] que se basan en un idioma distinto de y si desea admitir uno o varios de los siguientes:

- Compilar

- Implementación

- Múltiples configuraciones

- Control de código fuente

- Depuración

- Elementos de proyecto en el Explorador de soluciones

- Los cuadros de diálogo **Abrir proyecto** o **Nuevo proyecto**

- Anidación de proyectos

- Para obtener más información acerca de las capacidades de los tipos de proyecto, consulte lo siguiente:

- Tipos de proyecto son objetos en un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage que implementan el conjunto de interfaces espera. Si usa C- para desarrollar un tipo de proyecto, las clases de proyecto de Managed Package Framework implementan las interfaces necesarias para usted y le permiten heredar esa implementación. Para obtener más información, vea Uso del marco de trabajo de paquete administrado para implementar un tipo de [proyecto (C-)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).

- Para los desarrolladores de C++, las clases de la biblioteca HierUtil funcionan de forma similar. Para obtener más información, vea No en compilación: uso de clases de [proyecto HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

- Los tipos de proyecto pueden admitir datos distintos de los archivos de código fuente típicos que se compilan en un ensamblado .exe o .dll. Por ejemplo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] los proyectos de base de datos contienen referencias a archivos de script y consulta almacenados en el disco y agregan comandos al **Explorador** de soluciones para ejecutar los scripts y consultas en una base de datos, pero los proyectos no admiten el comportamiento de compilación. Para obtener más información, consulte Apertura y guardado de [elementos](../../extensibility/internals/opening-and-saving-project-items.md)de proyecto .

- Un tipo de proyecto no tiene que utilizar archivos en absoluto. Por ejemplo, un tipo de proyecto podría almacenar todos sus datos en una base de datos. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona a los tipos de proyecto un control completo sobre cómo conservan los datos de los proyectos y los elementos de proyecto. Para obtener más información, vea [Decisiones](../../extensibility/internals/project-type-design-decisions.md)de diseño de tipo de proyecto .

- Los tipos de proyecto deben proporcionar un generador de *proyectos,* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que es un objeto que crea una instancia del tipo de proyecto siempre que se le indique que abra o cree un proyecto basado en ese tipo de proyecto. Para obtener más información, vea Creación de instancias de [proyecto mediante factorías](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)de proyecto .

- Los tipos de proyecto deben proporcionar plantillas para proyectos y elementos de proyecto. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utiliza las plantillas cuando los usuarios crean nuevos proyectos y agregan nuevos elementos a los proyectos existentes. Para obtener más información, vea Agregar plantillas de [proyecto y elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)de proyecto .

- Los tipos de proyecto pueden admitir varias configuraciones, como Depurar y Liberar. Los usuarios pueden cambiar las diferentes configuraciones de un proyecto mediante las páginas de propiedades que proporcione. Para obtener más información, consulte Administración de opciones de [configuración](../../extensibility/internals/managing-configuration-options.md).

## <a name="see-also"></a>Vea también
- [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)
