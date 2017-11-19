---
title: "Determinar si se debe implementar un VSPackage de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 808f2fda26046962eada377f8a204351adef19bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinar si se debe implementar un VSPackage de Control de código fuente
Esta sección explican las opciones de los complementos de control de código fuente y el control de código fuente VSPackages para extender el control de código fuente soluciones y proporciona instrucciones generales acerca de cómo elegir una ruta de acceso de integración adecuado.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solución de Control de origen pequeñas con recursos limitados  
 Si dispone de recursos limitados y no puede estar sobrecargado con la sobrecarga de la escritura de un paquete de control de código fuente, puede crear complementos en función de la API de complementos de Control de código fuente. Esto le permite trabajar junto a los paquetes de control de código fuente, y puede cambiar entre los complementos de control de código fuente y los paquetes a petición. Para obtener más información, consulte [registro y la selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solución de Control de código fuente grande con un conjunto enriquecido de características  
 Si desea implementar una solución de control de origen que proporciona un modelo de control de código fuente completo que no se captura adecuadamente mediante la API de complemento de Control de origen, puede considerar un paquete de control de código fuente como la ruta de acceso de integración. Esto se aplica especialmente si en su lugar debe reemplazar el paquete de adaptador de Control de origen (que se comunica con los complementos de control de código fuente y proporciona un control de código fuente básico UI) con su propia manera que pueda controlar los eventos de control de código fuente de una manera personalizada. Si ya tiene un origen satisfactorio controlar la interfaz de usuario y desea conservar esa experiencia en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la opción de paquete de control de código fuente le permite hacer exactamente eso. El paquete de control de código fuente no es genérico y está diseñado únicamente para su uso con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Si desea implementar una solución de control de origen que proporciona flexibilidad y un mayor control sobre la interfaz de usuario y la lógica de control de código fuente, puede ser preferible la ruta de integración de paquete de control de código fuente. Puede realizar lo siguiente:  
  
1.  Registrar su propio control de código fuente VSPackage (vea [registro y la selección de](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Reemplazar el control de código fuente predeterminada interfaz de usuario con la interfaz de usuario personalizado (vea [la interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Especifique los glifos que se utilizará y controlar los eventos de glifo del explorador de soluciones (vea [glifo Control](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Controlar eventos de consulta editar y guardar consultas (consulte [consulta Editar consulta guardar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Vea también  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)