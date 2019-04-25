---
title: 'Lista de comprobación: Creación de nuevos tipos de proyecto | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1699846c0a588a21ebd37a13f77dc45c2a695139
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101059"
---
# <a name="checklist-creating-new-project-types"></a>Lista de comprobación: Creación de nuevos tipos de proyectos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debe completar varias tareas para crear un nuevo tipo de proyecto. La siguiente lista de comprobación proporciona a una guía para esas tareas.  
  
1. Diseñe la funcionalidad para el tipo de proyecto nuevo. Para obtener más información, consulte [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
2. Determinar qué editores se utilizan para código y otros elementos de proyecto. Puede usar el núcleo o editores estándar, o puede crear y usar los editores específicos del proyecto. Para obtener más información, consulte [crear editores personalizados y diseñadores](../../extensibility/creating-custom-editors-and-designers.md) y [Cómo: Apertura de editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3. Determinar el nivel de participación que tendrán los elementos de proyecto en el **vista de clases** y **Examinador de objetos**. Para obtener más información, consulte [herramientas de exploración de símbolos que admiten](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4. Derivar nuevas clases basadas en las decisiones de diseño que realizó anteriormente para el proyecto y elementos de proyecto.  
  
5. Escribir el código para los siguientes componentes de tipo de proyecto:  
  
    - Generador de proyectos para administrar la creación de nuevos proyectos y abrir proyectos existentes. Para obtener más información, consulte [crear proyecto instancias por usar generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    - Jerarquía del proyecto y gestión de comandos. Para obtener más información, consulte [no en la compilación: Uso de HierUtil7 proyecto clases para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md), [componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md) y [MenuCommands frente a. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    - Administración de elementos de proyecto, incluida la adición de su proyecto a la **nuevo proyecto** cuadro de diálogo. Para obtener más información, consulte [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    - Persistencia de estado del proyecto y elementos individuales. Para obtener más información, consulte [abriendo y guardando elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md). Para la persistencia de la información de la solución, consulte [soluciones](../../extensibility/internals/solutions-overview.md).  
  
    - Propiedades independientes de configuración que se muestra en la ventana Propiedades. Para obtener más información, consulte [extender propiedades](../../extensibility/internals/extending-properties.md).  
  
    - Propiedades de configuración del proyecto tal como está implementado en las páginas de propiedades para mostrar las propiedades dependientes de la configuración. Para obtener más información, consulte [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
    - Enumerar salidas para la implementación. Para obtener más información, consulte [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).  
  
    - Servicios de inicio del proyecto. Para obtener más información, consulte [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md) y [componentes principales del proyecto de modelo](../../extensibility/internals/project-model-core-components.md).  
  
    - Los objetos o clases derivadas de `IDispatch`, disponible para la automatización.  
  
    - Archivos de la tabla de comandos XML (.vsct). Para obtener más información, consulta [Visual Studio Command Table (.Vsct) Files](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6. Probar, depurar e iniciar el tipo de proyecto.  
  
7. Mostrar el proyecto en el **proyecto** pestaña de la **Agregar referencia** cuadro de diálogo estableciendo `VARIANT_TRUE` como el valor de `VSHPROPID_ShowProjInSolutionPage`. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8. Cree el archivo Microsoft Installer (.msi) para instalar los paquetes VSPackage. Para obtener más información, consulte [Installing VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrar un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md), y [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vea también  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Cuándo se debe crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)
