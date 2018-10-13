---
title: Administración de deshacer y rehacer mediante la API heredada | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 838c0ddf-fdf3-4df1-8d21-79610b8ba0b1
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb2ff049635d75608114be380c9697faf0585725
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177897"
---
# <a name="managing-undo-and-redo-by-using-the-legacy-api"></a>Administración de deshacer y rehacer mediante la API heredada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los editores deben admitir las operaciones de deshacer que permiten a los usuarios revertir sus cambios recientes cuando modifica el código. La mayoría de editores implementados en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] puede tener soporte para deshacer automáticamente proporcionada por el entorno de desarrollo integrado (IDE).  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Implementar la administración de la fase de reversión](../extensibility/how-to-implement-undo-management.md)  
 Proporciona la capacidad de deshacer para los editores con una o varias vistas.  
  
 [Cómo: Borrar la pila de la fase de reversión](../extensibility/how-to-clear-the-undo-stack.md)  
 Describe cómo borrar una pila de deshacer.  
  
 [Cómo: Usar la administración vinculada de la fase de reversión](../extensibility/how-to-use-linked-undo-management.md)  
 Incorpora la administración de la fase de reversión vinculado en el editor.  
  
## <a name="reference"></a>Referencia  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>  
 Proporciona administración de la fase de reversión para un editor que admite varias vistas.  
  
## <a name="related-sections"></a>Secciones relacionadas

