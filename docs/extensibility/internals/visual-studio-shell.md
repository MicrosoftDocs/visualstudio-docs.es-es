---
title: Shell de Visual Studio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a147abd4655c923604dd9ca6696e97aac4944ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332875"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell es el agente de integración en principal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. El shell proporciona la funcionalidad necesaria para habilitar los VSPackages compartir los servicios comunes. Dado que el objetivo de la arquitectura [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es chaleco funcionalidad principal en los VSPackages, el shell es un marco de trabajo para proporcionar funcionalidad básica y admite la comunicación cruzada entre su componente VSPackages.

## <a name="shell-responsibilities"></a>Responsabilidades de shell
 El shell tiene las siguientes responsabilidades claves:

- Admitir elementos básicos de la interfaz de usuario (IU) (a través de interfaces COM). Estos incluyen menús predeterminados y las barras de herramientas, marcos de ventana de documento o ventanas secundarias de interfaz de múltiples documentos (MDI) y marcos de ventana de herramienta y soporte técnico de acoplamiento.

- Mantener un listado actualizado de todos los documentos abiertos actualmente en una tabla de documentos en ejecución (RDT) con el fin de coordinar la persistencia de los documentos y para garantizar que un documento no se puede abrir en más de una forma o de formas no compatibles.

- Compatibilidad con la interfaz de enrutamiento de comandos y control de comandos, `IOleCommandTarget`.

- Al cargar VSPackages en los momentos adecuados. Un VSPackage de carga de retraso es necesaria para mejorar el rendimiento del shell.

- Administrar determinados servicios compartidos, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, lo que proporciona la funcionalidad básica de shell, y <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que proporciona la funcionalidad básica de ventanas.

- Administración de los archivos de solución (.sln). Las soluciones contienen grupos de proyectos relacionados, similares a los archivos del área de trabajo (.dsw) en Visual C++ 6.0.

- Selección de todo el shell de seguimiento, el contexto y la moneda. El shell realiza un seguimiento de los siguientes tipos de elementos:

  - El proyecto actual

  - El elemento de proyecto actual o un ItemID actual <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - La selección actual para el **propiedades** ventana o `SelectionContainer`

  - El contexto de interfaz de usuario, identificadores o CmdUIGuids que controlan la visibilidad de comandos, menús y barras de herramientas

  - Los elementos actualmente activos, como la ventana activa, el documento y el Administrador de deshacer

  - Los atributos de contexto de usuario que controlan la Ayuda dinámica

  El shell también Media en la comunicación entre VSPackages instalados y los servicios actuales. Admite las características principales del shell y pone a disposición de todos los VSPackages integrados en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Estas características principales incluyen los siguientes elementos:

- **Acerca de** pantalla de presentación y de cuadro de diálogo

- **Agregar nuevo y agregar elemento existente** cuadros de diálogo

- **Vista de clases** ventana y **Examinador de objetos**

- **Referencias** cuadro de diálogo

- **Esquema de documento** ventana

- **Ayuda dinámica** ventana

- **Buscar** y **reemplazar**

- **Abrir proyecto** y **abrir archivo** cuadros de diálogo en el **New** menú

- **Opciones de** cuadro de diálogo en el **herramientas** menú

- Ventana de **propiedades**

- **Explorador de soluciones**

- **Lista de tareas** ventana

- **Cuadro de herramientas**

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)