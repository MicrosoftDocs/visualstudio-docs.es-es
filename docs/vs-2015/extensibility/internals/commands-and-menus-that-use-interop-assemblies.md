---
title: Comandos y menús que utilizan ensamblados de interoperabilidad | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, using interop assemblies
- interop assemblies, using in commands and menus
- commands, handling using interop assemblies
- command handling with interop assemblies
ms.assetid: 8f4af525-39e5-4e69-92c8-d3efabe80bb2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ad6b324953914df7103d0dec7371199e3cbbd937
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195053"
---
# <a name="commands-and-menus-that-use-interop-assemblies"></a>Comandos y menús que usan ensamblados de interoperabilidad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage que implementa comandos de menú y de barra de herramientas mediante ensamblados de interoperabilidad debe:  
  
- Informe al [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno de desarrollo integrado (IDE) acerca de los comandos que admite y si están habilitados actualmente.  
  
- Siga las reglas (contrato) para controlar los comandos.  
  
- Implemente explícitamente el control de comandos mediante la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaz o.  
  
  A continuación se describe cómo realizar estas tareas.  
  
## <a name="in-this-section"></a>En esta sección  
 [Determinación del estado de los comandos mediante ensamblados de interoperabilidad](../../extensibility/internals/determining-command-status-by-using-interop-assemblies.md)  
 Describe cómo un VSPackage notifica al IDE los comandos que admite y si están habilitados actualmente.  
  
 [Contratos de comandos en los ensamblados de interoperabilidad](../../extensibility/internals/command-contracts-in-interop-assemblies.md)  
 Proporciona una definición del contrato de comandos básico que utilizan todos los comandos que implementan comandos mediante ensamblados de interoperabilidad.  
  
 [Implementación](../../extensibility/internals/command-implementation.md)  
 Proporciona información general sobre cómo un VSPackage implementa un comando.  
  
 [Registro de controladores de comandos de ensamblado de interoperabilidad](../../extensibility/internals/registering-interop-assembly-command-handlers.md)  
 Describe las entradas del registro necesarias para notificar al IDE que un VSPackage proporciona un controlador de comandos.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe los criterios que usa el IDE para determinar qué comandos de VSPackage están disponibles y qué objeto los controla.  
  
 [Cómo VSPackages agrega elementos de la interfaz de usuario](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Proporciona detalles sobre cómo crear una interfaz de usuario que use la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] compatibilidad con comandos.  
  
 [Enrutamiento de comandos en VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Información general del proceso utilizado para relacionar un objeto con la solicitud de comando correcta.
