---
title: Enrutamiento de comandos en VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a5f884873e714c12708780a0e52f5f5574727fb
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512940"
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
Un comando se enruta en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] según el contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia el exterior para el contexto global.  
  
## <a name="in-this-section"></a>En esta sección  
 [Algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md)  
 Describe el orden de resolución de enrutamiento de comandos.  
  
 [Disponibilidad de los comandos](../../extensibility/internals/command-availability.md)  
 Describe el enrutamiento de comandos.  
  
 [Los comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Se describen las consideraciones en los comandos de enrutamientos entre código administrado y COM.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)  
 Describe el modelo de cómo determinar el enfoque de contexto de selección del usuario en una ventana.  
  
 [Los comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.