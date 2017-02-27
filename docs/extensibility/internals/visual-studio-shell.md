---
title: "Visual Studio Shell | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Shell de Visual Studio"
  - "Shell de Visual Studio"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell es el principal agente de integración de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El shell proporciona la funcionalidad necesaria para habilitar VSPackages compartir servicios comunes. Dado que el objetivo de la arquitectura [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es chaleco funcionalidad principal en los VSPackages, el shell es un marco para proporcionar la funcionalidad básica y admitir la comunicación cruzada entre su componente VSPackages.  
  
## Responsabilidades de shell  
 El shell tiene las siguientes responsabilidades claves:  
  
-   Compatibilidad \(a través de interfaces COM\) de los elementos básicos de la interfaz de usuario \(UI\). Estos incluyen menús predeterminados y las barras de herramientas, marcos de ventana de documento o ventanas secundarias de interfaz de múltiples documentos \(MDI\) y marcos de ventana de herramienta y compatibilidad.  
  
-   Mantener una lista de todos los documentos abiertos actualmente en una tabla de documentos de ejecución \(RDT\) para coordinar la persistencia de los documentos y para garantizar que un documento no se puede abrir en más de una forma o en medios incompatibles.  
  
-   Compatible con la interfaz de enrutamiento de comandos y de control de comandos, `IOleCommandTarget`.  
  
-   Cargar VSPackages en los momentos adecuados. Carga retrasada un VSPackage es necesaria mejorar el rendimiento del shell.  
  
-   Administración de ciertos servicios compartidos, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, lo que proporciona la funcionalidad básica de shell, y <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que proporciona la funcionalidad básica de ventanas.  
  
-   Administración de los archivos de solución \(.sln\). Las soluciones contienen grupos de proyectos relacionados, similares a los archivos del área de trabajo \(.dsw\) en Visual C\+\+ 6.0.  
  
-   Selección de todo el shell de seguimiento, el contexto y la moneda. El shell realiza un seguimiento de los siguientes tipos de elementos:  
  
    -   El proyecto actual  
  
    -   El elemento de proyecto actual o Id. de elemento actual <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La selección actual para el **propiedades** ventana o `SelectionContainer`  
  
    -   El contexto de la interfaz de usuario identificadores o CmdUIGuids que controlan la visibilidad de las barras de herramientas, menús y comandos  
  
    -   Los elementos actualmente activos como la ventana activa, el documento y el Administrador de deshacer  
  
    -   Los atributos de contexto de usuario que controlan la Ayuda dinámica  
  
 El shell de Media también la comunicación entre los VSPackages instalados y los servicios actuales. Admite las características principales del shell y pone a disposición de todos los VSPackages integrados en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Estas características principales incluyen los siguientes elementos:  
  
-   **Sobre** pantalla de presentación y de cuadro de diálogo  
  
-   **Agregar nuevo y agregar elemento existente** cuadros de diálogo  
  
-   **La vista de clases** ventana y **Examinador de objetos**  
  
-   **Referencias** cuadro de diálogo  
  
-   **Esquema del documento** ventana  
  
-   **Ayuda dinámica** ventana  
  
-   **Buscar** y **reemplazar**  
  
-   **Abrir proyecto** y **Abrir archivo** cuadros de diálogo en el **nuevo** menú  
  
-   **Opciones** cuadro de diálogo en el **herramientas** menú  
  
-   **Propiedades** ventana  
  
-   **Explorador de soluciones**  
  
-   **Lista de tareas** ventana  
  
-   **Cuadro de herramientas**  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)