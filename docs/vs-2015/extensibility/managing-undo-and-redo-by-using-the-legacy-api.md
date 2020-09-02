---
title: Administrar deshacer y rehacer mediante la API heredada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7c2133c75b32e56c1a054740bd829bd04cac97cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194367"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Administración de las fases de reversión y puesta al día mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los editores deben admitir las operaciones de deshacer que permiten a los usuarios invertir sus cambios recientes cuando modifican el código. La mayoría de los editores implementados en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pueden tener soporte de deshacer automáticamente proporcionado por el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la funcionalidad de deshacer para los editores con una o varias vistas.  
  
 [Cómo: Borrar la pila de la fase de reversión](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: Usar la administración vinculada de la fase de reversión](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora administración de deshacer vinculada en el editor.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de la fase de reversión para un editor que admite varias vistas.  
  
## <a name="related-sections"></a>Secciones relacionadas
