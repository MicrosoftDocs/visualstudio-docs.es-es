---
title: Enrutamiento de comandos en VSPackages ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing, Visual Studio SDK
ms.assetid: a9c7f9ae-3594-4557-a314-8cf76f5f8772
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 957ddcca46365a882609c15c96d666c2848ace6c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709554"
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
Un comando se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] enruta en función del contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia el contexto global.

## <a name="in-this-section"></a>En esta sección
- [Algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md)

 Describe el orden de resolución de enrutamiento de comandos.

- [Disponibilidad de comandos](../../extensibility/internals/command-availability.md)

 Describe el enrutamiento de comandos.

- [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Describe las consideraciones en los comandos de enrutamiento entre código administrado y COM.

## <a name="related-sections"></a>Secciones relacionadas
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)

 Describe el modelo de cómo puede determinar el foco de contexto de selección del usuario en una ventana.

- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.
