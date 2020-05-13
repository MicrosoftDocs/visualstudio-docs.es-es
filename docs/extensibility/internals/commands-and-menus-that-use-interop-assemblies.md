---
title: Comandos y menús que utilizan ensamblados de interoperabilidad ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6c381abe9b4c6ea2a58342e185d7427fa56a180
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709485"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos y menús que utilizan ensamblados de interoperabilidad
Un VSPackage que implementa comandos de menú y barra de herramientas mediante el uso de ensamblados de interoperabilidad debe:

- Informar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] al entorno de desarrollo integrado (IDE) sobre los comandos que admite y si están habilitados actualmente.

- Adherirse a las reglas (contrato) para el manejo de comandos.

- Implemente explícitamente el control <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> comandos mediante la interfaz o.

  En la siguiente sección se describe cómo realizar estas tareas.

## <a name="in-this-section"></a>En esta sección
- [Determinar el estado del comando mediante ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Describe cómo un VSPackage notifica al IDE sobre qué comandos admite y si están habilitados actualmente.

- [Contratos de comandos en ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Proporciona una definición del contrato de comandos básico utilizado por todos los VSPackages que implementan comandos mediante ensamblados de interoperabilidad.

- [Implementación del comando](../../extensibility/internals/command-implementation.md)

 Proporciona información general sobre cómo un VSPackage implementa un comando.

- [Registrar controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Describe las entradas del Registro necesarias para notificar al IDE que un VSPackage proporciona un controlador de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Disponibilidad de comandos](../../extensibility/internals/command-availability.md)

 Describe los criterios que usa el IDE para determinar qué comandos de VSPackage están disponibles y qué objeto los controla.

- [Cómo VSPackages agregan elementos de interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Proporciona detalles sobre cómo crear [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una interfaz de usuario que usa compatibilidad con comandos.

- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Visión general del proceso utilizado para relacionar un objeto con la solicitud de comando correcta.
