---
title: Comandos y menús que utilizan ensamblados de interoperabilidad | Microsoft Docs
description: Obtenga información sobre las tareas que se deben completar al implementar comandos de menús y barras de herramientas en un VSPackage mediante ensamblados de interoperabilidad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5a487c2fe6f97e338924a0b8c682f9dd9798571
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057239"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos y menús que utilizan ensamblados de interoperabilidad
Un VSPackage que implementa comandos de menú y de barra de herramientas mediante ensamblados de interoperabilidad debe:

- Informe al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) acerca de los comandos que admite y si están habilitados actualmente.

- Siga las reglas (contrato) para controlar los comandos.

- Implemente explícitamente el control de comandos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz o.

  En la siguiente sección se describe cómo realizar estas tareas.

## <a name="in-this-section"></a>En esta sección
- [Determinar el estado del comando mediante ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)

 Describe cómo un VSPackage notifica al IDE los comandos que admite y si están habilitados actualmente.

- [Contratos de comandos en ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)

 Proporciona una definición del contrato de comando básico utilizado por todos los paquetes de comandos de implementación de VSPackages que utilizan ensamblados de interoperabilidad.

- [Implementación de comandos](../../extensibility/internals/command-implementation.md)

 Proporciona información general sobre cómo un VSPackage implementa un comando.

- [Registrar controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)

 Describe las entradas del registro necesarias para notificar al IDE que un VSPackage proporciona un controlador de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Disponibilidad de comandos](../../extensibility/internals/command-availability.md)

 Describe los criterios que usa el IDE para determinar qué comandos de VSPackage están disponibles y qué objeto los controla.

- [Cómo agrega VSPackages los elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Proporciona detalles sobre cómo crear una interfaz de usuario que use la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compatibilidad con comandos.

- [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Información general del proceso utilizado para relacionar un objeto con la solicitud de comando correcta.
