---
title: Implementación de tipos de proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708784"
---
# <a name="deploy-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala un nuevo agregador de tipo de proyecto (*ProjectAggregator2.dll*) y también un paquete de Windows Installer para su redistribución (*ProjectAggregator2.msi*). Debe usar el nuevo agregador para los tipos de proyecto de código administrado. ProjectAggregator2 se endosa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de las limitaciones en el agregador de proyectos que impide que los tipos de proyecto de código administrado funcionen correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.

1. Quite el proyecto NativeHierarchyWrapper de la solución.

2. Quite los archivos binarios NativeHierarchyWrapper de la configuración.

3. Agregue *ProjectAggregator2.msi* a la configuración.
