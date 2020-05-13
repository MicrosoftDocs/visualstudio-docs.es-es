---
title: Fundamentos de la integración de Control de código fuente ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705231"
---
# <a name="source-control-integration-essentials"></a>Conceptos básicos de la integración del control de código fuente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Admite dos tipos de integración de control de código fuente: un complemento de control de código fuente que proporciona funcionalidad básica y se compila mediante la API de complemento de Control de código fuente (anteriormente conocida como la API de MSSCCI) y una solución de integración de control de código fuente basada en VSPackage que proporciona una funcionalidad más sólida.

## <a name="source-control-plug-in"></a>Complemento control de código fuente
 Un complemento de Control de código fuente se escribe como un archivo DLL que implementa la API de complemento de Control de código fuente. La funcionalidad de integración de registro y control de código fuente se proporciona a través de la API. Este enfoque es más fácil de implementar que un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] control de código fuente VSPackage y usa la interfaz de usuario (UI) para la mayoría de las operaciones de control de código fuente.

 Para implementar un complemento de control de código fuente mediante la API de complemento de Control de código fuente, siga estos pasos:

1. Cree un archivo DLL que implemente las funciones especificadas en [Complementos](../../extensibility/source-control-plug-ins.md)de Control de código fuente .

2. Registre el archivo DLL realizando las entradas de registro adecuadas, como se describe en [Cómo: instalar un complemento](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)de Control de código fuente .

3. Cree una interfaz de usuario auxiliar y muésela cuando se lo solicite el paquete de adaptador de Control de código fuente (el componente que controla la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funcionalidad de control de código fuente a través de complementos de control de código fuente).

   Para obtener más información, consulte Creación de un complemento de [control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md).

## <a name="source-control-vspackage"></a>Control de código fuente VSPackage
 Una implementación de VSPackage de control de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fuente le permite desarrollar un reemplazo personalizado para la interfaz de usuario del control de código fuente. Este enfoque proporciona un control completo sobre la integración del control de código fuente, pero requiere que proporcione los elementos de la interfaz de usuario e implemente las interfaces de control de código fuente que, de lo contrario, se proporcionarían bajo el enfoque de complemento.

 Para implementar un control de código fuente VSPackage, debe:

1. Cree y registre su propio control de código fuente VSPackage, como se describe en [Registro y selección](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).

2. Reemplace la interfaz de usuario de control de código fuente predeterminada por la interfaz de usuario personalizada. Consulte [Interfaz de usuario personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).

3. Especifique los pictogramas que se van a usar y controle los eventos de glifo del Explorador de **soluciones.** Consulte [Control de pictogramas](../../extensibility/internals/glyph-control-source-control-vspackage.md).

4. Controlar eventos de edición de consulta y guardado de consulta, como se muestra en [Query Edit Query Save](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).

   Para obtener más información, vea [Crear un VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md)de control de código fuente .

## <a name="see-also"></a>Vea también
- [Información general](../../extensibility/internals/source-control-integration-overview.md)
- [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [Creación de un VSPackage de control de código fuente](../../extensibility/internals/creating-a-source-control-vspackage.md)
