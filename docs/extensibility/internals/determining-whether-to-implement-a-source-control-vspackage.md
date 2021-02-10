---
title: Cuándo implementar un VSPackage de control de código fuente
description: Obtenga información sobre las opciones de los complementos de control de código fuente y los paquetes VSPackage de control de código fuente que están disponibles para extender las soluciones de control de código fuente de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 80c86a8ab40b74d1b8f2838e3bf4359af41b0fc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963437"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinar si se va a implementar un VSPackage de control de código fuente

En esta sección se describen las opciones de los complementos de control de código fuente y los paquetes VSPackage de control de código fuente para extender las soluciones de control de código fuente y se proporcionan instrucciones generales sobre cómo elegir una ruta de integración adecuada.

## <a name="small-source-control-solution-with-limited-resources"></a>Solución de control de código fuente pequeña con recursos limitados

 Si tiene recursos limitados y no se pueden sobrecargar con la sobrecarga de escribir un paquete de control de código fuente, puede crear complementos basados en la API del complemento de control de código fuente. Esto le permite trabajar en paralelo con paquetes de control de código fuente y puede cambiar entre complementos de control de código fuente y paquetes a petición. Para obtener más información, consulte el [registro y la selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solución de control de código fuente grande con un conjunto de características enriquecidas

 Si desea implementar una solución de control de código fuente que proporcione un modelo de control de código fuente enriquecido que no se haya capturado correctamente mediante la API del complemento de control de código fuente, considere la posibilidad de usar un paquete de control de código fuente como ruta de acceso de integración. Esto se aplica especialmente si prefiere reemplazar el paquete del adaptador de control de código fuente (que se comunica con los complementos de control de código fuente y proporciona una interfaz de usuario básica de control de código fuente), para que pueda controlar los eventos de control de código fuente de una manera personalizada. Si ya tiene una interfaz de usuario de control de código fuente satisfactoria y desea conservar esa experiencia en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , la opción del paquete de control de código fuente le permite hacer justamente eso. El paquete de control de código fuente no es genérico y está diseñado únicamente para su uso con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

 Si desea implementar una solución de control de código fuente que proporcione flexibilidad y control más completo sobre la lógica de control de código fuente y la interfaz de usuario, puede que prefiera la ruta de integración del paquete de control de código fuente. Puede:

1. Registre su propio VSPackage de control de código fuente (consulte [registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Reemplace la interfaz de usuario de control de código fuente predeterminada por su interfaz de usuario personalizada (consulte [interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)).

3. Especificar glifos que se van a utilizar y controlar Explorador de soluciones eventos de glifo (vea [control de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Controlar los eventos de edición de consulta y de guardado de consulta (vea consulta de edición de consultas [Guardar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Vea también

- [Crear un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
