---
title: "Lista de comprobaci&#243;n: Crear nuevos tipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "creación de nuevos tipos de proyectos [Visual Studio SDK]"
  - "tipos de proyecto, la lista de comprobación para la creación de"
ms.assetid: 29eb9c3b-1933-4741-aa85-65a33f0825ba
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Lista de comprobaci&#243;n: Crear nuevos tipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debe completar varias tareas para crear un nuevo tipo de proyecto. La siguiente lista de comprobación proporciona a una guía para esas tareas.  
  
1.  Diseñe la funcionalidad para el tipo de proyecto nuevo. Para obtener más información, consulta [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
2.  Determine qué editores se utilizan para el código y otros elementos de proyecto. Puede utilizar el núcleo o editores estándares, o puede crear y utilizar los editores específicos del proyecto. Para obtener más información, vea [Creación de diseñadores y editores personalizados](../../extensibility/creating-custom-editors-and-designers.md) y [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md).  
  
3.  Determinar el nivel de participación tendrán sus elementos de proyecto en el **la vista de clases** y **Examinador de objetos**. Para obtener más información, consulta [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md).  
  
4.  Derivar clases nuevas basadas en las decisiones de diseño que realizó anteriormente para el proyecto y elementos de proyecto.  
  
5.  Escribir el código para los siguientes componentes de tipo de proyecto:  
  
    -   Generador de proyectos para administrar la creación de nuevos proyectos y abrir proyectos existentes. Para obtener más información, consulta [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
    -   Jerarquía de proyectos y gestión de comandos. Para obtener más información, consulte [no en la compilación: utilizar clases de proyecto HierUtil7 para implementar un tipo de proyecto \(C\+\+\)](http://msdn.microsoft.com/es-es/a5c16a09-94a2-46ef-87b5-35b815e2f346), [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md), [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md) y [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
    -   Administración de elementos de proyecto, incluida la adición de su proyecto para la **nuevo proyecto** cuadro de diálogo. Para obtener más información, vea [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md) y [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md).  
  
    -   Persistencia de estado de los proyectos y elementos individuales. Para obtener más información, consulta [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md). Para la persistencia de la información de la solución, consulte [Soluciones](../../extensibility/internals/solutions.md).  
  
    -   Propiedades independientes de configuración para mostrar en la ventana Propiedades. Para obtener más información, consulta [Extender propiedades](../../extensibility/internals/extending-properties.md).  
  
    -   Propiedades de configuración de proyecto tal como se implementa en las páginas de propiedades para mostrar las propiedades dependientes de la configuración. Para obtener más información, consulta [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
    -   Enumerar salidas para la implementación. Para obtener más información, consulta [Configuración del proyecto para la salida](../../extensibility/internals/project-configuration-for-output.md).  
  
    -   Servicios de inicio del proyecto. Para obtener más información, vea [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md) y [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md).  
  
    -   Objetos o clases derivadas de `IDispatch`, disponible para la automatización.  
  
    -   Archivos de la tabla de comandos de XML \(.vsct\). Para obtener más información, consulta [Tabla de comandos de Visual Studio \(. Archivos de Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
6.  Probar, depurar y su tipo de proyecto de inicio.  
  
7.  Mostrar el proyecto en el **proyecto** ficha de la **Agregar referencia** cuadro de diálogo estableciendo `VARIANT_TRUE` como el valor de `VSHPROPID_ShowProjInSolutionPage`. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>.  
  
8.  Crear el archivo de Microsoft Installer \(.msi\) para instalar los VSPackages. Para obtener más información, vea [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md), [Registra un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md) y [VSPackages](../../extensibility/internals/vspackages.md).  
  
## Vea también  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)   
 [Cuándo crear tipos de proyecto](../../extensibility/internals/when-to-create-project-types.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)