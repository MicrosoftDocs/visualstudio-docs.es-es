---
title: Ocultar propiedades que tienen propiedades secundarias | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d20b865c6f07d76320a7df8402810c82869ddfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822391"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ocultar propiedades que tienen propiedades secundarias
Desea ocultar las propiedades que tienen propiedades secundarias:  
  
- Si tiene proyectos anidados en los que el proyecto primario controla mediante programación algunos aspectos del proyecto secundario.  
  
- Si utiliza un control con un diseñador especializado y no desea conceder a los desarrolladores acceso completo a todas las propiedades del control.  
  
- Si tiene la propiedad del ámbito de un objeto y desea limitar la vista de propiedades.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Para ocultar propiedades que tienen propiedades secundarias  
  
1. Establezca el `pfDisplay` parámetro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> en `FALSE` .  
  
2. Establezca el `pfHide` parámetro de <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> en `TRUE` .  
  
## <a name="see-also"></a>Consulte también  
 [Cuadrícula para mostrar de Propiedades](../extensibility/internals/properties-display-grid.md)