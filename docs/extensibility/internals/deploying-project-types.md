---
title: Implementar tipos de proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12af8607dd1561a4a2561cc688d2bb4ba0f07c88
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="deploying-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala un nuevo agregador de tipo de proyecto (ProjectAggregator2.dll) y también un paquete de Windows Installer para su redistribución (ProjectAggregator2.msi). Debe usar el nuevo agregador para tipos de proyectos de código administrado. ProjectAggregator2 funciona alternativas limitaciones el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregador que impiden que los tipos de proyectos de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.  
  
1.  Quitar el proyecto NativeHierarchyWrapper de la solución.  
  
2.  Quite todos los archivos binarios de NativeHierarchyWrapper de su instalación.  
  
3.  Agregar ProjectAggregator2.msi a su instalación.