---
title: Optimización de los comandos de menú y barra de herramientas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], menus
- commands [Visual Studio], toolbars
- menus [Visual Studio SDK], commands
- menu commands, implementing
- toolbars [Visual Studio], commands
ms.assetid: 8385f1a6-1e98-4dca-83d2-fcbed7177242
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4932a4404c3d76b089468864f84d011524e9cfa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706918"
---
# <a name="optimizing-menu-and-toolbar-commands"></a>Optimización de comandos de menú y barra de herramientas
La adición de VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y sus comandos correspondientes a puede provocar una interfaz de usuario concurrido. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona maneras de ayudar a minimizar la confusión de comandos de la interfaz de usuario.

## <a name="in-this-section"></a>En esta sección
- [Puesta a disposición de comandos](../../extensibility/internals/making-commands-available.md)

 Proporciona directrices generales para minimizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el hacinamiento de la interfaz de usuario al agregar VSPackages.

- [Instrucciones sobre la selección de ubicación](../../extensibility/internals/command-placement-guidelines.md)

 Proporciona instrucciones específicas para implementar un VSPackage según el tamaño del conjunto de comandos.

## <a name="related-sections"></a>Secciones relacionadas
- [Comandos, menús y barras de herramientas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica cómo crear una interfaz de usuario que incluya menús, barras de herramientas y cuadros combinados de comandos.
