---
title: "Lista de comprobación: Creación de nuevos tipos de proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 06b6dc2fab4158f36126b6509909dd0db6fd7125
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-new-project-types"></a>Lista de comprobación: Creación de nuevos tipos de proyecto
Debe completar varias tareas para crear un nuevo tipo de proyecto. La siguiente lista de comprobación proporciona a una guía para esas tareas.  
  
1.  Diseñar la funcionalidad para el nuevo tipo de proyecto. Para obtener más información, consulte [decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determinar qué editores se utilizan para código y otros elementos de proyecto. Puede usar el núcleo o editores estándares, o puede crear y usar los editores de específica del proyecto. Para obtener más información, consulte [crear editores personalizados y diseñadores](../../extensibility/creating-custom-editors-and-designers.md) y [Cómo: abrir editores específica del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinar el nivel de participación tendrán sus elementos de proyecto en el **vista de clases** y **Examinador de objetos**. Para obtener más información, consulte [herramientas de exploración de admitir símbolo](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivar nuevas clases basadas en las decisiones de diseño que realizó anteriormente para el proyecto y elementos de proyecto.  
  
5.  Escribir el código para los siguientes componentes de tipo de proyecto:  
  
    -   Generador de proyectos, para administrar la creación de nuevos proyectos y abrir proyectos existentes. Para obtener más información, consulte [crear proyecto instancias por usar generadores de proyectos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Jerarquía de proyectos y gestión de comandos. Para obtener más información, consulte [no en la compilación: utilizar clases de proyecto HierUtil7 para implementar un tipo de proyecto (C++)](http://msdn.microsoft.com/en-us/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md), [componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)y [MenuCommands frente a. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
    -   Administración de elementos de proyecto, incluida la adición de su proyecto para la **nuevo proyecto** cuadro de diálogo. Para obtener más información, consulte [Agregar proyecto y plantillas de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md) y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistencia de estado de proyecto y elementos individuales. Para obtener más información, consulte [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md). Para la persistencia de la información de la solución, vea [soluciones](../../extensibility/internals/solutions.md).  
  
    -   Propiedades independientes de configuración para mostrar en la ventana Propiedades. Para obtener más información, consulte [extender propiedades](../../extensibility/internals/extending-properties.md).  
  
    -   Propiedades de configuración del proyecto como se implementa en las páginas de propiedades para mostrar las propiedades dependientes de la configuración. Para obtener más información, consulte [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Enumerar salidas para la implementación. Para obtener más información, consulte [configuración del proyecto para la salida de](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servicios de inicio de proyecto. Para obtener más información, consulte [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md) y [componentes principales del proyecto de modelo](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objetos o clases derivadas de `IDispatch`, que está disponible para la automatización.  
  
    -   Archivos de tabla de comandos de XML (.vsct). Para obtener más información, vea [tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Probar, depurar y el tipo de proyecto de inicio.  
  
7.  Mostrar el proyecto en el **proyecto** pestaña de la **Agregar referencia** cuadro de diálogo estableciendo `VARIANT_TRUE` como el valor de `VSHPROPID_ShowProjInSolutionPage`. Para obtener más información, consulte <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Crear el archivo de Microsoft Installer (.msi) para instalar los paquetes VSPackage. Para obtener más información, consulte [instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [registrar un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md), y [VSPackages](../../extensibility/internals/vspackages.md).  
  
## <a name="see-also"></a>Vea también  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Cuándo se debe crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)