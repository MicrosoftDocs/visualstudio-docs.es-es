---
title: Determinar si se va a implementar un VSPackage de control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196794"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>Determinación de si se debe implementar un VSPackage de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta sección se describen las opciones de los complementos de control de código fuente y los paquetes VSPackage de control de código fuente para extender las soluciones de control de código fuente y se proporcionan instrucciones generales sobre cómo elegir una ruta de integración adecuada.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>Solución de control de código fuente pequeña con recursos limitados  
 Si tiene recursos limitados y no se pueden sobrecargar con la sobrecarga de escribir un paquete de control de código fuente, puede crear complementos basados en la API del complemento de control de código fuente. Esto le permite trabajar en paralelo con paquetes de control de código fuente, y puede cambiar entre complementos de control de código fuente y paquetes a petición. Para obtener más información, consulte el [registro y la selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solución de control de código fuente grande con un conjunto de características enriquecidas  
 Si desea implementar una solución de control de código fuente que proporcione un modelo de control de código fuente enriquecido que no se haya capturado correctamente mediante la API del complemento de control de código fuente, considere la posibilidad de usar un paquete de control de código fuente como ruta de acceso de integración. Esto se aplica especialmente si prefiere reemplazar el paquete del adaptador de control de código fuente (que se comunica con los complementos de control de código fuente y proporciona una interfaz de usuario básica de control de código fuente), para que pueda controlar los eventos de control de código fuente de una manera personalizada. Si ya tiene una interfaz de usuario de control de código fuente satisfactoria y desea conservar esa experiencia en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , la opción del paquete de control de código fuente le permite hacer justamente eso. El paquete de control de código fuente no es genérico y está diseñado únicamente para su uso con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 Si desea implementar una solución de control de código fuente que proporcione flexibilidad y control más completo sobre la lógica de control de código fuente y la interfaz de usuario, puede que prefiera la ruta de integración del paquete de control de código fuente. Puede:  
  
1. Registre su propio VSPackage de control de código fuente (consulte [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).  
  
2. Reemplace la interfaz de usuario de control de código fuente predeterminada por su interfaz de usuario personalizada (consulte [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).  
  
3. Especificar glifos que se van a utilizar y controlar Explorador de soluciones eventos de glifo (vea [control de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).  
  
4. Controlar los eventos de edición de consulta y de guardado de consulta (vea consulta de edición de consultas [Guardar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).  
  
## <a name="see-also"></a>Consulte también  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
