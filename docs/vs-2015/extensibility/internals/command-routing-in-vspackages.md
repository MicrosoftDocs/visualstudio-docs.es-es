---
title: Enrutamiento de comandos en VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e945b16134debce8ec23ed15e5c9b0ca436e5bd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581450"
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [enrutamiento de comandos en VSPackages](https://docs.microsoft.com/visualstudio/extensibility/internals/command-routing-in-vspackages).  
  
Un comando se enruta en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] según el contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia el exterior para el contexto global.  
  
## <a name="in-this-section"></a>En esta sección  
 [Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)  
 Describe el orden de resolución de enrutamiento de comandos.  
  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe el enrutamiento de comandos.  
  
 [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Se describen las consideraciones en los comandos de enrutamientos entre código administrado y COM.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)  
 Describe el modelo de cómo determinar el enfoque de contexto de selección del usuario en una ventana.  
  
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.

