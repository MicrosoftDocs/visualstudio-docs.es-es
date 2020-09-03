---
title: Implementación de tipos de proyecto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196878"
---
# <a name="deploying-project-types"></a>Implementación de tipos de proyecto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instala un nuevo agregador de tipo de proyecto (ProjectAggregator2.dll) y también un paquete de Windows Installer para la redistribución (ProjectAggregator2.msi). Debe usar el nuevo agregador para los tipos de proyecto de código administrado. ProjectAggregator2 funciona en torno a las limitaciones del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] agregador de proyectos que evitan que los tipos de proyecto de código administrado funcionen correctamente. En los pasos siguientes se describe cómo cambiar el VSPackage para usar el nuevo agregador.  
  
1. Quite el proyecto NativeHierarchyWrapper de la solución.  
  
2. Quite todos los archivos binarios de NativeHierarchyWrapper de la configuración.  
  
3. Agregue ProjectAggregator2.msi a la configuración.
