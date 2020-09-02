---
title: Aspectos básicos de los tipos de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types [Visual Studio SDK]
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e45d5f252deaf1788ae5093048ef8afb900fbe4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704075"
---
# <a name="project-type-essentials"></a>Conceptos básicos del tipo de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] incluye varios tipos de proyecto para lenguajes como [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] . [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] también le permite crear sus propios tipos de proyecto.  
  
 Si solo desea agregar comandos, editores o ventanas de herramientas personalizados a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , puede hacerlo sin crear un nuevo tipo de proyecto. Para obtener más información, vea los temas siguientes:  
  
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Del mismo modo, si desea personalizar el comportamiento de los [!INCLUDE[csprcs](../../includes/csprcs-md.md)] tipos de proyecto y proporcionados [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] , puede hacerlo mediante subtipos de proyecto. Para obtener más información, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
  Debe crear un nuevo tipo de proyecto para los proyectos basados en un lenguaje distinto de [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] si desea admitir uno o varios de los siguientes elementos:  
  
- Compilar  
  
- Implementación  
  
- Varias configuraciones  
  
- Control de código fuente  
  
- Depuración  
  
- Elementos de proyecto en Explorador de soluciones  
  
- Cuadros de diálogo **Abrir proyecto** o **nuevo proyecto**  
  
- Anidamiento de proyectos  
  
- Para obtener más información acerca de las capacidades de los tipos de proyecto, vea lo siguiente:  
  
- Los tipos de proyecto son objetos de un VSPackage que implementan el conjunto de interfaces [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] espera. Si usa C# para desarrollar un tipo de proyecto, las clases de proyecto de Managed Package Framework implementan las interfaces necesarias automáticamente y permiten heredar esa implementación. Para obtener más información, vea [usar el marco de trabajo de paquetes administrados para implementar un tipo de proyecto (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- En el caso de los desarrolladores de C++, las clases de la biblioteca HierUtil funcionan de manera similar. Para obtener más información, vea [no está en la compilación: usar clases de proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Los tipos de proyecto pueden admitir datos distintos de los archivos de código fuente típicos que se compilan en un ensamblado. exe o. dll. Por ejemplo, los [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyectos de base de datos contienen referencias a archivos de script y de consulta almacenados en disco y agregan comandos a **Explorador de soluciones** para ejecutar los scripts y las consultas en una base de datos, pero los proyectos no admiten el comportamiento de compilación. Para obtener más información, vea [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- Un tipo de proyecto no tiene que usar archivos en absoluto. Por ejemplo, un tipo de proyecto podría almacenar todos sus datos en una base de datos. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proporciona a los tipos de proyecto un control completo sobre cómo conservan los datos para los proyectos y los elementos de proyecto. Para obtener más información, vea [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
- Los tipos de proyecto deben proporcionar un *generador de proyectos*, que es un objeto que crea una instancia del tipo de proyecto siempre que se le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] indica que abra o cree un proyecto basado en ese tipo de proyecto. Para obtener más información, vea [crear instancias de proyecto mediante el uso de generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Los tipos de proyecto deben proporcionar plantillas para proyectos y elementos de proyecto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa las plantillas cuando los usuarios crean nuevos proyectos y agregan nuevos elementos a los proyectos existentes. Para obtener más información, vea [agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Los tipos de proyecto pueden admitir varias configuraciones, como la depuración y la versión. Los usuarios pueden cambiar las diferentes configuraciones de un proyecto mediante las páginas de propiedades que proporcione. Para obtener más información, vea [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Consulte también  
 [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)
