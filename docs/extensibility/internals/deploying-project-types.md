---
title: Implementar tipos de proyecto | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2171a940951d828df358d09dae5fec68b6475e4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-project-types"></a>Implementar tipos de proyecto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala un nuevo agregador de tipo de proyecto (ProjectAggregator2.dll) y también un paquete de Windows Installer para su redistribución (ProjectAggregator2.msi). Debe usar el nuevo agregador para tipos de proyectos de código administrado. ProjectAggregator2 funciona alternativas limitaciones el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyecto agregador que impiden que los tipos de proyectos de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.  
  
1.  Quitar el proyecto NativeHierarchyWrapper de la solución.  
  
2.  Quite todos los archivos binarios de NativeHierarchyWrapper de su instalación.  
  
3.  Agregar ProjectAggregator2.msi a su instalación.