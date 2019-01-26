---
title: Implementación de tipos de proyecto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b42e4f879352a6edaf9171296b282accd9b1ae3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009913"
---
# <a name="deploy-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala un nuevo agregador de tipo de proyecto (*ProjectAggregator2.dll*) y también un paquete de Windows Installer para la redistribución (*ProjectAggregator2.msi*). Debe usar el nuevo agregador para tipos de proyecto de código administrado. ProjectAggregator2 puede solventar las limitaciones en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregador que impide que los tipos de proyecto de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.  
  
1.  Quitar el proyecto NativeHierarchyWrapper de la solución.  
  
2.  Quite todos los archivos binarios de NativeHierarchyWrapper de su programa de instalación.  
  
3.  Agregar *ProjectAggregator2.msi* a su instalación.