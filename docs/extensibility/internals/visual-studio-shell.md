---
title: Shell de Visual Studio (Visual Studio Shell) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703998"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell es el agente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]principal de integración en . El shell proporciona la funcionalidad necesaria para permitir vsPackages para compartir servicios comunes. Dado que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] objetivo arquitectónico de es establecer la funcionalidad principal en los VSPackages, el shell es un marco para proporcionar funcionalidad básica y admitir la comunicación cruzada entre sus componentes VSPackages.

## <a name="shell-responsibilities"></a>Responsabilidades de Shell
 El shell tiene las siguientes responsabilidades clave:

- Compatibilidad con elementos básicos (a través de interfaces COM) de la interfaz de usuario (UI). Estos incluyen menús y barras de herramientas predeterminados, marcos de ventanas de documento o ventanas secundarias de interfaz multidocumento (MDI), marcos de ventanas de herramientas y compatibilidad con el acoplamiento.

- Mantener una lista en ejecución de todos los documentos abiertos actualmente en una tabla de documentos en ejecución (RDT) con el fin de coordinar la persistencia de los documentos y garantizar que un documento no se puede abrir de más de una manera, o de maneras incompatibles.

- Compatible con la interfaz de enrutamiento `IOleCommandTarget`de comandos y gestión de comandos, .

- Carga de VSPackages en los momentos adecuados. Retrasar la carga de un VSPackage es necesario para mejorar el rendimiento del shell.

- Administración de determinados <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>servicios compartidos, como , <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>que proporciona funcionalidad básica de shell y , que proporciona funcionalidad básica de ventanas.

- Administración de los archivos de solución (.sln). Las soluciones contienen grupos de proyectos relacionados, similares a los archivos de área de trabajo (.dsw) en Visual C++ 6.0.

- Seguimiento de la selección, el contexto y la moneda de todo el shell. El shell realiza un seguimiento de los siguientes tipos de elementos:

  - El proyecto actual

  - El elemento de proyecto actual o ItemID el actual<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - La selección actual para la ventana **Propiedades** o`SelectionContainer`

  - Los IDs de contexto de interfaz de usuario o CmdUIGuids que controlan la visibilidad de comandos, menús y barras de herramientas

  - Los elementos activos actualmente, como la ventana activa, el documento y el administrador de deshacer

  - Los atributos de contexto de usuario que impulsan la Ayuda dinámica

  El shell también media la comunicación entre VSPackages instalados y los servicios actuales. Es compatible con las características principales del shell y [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]las pone a disposición de todos los VSPackages integrados en . Estas características principales incluyen los siguientes elementos:

- **Acerca del** cuadro de diálogo y la pantalla de presentación

- **Agregar nuevo y Agregar elemento existente** cuadros de diálogo

- **Ventana Vista de clases** y **Navegador de objetos**

- **Cuadro de** diálogo Referencias

- **Ventana Esquema del documento**

- **Ventana de Ayuda dinámica**

- **Buscar** y **reemplazar**

- **Abra** los cuadros de diálogo Proyecto y **Abrir archivo** en el menú **Nuevo**

- **Cuadro** de diálogo Opciones del menú **Herramientas**

- **Ventana Propiedades**

- **Explorador de soluciones**

- **Ventana Lista de tareas**

- **Cuadro de herramientas**

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
