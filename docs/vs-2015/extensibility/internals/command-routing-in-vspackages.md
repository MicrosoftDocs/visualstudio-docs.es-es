---
title: Enrutamiento de comandos en VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 954d3f25a425652d8adcb31bd36fab06de0d04d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195086"
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un comando se enruta en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] función del contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia afuera hasta el contexto global.  
  
## <a name="in-this-section"></a>En esta sección  
 [Algoritmo de enrutamiento](../../extensibility/internals/command-routing-algorithm.md)  
 Describe el orden de resolución de enrutamiento de comandos.  
  
 [Disponibilidad](../../extensibility/internals/command-availability.md)  
 Describe el enrutamiento de comandos.  
  
 [Comandos y menús que usan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Describe las consideraciones de enrutamiento de comandos entre el código administrado y COM.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)  
 Describe el modelo de cómo puede determinar el foco del contexto de selección del usuario en una ventana.  
  
 [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.
