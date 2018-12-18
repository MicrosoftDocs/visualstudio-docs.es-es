---
title: Implementación de tipos de proyecto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0a1da27c22f2675042ecd03ffe092c209eaa1bbc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51729746"
---
# <a name="deploying-project-types"></a>Implementación de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instala un nuevo agregador de tipo de proyecto (ProjectAggregator2.dll) y también un paquete de Windows Installer para la redistribución (ProjectAggregator2.msi). Debe usar el nuevo agregador para tipos de proyecto de código administrado. ProjectAggregator2 funciona alternativas limitaciones en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proyecto agregador que impiden que los tipos de proyecto de código administrado funciona correctamente. Los pasos siguientes describen cómo cambiar el VSPackage para usar el nuevo agregador.  
  
1.  Quitar el proyecto NativeHierarchyWrapper de la solución.  
  
2.  Quite todos los archivos binarios de NativeHierarchyWrapper de su programa de instalación.  
  
3.  Agregar ProjectAggregator2.msi a su instalación.

