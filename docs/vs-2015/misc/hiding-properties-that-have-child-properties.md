---
title: Ocultar propiedades que tienen propiedades secundarias | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], hiding
- Properties window, hiding properties that have child properties
ms.assetid: 6003607e-fc19-4bf9-a299-9f6adf8e92eb
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: bd340b748311bbb257ed0c4bbfe7b972cbf7beb9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579476"
---
# <a name="hiding-properties-that-have-child-properties"></a>Ocultar propiedades que tienen propiedades secundarias
¿Desea ocultar las propiedades que tienen propiedades secundarias:  
  
-   Si tiene proyectos anidados en el proyecto principal mediante programación controla algunos aspectos del proyecto secundario.  
  
-   Si usa un control con un diseñador especializado y no desea proporcionar a los desarrolladores acceso total a todas las propiedades del control.  
  
-   Si tiene la propiedad de ámbito de un objeto y desea limitar la vista de propiedades.  
  
### <a name="to-hide-properties-that-have-child-properties"></a>Para ocultar las propiedades que tienen propiedades secundarias  
  
1.  Establecer el `pfDisplay` parámetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> a `FALSE`.  
  
2.  Establecer el `pfHide` parámetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> a `TRUE`.  
  
## <a name="see-also"></a>Vea también  
 [Cuadrícula para mostrar de Propiedades](../extensibility/internals/properties-display-grid.md)