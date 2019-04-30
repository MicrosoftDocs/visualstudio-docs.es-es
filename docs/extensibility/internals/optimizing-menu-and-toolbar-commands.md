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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a3fb7b44f0e21c564bc9bef26d5aa158d43091
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909338"
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