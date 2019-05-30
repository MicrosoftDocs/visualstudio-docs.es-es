---
title: Optimización de menús y comandos de la barra de herramientas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c76e4f37fd77bd35526153bd86d419417a6cdb6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333126"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optimización de comandos de menú y barra de herramientas
La adición de VSPackages y sus comandos correspondientes a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede provocar una interfaz de usuario atestado. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona métodos para ayudar a minimizar la confusión de comando de la interfaz de usuario.

## <a name="in-this-section"></a>En esta sección
- [Puesta a disposición de comandos](../../extensibility/internals/making-commands-available.md)

 Proporciona directrices generales para minimizar la aglomeración de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la interfaz de usuario al agregar los paquetes VSPackage.

- [Instrucciones sobre la selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)

 Proporciona directrices para implementar un paquete VSPackage según el tamaño del conjunto de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.