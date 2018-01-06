---
title: Shell de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9240df0a4f551ab4fa47fc2ceacaf0654dc562e4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell es el agente de integración en principal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El shell proporciona funcionalidad necesaria para habilitar VSPackages compartir servicios comunes. Dado que el objetivo de arquitectura de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es chaleco funcionalidad principal en los VSPackages, el shell es un marco para proporcionar la funcionalidad básica y admitir la comunicación cruzada entre su componente VSPackages.  
  
## <a name="shell-responsibilities"></a>Responsabilidades de shell  
 El shell tiene las siguientes responsabilidades claves:  
  
-   (A través de interfaces de COM) se admiten elementos básicos de la interfaz de usuario (UI). Estos incluyen menús predeterminados y las barras de herramientas, los marcos de ventana de documento o ventanas secundarias de interfaz de múltiples documentos (MDI) y marcos de ventana de herramienta y compatibilidad.  
  
-   Mantener una lista de todos los documentos abiertos actualmente en una tabla de documentos de ejecución (RDT) con el fin de coordinar la persistencia de los documentos y para garantizar que un documento no se puede abrir en más de una manera o de formas incompatible.  
  
-   Compatibilidad con la interfaz de enrutamiento de comandos y gestión de comandos, `IOleCommandTarget`.  
  
-   Cargar VSPackages en los momentos adecuados. Carga retrasada un VSPackage es necesaria para mejorar el rendimiento del shell.  
  
-   Administrar determinados servicios compartidos, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, lo que proporciona funcionalidad de shell básico, y <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, lo que proporciona la funcionalidad básica basada en ventanas.  
  
-   Administración de los archivos de solución (.sln). Las soluciones contienen grupos de proyectos relacionados, similares a los archivos de área de trabajo (.dsw) en Visual C++ 6.0.  
  
-   Selección de todo el shell de seguimiento, contexto y moneda. El shell realiza un seguimiento de los siguientes tipos de elementos:  
  
    -   El proyecto actual  
  
    -   El elemento de proyecto actual o ItemID actual<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   La selección actual para la **propiedades** ventana o`SelectionContainer`  
  
    -   El contexto de la interfaz de usuario CmdUIGuids que controlan la visibilidad de los comandos, menús y barras de herramientas o Id.  
  
    -   Los elementos actualmente activos, como la ventana activa, el documento y el Administrador de deshacer  
  
    -   Los atributos de contexto de usuario que controlan la Ayuda dinámica  
  
 El shell de Media también la comunicación entre los servicios actuales y VSPackages instalados. Es compatible con las características principales del shell y hace que estén disponibles para todos los VSPackages integrados en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Estas características principales incluyen los siguientes elementos:  
  
-   **Acerca de** pantalla de presentación y de cuadro de diálogo  
  
-   **Agregar nuevo y agregar elemento existente** cuadros de diálogo  
  
-   **Vista de clases** ventana y **Examinador de objetos**  
  
-   **Referencias** cuadro de diálogo  
  
-   **Esquema de documento** ventana  
  
-   **Ayuda dinámica** ventana  
  
-   **Buscar** y **reemplazar**  
  
-   **Abrir proyecto** y **archivos abiertos** cuadros de diálogo en el **New** menú  
  
-   **Opciones de** cuadro de diálogo en el **herramientas** menú  
  
-   **Propiedades** ventana  
  
-   **Explorador de soluciones**  
  
-   **Lista de tareas** ventana  
  
-   **Cuadro de herramientas**  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)