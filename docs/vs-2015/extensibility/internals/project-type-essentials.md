---
title: Conceptos básicos del tipo de proyecto | Microsoft Docs
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704075"
---
# <a name="project-type-essentials"></a>Conceptos básicos del tipo de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] incluye varios tipos de proyectos para idiomas como [!INCLUDE[csprcs](../../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] También le permite crear sus propios tipos de proyecto.  
  
 Si desea agregar comandos personalizados, editores o ventanas de herramientas a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], puede hacerlo sin necesidad de crear un nuevo tipo de proyecto. Para obtener más información, vea los temas siguientes:  
  
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
- [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)  
  
- [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md)  
  
  Del mismo modo, si desea personalizar el comportamiento de la [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] tipos de proyecto, puede hacer mediante subtipos de proyecto. Para obtener más información, consulte [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
  Debe crear un nuevo tipo de proyecto para los proyectos que se basan en un idioma distinto [!INCLUDE[csprcs](../../includes/csprcs-md.md)] y [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] si desea admitir uno o varios de los siguientes:  
  
- Compilar  
  
- Implementación  
  
- Varias configuraciones  
  
- Control de código fuente  
  
- Depuración  
  
- Elementos de proyecto en el Explorador de soluciones  
  
- El **Abrir proyecto** o **nuevo proyecto** cuadros de diálogo  
  
- Anidamiento de proyecto  
  
- Para obtener más información acerca de las capacidades de tipos de proyecto, vea lo siguiente:  
  
- Tipos de proyecto son objetos en un VSPackage que implementan el conjunto de interfaces [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] espera. Si está utilizando C# para desarrollar un tipo de proyecto, las clases del proyecto de Managed Package Framework implementan las interfaces necesarias para usted y le permiten heredar esa implementación. Para obtener más información, consulte [mediante Managed Package Framework para implementar un tipo de proyecto (C#)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
- Para los desarrolladores de C++, las clases de la biblioteca HierUtil funcionan de forma similar. Para obtener más información, consulte [no en la compilación: Uso de HierUtil7 proyecto clases para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
- Los tipos de proyecto pueden admitir datos distintos de los archivos de código fuente típico que se basan en un ensamblado .exe o .dll. Por ejemplo, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyectos de base de datos contienen referencias a la secuencia de comandos y consultas de los archivos almacenados en disco y agregar comandos a **el Explorador de soluciones** para ejecutar los scripts y consultas en una base de datos, pero los proyectos no admiten compilar el comportamiento. Para obtener más información, consulte [abriendo y guardando elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
- No tiene un tipo de proyecto usar en todos los archivos. Por ejemplo, un tipo de proyecto podría almacenar todos sus datos en una base de datos. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ofrece control completo sobre cómo conservar los datos para los proyectos y elementos de proyecto de tipos de proyecto. Para obtener más información, consulte [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
- Tipos de proyecto deben proporcionar un *generador de proyectos*, que es un objeto que se crea una instancia del proyecto cada vez que escriba [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se le indica que abra o cree un proyecto que se basa en ese tipo de proyecto. Para obtener más información, consulte [crear proyecto instancias por usar generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
- Tipos de proyecto deben proporcionar plantillas para proyectos y elementos de proyecto. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utiliza las plantillas cuando los usuarios creación nuevos proyectos y agregar nuevos elementos a los proyectos existentes. Para obtener más información, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
- Tipos de proyecto pueden admitir varias configuraciones, como Debug y Release. Los usuarios pueden cambiar las diferentes configuraciones de un proyecto mediante el uso de páginas de propiedades que proporcione. Para obtener más información, consulte [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementación de tipos de proyecto](../../extensibility/internals/deploying-project-types.md)
