---
title: "Essentials de tipo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto [Visual Studio SDK]"
ms.assetid: 09991589-2300-430e-b6a4-7f2b95fe676f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Essentials de tipo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] incluye varios tipos de proyectos para lenguajes como [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] También le permite crear sus propios tipos de proyecto.  
  
 Si desea agregar comandos personalizados, editores o ventanas de herramientas a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede hacerlo sin crear un nuevo tipo de proyecto. Para obtener más información, vea los temas siguientes:  
  
-   [Barras de herramientas, menús y comandos](../../extensibility/internals/commands-menus-and-toolbars.md)  
  
-   [Editor y extensiones de servicio de lenguaje](../../extensibility/editor-and-language-service-extensions.md)  
  
-   [Ampliación y personalización de ventanas de herramientas](../../extensibility/extending-and-customizing-tool-windows.md)  
  
 Del mismo modo, si desea personalizar el comportamiento de la [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto, puede hacer mediante subtipos de proyecto. Para obtener más información, consulta [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
 Debe crear un nuevo tipo de proyecto para los proyectos que se basan en un lenguaje distinto de [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Si desea admitir uno o varios de los siguientes:  
  
-   Compilar  
  
-   Implementación  
  
-   Varias configuraciones  
  
-   Control de código fuente  
  
-   Depuración  
  
-   Elementos de proyecto en el Explorador de soluciones  
  
-   El **Abrir proyecto** o **nuevo proyecto** cuadros de diálogo  
  
-   Anidamiento de proyecto  
  
-   Para obtener más información acerca de las capacidades de tipos de proyecto, vea lo siguiente:  
  
-   Tipos de proyecto son objetos en un VSPackage que implementan el conjunto de interfaces [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] espera. Si está utilizando C\# para desarrollar un tipo de proyecto, las clases del proyecto Managed Package Framework implementan las interfaces necesarias para usted y le permiten heredan esa implementación. Para obtener más información, consulta [Utilizando el marco de trabajo de paquete administrado para implementar un tipo de proyecto \(C\#\)](../../extensibility/internals/using-the-managed-package-framework-to-implement-a-project-type-csharp.md).  
  
-   Para los desarrolladores de C\+\+, las clases de la biblioteca HierUtil funcionan de manera similar. Para obtener más información, consulte [no en la compilación: utilizar clases de proyecto HierUtil7 para implementar un tipo de proyecto \(C\+\+\)](http://msdn.microsoft.com/es-es/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
-   Tipos de proyecto pueden admitir datos distintos de los archivos de código fuente típico que compilar en un ensamblado .exe o .dll. Por ejemplo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos de base de datos contienen referencias a archivos de script y consulta almacenados en disco y agregar comandos a **el Explorador de soluciones** para ejecutar los scripts y consultas en una base de datos, pero los proyectos no admiten el comportamiento de compilación. Para obtener más información, consulta [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
-   No tiene un tipo de proyecto usar archivos en absoluto. Por ejemplo, un tipo de proyecto podría almacenar todos sus datos en una base de datos.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ofrece control completo sobre cómo se conservan los datos de proyectos y elementos de proyecto de tipos de proyecto. Para obtener más información, consulta [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md).  
  
-   Deben proporcionar los tipos de proyecto un *generador del proyecto*, que es un objeto que se crea una instancia del proyecto cada vez que escriba [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se le indica que abra o cree un proyecto basado en ese tipo de proyecto. Para obtener más información, consulta [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md).  
  
-   Tipos de proyecto deben proporcionar plantillas para proyectos y elementos de proyecto.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza las plantillas cuando los usuarios creación nuevos proyectos y agregar nuevos elementos a proyectos existentes. Para obtener más información, consulta [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
-   Tipos de proyecto pueden admitir varias configuraciones, como Debug y Release. Los usuarios pueden cambiar las diferentes configuraciones de un proyecto mediante el uso de páginas de propiedades que proporcione. Para obtener más información, consulta [Administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
## Vea también  
 [Tipos de proyecto de implementación](../../extensibility/internals/deploying-project-types.md)