---
title: Desactivar las advertencias de compatibilidad para los complementos de control de código fuente . Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22dd3821426aa1dae6265c520ddac60dd93e1c5e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710721"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Cómo: Desactivar las advertencias de compatibilidad para complementos de control de código fuente
Un usuario puede ver varias advertencias de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]compatibilidad al emplear el control de código fuente en . Las advertencias presentadas dependen de las capacidades del complemento de control de código fuente y se pueden deshabilitar como se detalla aquí.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la advertencia: "Para garantizar una integración óptima del control de código fuente con Visual Studio"

- Establezca la siguiente entrada del Registro (añadiendo el valor si es necesario):

   **HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8,0, SourceControl, DontDisplayCheckDotNETCompatible, dword:00000001**

   Esta advertencia se muestra para[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] todos los no plug-ins.

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la advertencia: "El proveedor de control de código fuente instalado no admite todas las capacidades"

- Establezca los dos valores del Registro siguientes (añadiendo los valores si es necesario):

     **HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8,0, SourceControl, WarnedOldMSSCCIProvider, dword:00000000**

    **HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8,0, SourceControl, UseOldSCC, dword:00000001**

     Esta advertencia se muestra si el complemento de control de código fuente no admite explícitamente la reentrada para varios proyectos (es decir, si solo puede proteger un archivo y un proyecto a la vez).

     Lo mejor es apoyar la`SCC_CAP_REENTRANT` reentrada (capacidad); al hacerlo, se eliminará esta advertencia. Sin embargo, si este soporte no es posible, se pueden establecer estas entradas del registro.

## <a name="see-also"></a>Vea también
- [Banderas de capacidad](../extensibility/capability-flags.md)
