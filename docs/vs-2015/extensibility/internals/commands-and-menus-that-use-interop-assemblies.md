---
title: Los comandos y menús que utilizan ensamblados de interoperabilidad | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 105a4ed0f30991fe656c7f257ca766dd06c150a9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49261721"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos y menús que usan ensamblados de interoperabilidad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage que implemente los comandos de menú y barra de herramientas mediante el uso de ensamblados de interoperabilidad debe:  
  
-   Informar a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE) acerca de los comandos que admite y si están habilitadas actualmente.  
  
-   Cumplir las reglas (contrato) para controlar los comandos.  
  
-   Implementar explícitamente la gestión de comandos mediante el uso del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz.  
  
 El siguiente describe cómo realizar estas tareas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Determinación del estado de los comandos mediante el uso de ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Describe cómo un VSPackage notifica al IDE acerca de los comandos que admite y si están habilitadas actualmente.  
  
 [Contratos de comandos en los ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Proporciona una definición del contrato de comando básico usado por todos los VSPackages, implementación de comandos mediante ensamblados de interoperabilidad  
  
 [Implementación](../../extensibility/internals/command-implementation.md)  
 Proporciona información general de cómo un VSPackage implementa un comando.  
  
 [Registro de controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Describe las entradas del registro necesarias para notificar el IDE que un paquete VSPackage proporciona un controlador de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe los criterios que se usan por el IDE para determinar qué comandos VSPackage están disponibles y qué objeto administra.  
  
 [Adición de elementos de la interfaz de usuario por VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Proporciona información detallada sobre cómo crear una interfaz de usuario que utiliza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] comando soporte técnico.  
  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Información general sobre el proceso que se utiliza para relacionar un objeto con la solicitud de comando correcto.

