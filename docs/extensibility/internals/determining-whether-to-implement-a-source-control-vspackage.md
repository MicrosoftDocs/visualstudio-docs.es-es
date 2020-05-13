---
title: Determinar si se debe implementar un VSPackage de control de código fuente ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708723"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Determinar si se debe implementar un control de código fuente VSPackage
En esta sección se explican las opciones de complementos de control de código fuente y VSPackages de control de código fuente para ampliar las soluciones de control de código fuente y proporciona instrucciones generales sobre cómo elegir una ruta de acceso de integración adecuada.

## <a name="small-source-control-solution-with-limited-resources"></a>Pequeña solución de control de código fuente con recursos limitados
 Si tiene recursos limitados y no se puede cargar con la sobrecarga de escribir un paquete de control de código fuente, puede crear complementos basados en API de complementode de Control de código fuente. Para obtener más información, consulte [Registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Solución de control de código fuente grande con un amplio conjunto de características
 Si desea implementar una solución de control de código fuente que proporciona un modelo de control de código fuente enriquecido que no se captura adecuadamente mediante la API de complemento de Control de código fuente, puede considerar un paquete de control de código fuente como la ruta de acceso de integración. Esto se aplica especialmente si prefiere reemplazar el paquete de adaptador de Control de código fuente (que se comunica con complementos de control de código fuente y proporciona una interfaz de usuario de control de código fuente básica) con la suya propia para que pueda controlar los eventos de control de código fuente de una manera personalizada. Si ya tiene una interfaz de usuario de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]control de código fuente satisfactoria y desea conservar esa experiencia en , la opción de paquete de control de código fuente le permite hacer justo eso. El paquete de control de código fuente no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es genérico y está diseñado únicamente para su uso con IDE.

 Si desea implementar una solución de control de código fuente que proporciona flexibilidad y un control más completo sobre la lógica de control de código fuente y la interfaz de usuario, puede preferir la ruta de integración del paquete de control de código fuente. Puede:

1. Registre su propio control de código fuente VSPackage (consulte [Registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)).

2. Reemplace la interfaz de usuario de control de código fuente predeterminada por la interfaz de usuario personalizada (consulte [Interfaz](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)de usuario personalizada ).

3. Especifique los pictogramas que se van a usar y controle los eventos de glifo del Explorador de soluciones (consulte [Control de pictogramas](../../extensibility/internals/glyph-control-source-control-vspackage.md)).

4. Controlar eventos de edición de consultay guardado de consultas (consulte [Guardar consulta de edición](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)de consultas ).

## <a name="see-also"></a>Vea también
- [Crear un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
