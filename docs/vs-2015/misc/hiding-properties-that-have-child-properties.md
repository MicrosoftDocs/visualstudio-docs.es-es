---
title: Ocultar propiedades que tienen propiedades secundarias | Documentos de Microsoft
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
ms.openlocfilehash: 8bc6510936e25e61ef47bb813b77e6efbf063573
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58999713"
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