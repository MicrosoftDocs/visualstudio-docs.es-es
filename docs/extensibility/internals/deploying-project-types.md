---
title: Implementación de tipos de proyecto | Microsoft Docs
description: Aprenda a implementar tipos de proyecto de código administrado mediante un nuevo agregador de tipo de proyecto y Windows Installer paquete para la redistribución, en el SDK de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090998"
---
# <a name="deploy-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala un nuevo agregador de tipo de proyecto (*ProjectAggregator2.dll*) y también un paquete de Windows Installer para la redistribución (*ProjectAggregator2.msi*). Debe usar el nuevo agregador para los tipos de proyecto de código administrado. ProjectAggregator2 funciona en torno a las limitaciones del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregador de proyectos que evitan que los tipos de proyecto de código administrado funcionen correctamente. En los pasos siguientes se describe cómo cambiar el VSPackage para usar el nuevo agregador.

1. Quite el proyecto NativeHierarchyWrapper de la solución.

2. Quite todos los archivos binarios de NativeHierarchyWrapper de la configuración.

3. Agregue *ProjectAggregator2.msi* a la configuración.
