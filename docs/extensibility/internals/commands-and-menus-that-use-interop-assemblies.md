---
title: Los comandos y menús que utilizan ensamblados de interoperabilidad | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2212d9eb38487bf824fd8df3c497d9f256379c10
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907812"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Los comandos y menús que utilizan ensamblados de interoperabilidad
Un VSPackage que implemente los comandos de menú y barra de herramientas mediante el uso de ensamblados de interoperabilidad debe:  
  
- Informar a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) acerca de los comandos que admite y si están habilitadas actualmente.  
  
- Cumplir las reglas (contrato) para controlar los comandos.  
  
- Implementar explícitamente la gestión de comandos mediante el uso del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz.  
  
  La siguiente sección describe cómo realizar estas tareas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Determinar el estado del comando mediante el uso de ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Describe cómo un VSPackage notifica al IDE acerca de los comandos que admite y si están habilitadas actualmente.  
  
 [Contratos de comandos en los ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Proporciona una definición del contrato de comando básico usado por todos los VSPackages, implementación de comandos mediante ensamblados de interoperabilidad.
  
 [Implementación de comandos](../../extensibility/internals/command-implementation.md)  
 Proporciona información general de cómo un VSPackage implementa un comando.  
  
 [Registrar controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Describe las entradas del registro necesarias para notificar el IDE que un paquete VSPackage proporciona un controlador de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Disponibilidad de los comandos](../../extensibility/internals/command-availability.md)  
 Describe los criterios que se usan por el IDE para determinar qué comandos VSPackage están disponibles y qué objeto administra.  
  
 [Cómo VSPackages agregar elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Proporciona información detallada sobre cómo crear una interfaz de usuario que utiliza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comando soporte técnico.  
  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Información general sobre el proceso que se utiliza para relacionar un objeto con la solicitud de comando correcto.