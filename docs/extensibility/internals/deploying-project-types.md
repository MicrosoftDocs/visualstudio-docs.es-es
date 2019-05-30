---
title: Implementación de tipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac03682fa1158f5da9c694cf1be5282717c07b55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312174"
---
# <a name="deploy-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala un nuevo agregador de tipo de proyecto (*ProjectAggregator2.dll*) y también un paquete de Windows Installer para la redistribución (*ProjectAggregator2.msi*). Debe usar el nuevo agregador para tipos de proyecto de código administrado. ProjectAggregator2 puede solventar las limitaciones en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregador que impide que los tipos de proyecto de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.

1. Quitar el proyecto NativeHierarchyWrapper de la solución.

2. Quite todos los archivos binarios de NativeHierarchyWrapper de su programa de instalación.

3. Agregar *ProjectAggregator2.msi* a su instalación.