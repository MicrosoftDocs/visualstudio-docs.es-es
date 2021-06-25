---
title: Desactivar las advertencias de los complementos de control de código fuente
description: Un usuario puede ver varias advertencias de compatibilidad al emplear el control de código fuente en Visual Studio. Obtenga información sobre cómo deshabilitar estas advertencias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ced04b09f8d4442cf0769ef503ee52772eccc0f6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905753"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Cómo: Desactivar las advertencias de compatibilidad para los complementos de control de código fuente

Un usuario puede ver varias advertencias de compatibilidad al emplear el control de código fuente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Las advertencias presentadas dependen de las funciones del complemento de control de código fuente y se pueden deshabilitar como se detalla aquí.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la advertencia: "Para garantizar una integración óptima del control de código fuente con Visual Studio"

- Establezca la siguiente entrada del Registro (agregando el valor si es necesario):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = dword:00000001**

   Esta advertencia se muestra para todos los complementos que no [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] son de .

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la advertencia: "El proveedor de control de código fuente instalado no admite todas las funcionalidades"

- Establezca los dos valores del Registro siguientes (si es necesario agregar los valores):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = dword:000000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = dword:00000001**

     Esta advertencia se muestra si el complemento de control de código fuente no admite explícitamente la reenlazancia para varios proyectos (es decir, si solo puede comprobar un archivo y un proyecto a la vez).

     Es mejor admitir la reenlazancia `SCC_CAP_REENTRANT` (funcionalidad); si lo hace, se quitará esta advertencia. Sin embargo, si esta compatibilidad no es posible, se pueden establecer estas entradas del Registro.

## <a name="see-also"></a>Consulta también

- [Marcas de funcionalidad](../extensibility/capability-flags.md)
