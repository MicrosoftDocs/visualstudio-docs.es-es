---
title: Determina si se debe implementar un VSPackage de Control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3bef6030b6a21eeda708a5258c47c9dfdcfc0a3
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497318"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinar si se debe implementar un VSPackage de control de código fuente
Esta sección explican las opciones de los complementos de control de código fuente y control de código fuente VSPackages para extender soluciones y ofrece orientaciones sobre cómo elegir una ruta de acceso adecuada de integración de control de código fuente.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solución de control de origen pequeñas con recursos limitados  
 Si dispone de recursos limitados y no puede estar sobrecargado con la sobrecarga de la escritura de un paquete de control de código fuente, puede crear complementos en función de API de complemento de Control de código fuente. Si lo hace, le permite trabajar en paralelo con paquetes de control de código fuente, y puede cambiar entre los complementos de control de código fuente y los paquetes a petición. Para obtener más información, consulte [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solución de control de código fuente grandes con un amplio conjunto de características  
 Si desea implementar una solución de control de origen que proporciona un modelo de control de código fuente completo que no se captura adecuadamente mediante la API de complemento de Control de código fuente, puede considerar un paquete de control de código fuente como la ruta de acceso de integración. Esto se aplica especialmente si en su lugar reemplazaría el paquete de adaptador de Control de código fuente (que se comunica con los complementos de control de código fuente y proporciona un control de código fuente básicos la interfaz de usuario) con su propia manera que pueda controlar los eventos de control de código fuente de una manera personalizada. Si ya tiene un origen satisfactorio controlar la interfaz de usuario y desea conservar esa experiencia en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la opción de paquete de control de código fuente le permite hacer exactamente eso. El paquete de control de código fuente no es genérico y está diseñado únicamente para su uso con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 Si desea implementar una solución de control de origen que proporciona flexibilidad y un mayor control sobre la interfaz de usuario y la lógica de control de código fuente, prefiere la ruta de integración de paquete de control de origen. Puede realizar lo siguiente:  
  
1.  Registrar su propio control de código fuente VSPackage (consulte [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2.  Reemplace el control de código fuente de forma predeterminada la interfaz de usuario con la interfaz de usuario personalizada (consulte [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3.  Especifique los glifos que se utilizará y controlar los eventos de glifo del explorador de soluciones (consulte [control glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4.  Controlar eventos de consulta de editar y guardar la consulta (vea [para guardar la consulta Editar consulta](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Vea también  
 [Crear un control de código fuente complemento](../../extensibility/internals/creating-a-source-control-plug-in.md)