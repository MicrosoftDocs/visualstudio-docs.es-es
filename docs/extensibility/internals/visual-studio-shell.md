---
title: Shell de Visual Studio | Microsoft Docs
description: Visual Studio Shell es el agente principal de integración en Visual Studio y proporciona funcionalidad básica y admite la comunicación cruzada entre los VSPackages.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 546a76d1533efaef28ddafb14b04514f64e9d4f9
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488055"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell es el agente principal de integración en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . El Shell proporciona la funcionalidad necesaria para permitir que los VSPackages compartan servicios comunes. Dado que el objetivo arquitectónico de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es atribuir la funcionalidad principal en los VSPackages, el Shell es un marco de trabajo para proporcionar la funcionalidad básica y admitir la comunicación cruzada entre sus componentes VSPackages.

## <a name="shell-responsibilities"></a>Responsabilidades del shell
 El shell tiene las siguientes responsabilidades clave:

- Compatibilidad (a través de interfaces COM) elementos básicos de la interfaz de usuario (UI). Entre ellas se incluyen menús y barras de herramientas predeterminadas, marcos de ventanas de documento o ventanas secundarias de interfaz de múltiples documentos (MDI), y marcos de ventanas de herramientas y compatibilidad de acoplamiento.

- Mantener una lista en ejecución de todos los documentos abiertos actualmente en una tabla de documentos en ejecución (RDT) para coordinar la persistencia de los documentos y garantizar que un documento no se puede abrir de más de una manera o de maneras incompatibles.

- Compatibilidad con el enrutamiento de comandos y la interfaz de control de comandos, `IOleCommandTarget` .

- Cargar VSPackages en los momentos adecuados. La carga retrasada de un VSPackage es necesaria para mejorar el rendimiento del shell.

- Administrar determinados servicios compartidos, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> , que proporciona la funcionalidad básica de Shell y <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , que proporciona la funcionalidad básica de ventanas.

- Administrar los archivos de solución (. sln). Las soluciones contienen grupos de proyectos relacionados, similares a los archivos del área de trabajo (. DSW) en Visual C++ 6,0.

- Realizar un seguimiento de la selección, el contexto y la moneda de todo el shell. El shell realiza un seguimiento de los siguientes tipos de elementos:

  - El proyecto actual

  - Elemento de proyecto actual o ItemID el objeto actual <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - La selección actual de la ventana **propiedades** o `SelectionContainer`

  - Los identificadores de contexto de la interfaz de usuario o CmdUIGuids que controlan la visibilidad de los comandos, menús y barras de herramientas.

  - Los elementos activos actualmente, como la ventana activa, el documento y el administrador de deshacer

  - Los atributos de contexto de usuario que controlan la ayuda dinámica

  El shell también media la comunicación entre los VSPackages instalados y los servicios actuales. Admite las características principales del shell y ponerlas a disposición de todos los VSPackages integrados en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Estas características principales incluyen los siguientes elementos:

- Cuadro **de diálogo acerca de** y pantalla de presentación

- Cuadro **de diálogo Agregar nuevo y Agregar elemento existente**

- **Vista de clases** ventana y **Examinador de objetos**

- Cuadro de diálogo **referencias**

- Ventana **esquema del documento**

- Ventana de **Ayuda dinámica**

- **Buscar** y **reemplazar**

- Cuadro de diálogo **Abrir proyecto** y **Abrir archivo** en el menú **nuevo**

- Cuadro de diálogo **Opciones** del menú **herramientas**

- Ventana **propiedades**

- **Explorador de soluciones**

- **Lista de tareas** ventana

- **Cuadro de herramientas**

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
