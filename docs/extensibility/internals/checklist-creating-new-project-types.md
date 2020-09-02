---
title: 'Lista de comprobación: crear nuevos tipos de proyecto | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating new types
- project types, checklist for creating
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9372762f713b6a5ec78a92eeb96e8a616101b5bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183397"
---
# <a name="checklist-create-new-project-types"></a>Lista de comprobación: crear nuevos tipos de proyecto
Debe completar varias tareas para crear un nuevo tipo de proyecto. La siguiente lista de comprobación proporciona una guía para estas tareas:

1. Diseñe la funcionalidad del nuevo tipo de proyecto. Para obtener más información, vea [decisiones de diseño de tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).

2. Determine los editores que se usan para el código y otros elementos del proyecto. Puede usar los editores principales o estándar, o puede crear y usar editores específicos del proyecto. Para obtener más información, vea [crear editores y diseñadores personalizados](../../extensibility/creating-custom-editors-and-designers.md) y [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).

3. Determine el nivel de participación que tendrán los elementos de proyecto en el **vista de clases** y en el **Examinador de objetos**. Para obtener más información, consulte [compatibilidad con las herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Derivar nuevas clases basadas en las decisiones de diseño que se realizaron anteriormente para el proyecto y los elementos de proyecto.

5. Escriba el código para los siguientes componentes de tipo de proyecto:

    - Generador de proyectos, para administrar la creación de nuevos proyectos y la apertura de proyectos existentes. Para obtener más información, vea [crear instancias de proyecto mediante el uso de generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).

    - Jerarquía de proyectos y control de comandos. Para obtener más información, vea [usar clases de proyecto de HierUtil7 para implementar un tipo de proyecto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346), [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md), [componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md)y [MenuCommands frente a OleMenuCommands](/visualstudio/misc/menucommands-vs-olemenucommands?view=vs-2015).

    - Administración de elementos de proyecto, incluida la adición del proyecto al cuadro de diálogo **nuevo proyecto** . Para obtener más información, vea [agregar plantillas](../../extensibility/internals/adding-project-and-project-item-templates.md) de proyecto y de elemento de proyecto y [registrar plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistencia del estado y los elementos individuales del proyecto. Para obtener más información, vea [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md). Para la persistencia de la información de la solución, consulte [soluciones](../../extensibility/internals/solutions-overview.md).

    - Propiedades independientes de la configuración que se van a mostrar en el ventana Propiedades. Para obtener más información, vea [Extend Properties](../../extensibility/internals/extending-properties.md).

    - Propiedades de configuración del proyecto tal como se implementa en las páginas de propiedades para mostrar las propiedades dependientes de la configuración. Para obtener más información, vea [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).

    - Enumerando resultados para la implementación. Para obtener más información, vea [configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

    - Servicios de inicio de proyecto. Para obtener más información, vea [elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md) y [componentes principales del modelo de proyecto](../../extensibility/internals/project-model-core-components.md).

    - Objetos, o clases derivadas de `IDispatch` , disponibles para la automatización.

    - Archivos de tabla de comandos XML (*. Vsct*). Para obtener más información, vea [archivos de tabla de comandos de Visual Studio (. Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

6. Pruebe, depure e inicie el tipo de proyecto.

7. Muestre el proyecto en la pestaña **proyecto** del cuadro de diálogo **Agregar referencia** estableciendo `VARIANT_TRUE` como valor de `VSHPROPID_ShowProjInSolutionPage` . Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Cree el archivo de Microsoft Installer (*. msi*) para instalar los VSPackages. Para obtener más información, vea [install VSPackages with Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Register a Project Type](../../extensibility/internals/registering-a-project-type.md)y [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Vea también
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Cuándo crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)
- [Crear tipos de proyecto](../../extensibility/internals/creating-project-types.md)
