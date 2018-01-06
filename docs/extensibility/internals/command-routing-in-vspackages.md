---
title: Enrutamiento de comandos en VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90f3d2347f8bf37173f3eb257293b71d706eb0a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
Un comando se enruta en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] basándose en el contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia fuera en el contexto global.  
  
## <a name="in-this-section"></a>En esta sección  
 [Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)  
 Describe el orden de resolución de enrutamiento de comandos.  
  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe el enrutamiento de comandos.  
  
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Se tratan los aspectos en los comandos de enrutamientos entre código administrado y COM.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)  
 Describe el modelo para determinar foco de contexto de selección del usuario en una ventana.  
  
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.