---
title: 'Lista de verificación: Creación de nuevos tipos de proyecto Microsoft Docs'
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
ms.openlocfilehash: 5963083239571af43012e1a79576ee80846d80bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709748"
---
# <a name="checklist-create-new-project-types"></a>Lista de verificación: Crear nuevos tipos de proyecto
Debe completar varias tareas para crear un nuevo tipo de proyecto. La siguiente lista de comprobación proporciona una guía para esas tareas:

1. Diseñe la funcionalidad para el nuevo tipo de proyecto. Para obtener más información, consulte [Decisiones](../../extensibility/internals/project-type-design-decisions.md)de diseño de tipo de proyecto .

2. Determine qué editores se utilizan para el código y otros elementos del proyecto. Puede utilizar los editores principales o estándar, o puede crear y utilizar editores específicos del proyecto. Para obtener más información, consulte [Crear editores y diseñadores personalizados](../../extensibility/creating-custom-editors-and-designers.md) y [Cómo: Abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).

3. Determine el nivel de participación que tendrán los elementos del proyecto en la **vista de clases** y el **Examinador de objetos**. Para obtener más información, consulte Compatibilidad con [herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).

4. Derive nuevas clases basadas en las decisiones de diseño que tomó anteriormente para los elementos de proyecto y proyecto.

5. Escriba el código para los siguientes componentes de tipo de proyecto:

    - Fábrica de proyectos, para gestionar la creación de nuevos proyectos y la apertura de proyectos existentes. Para obtener más información, consulte Crear instancias de [proyecto mediante generadores](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)de proyectos.

    - Jerarquía de proyectos y control de comandos. Para obtener más información, vea Usar clases de [proyecto HierUtil7 para implementar un tipo de proyecto (C++),](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346) [Elementos de un modelo](../../extensibility/internals/elements-of-a-project-model.md)de proyecto , [Componentes principales](../../extensibility/internals/project-model-core-components.md)del modelo de proyecto y MenuCommands frente a [OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

    - Administración de elementos de proyecto, incluida la adición del proyecto al cuadro de diálogo **Nuevo proyecto.** Para obtener más información, vea Agregar plantillas de [elementos](../../extensibility/internals/adding-project-and-project-item-templates.md) de proyecto y proyecto y Registrar plantillas de [proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md).

    - Persistencia del estado del proyecto y de los elementos individuales. Para obtener más información, consulte [Abrir y guardar elementos](../../extensibility/internals/opening-and-saving-project-items.md)de proyecto . Para obtener información sobre la persistencia de la solución, consulte [Soluciones](../../extensibility/internals/solutions-overview.md).

    - Propiedades independientes de la configuración que se mostrarán en la ventana Propiedades. Para obtener más información, consulte [Extender propiedades](../../extensibility/internals/extending-properties.md).

    - Propiedades de configuración del proyecto tal como se implementan en las páginas de propiedades para mostrar propiedades dependientes de la configuración. Para obtener más información, consulte [Administrar opciones](../../extensibility/internals/managing-configuration-options.md)de configuración .

    - Enumeración de salidas para la implementación. Para obtener más información, consulte [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).

    - Servicios de inicio de proyectos. Para obtener más información, vea [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md) y [Componentes principales](../../extensibility/internals/project-model-core-components.md)del modelo de proyecto .

    - Objetos o clases `IDispatch`derivadas de , disponibles para la automatización.

    - Archivos de tabla de comandos XML (*.vsct*). Para obtener más información, vea Archivos de tabla de [comandos de Visual Studio (.vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

6. Pruebe, depure e inicie el tipo de proyecto.

7. Muestre el proyecto en la ficha **Proyecto** del `VARIANT_TRUE` cuadro de `VSHPROPID_ShowProjInSolutionPage`diálogo **Agregar referencia** estableciendo como valor para . Para más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.

8. Cree el archivo microsoft Installer (*.msi*) para instalar los VSPackages. Para obtener más información, vea [Instalar VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), Registrar un tipo de [proyecto](../../extensibility/internals/registering-a-project-type.md)y [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="see-also"></a>Vea también
- [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Cuándo crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)
- [Crear tipos de proyecto](../../extensibility/internals/creating-project-types.md)
