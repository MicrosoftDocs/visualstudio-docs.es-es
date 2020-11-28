---
title: Enrutamiento de comandos en VSPackages | Microsoft Docs
description: Obtenga información sobre el enrutamiento de comandos en VSPackages y cómo se enrutan los comandos en función del contexto en el que se ejecutan en Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8168fbe3ad5ba9b1b332aebc4675ecd8e752ee7e
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305216"
---
# <a name="command-routing-in-vspackages"></a>Enrutamiento de comandos en VSPackages
Un comando se enruta en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] función del contexto en el que se ejecuta. Se enruta desde el contexto inicial hacia afuera hasta el contexto global.

## <a name="in-this-section"></a>En esta sección
- [Algoritmo de enrutamiento de comandos](../../extensibility/internals/command-routing-algorithm.md)

 Describe el orden de resolución de enrutamiento de comandos.

- [Disponibilidad de comandos](../../extensibility/internals/command-availability.md)

 Describe el enrutamiento de comandos.

- [Comandos y menús que utilizan ensamblados de interoperabilidad](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Describe las consideraciones de enrutamiento de comandos entre el código administrado y COM.

## <a name="related-sections"></a>Secciones relacionadas
- [Objetos de contexto de selección](../../extensibility/internals/selection-context-objects.md)

 Describe el modelo de cómo puede determinar el foco del contexto de selección del usuario en una ventana.

- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.
