---
title: Desactivar advertencias de complementos de control de código fuente
description: Un usuario puede ver varias advertencias de compatibilidad al usar el control de código fuente en Visual Studio. Obtenga información sobre cómo deshabilitar estas advertencias.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ae293f92d8de3aec2137f26999a3315bb5dc5c08
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880741"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Desactivar advertencias de compatibilidad para complementos de control de código fuente

Un usuario puede ver varias advertencias de compatibilidad al utilizar el control de código fuente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Las advertencias presentadas dependen de las capacidades del complemento de control de código fuente y se pueden deshabilitar tal y como se detalla aquí.

### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la ADVERTENCIA: "para garantizar la integración óptima del control de código fuente con Visual Studio"

- Establezca la siguiente entrada del registro (agregando el valor si es necesario):

   **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**

   Esta advertencia se muestra para todos los complementos que no son de [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] .

### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la ADVERTENCIA: "el proveedor de control de código fuente instalado no es compatible con todas las funcionalidades"

- Establezca los dos valores del registro siguientes (agregando los valores si es necesario):

     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**

    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**

     Esta advertencia se muestra si el complemento de control de código fuente no admite explícitamente la reentrada para varios proyectos (es decir, si solo puede proteger un archivo y proyecto a la vez).

     Es mejor admitir la reentrada ( `SCC_CAP_REENTRANT` capacidad); si lo hace, se quitará esta advertencia. Sin embargo, si esta compatibilidad no es posible, se pueden establecer estas entradas del registro.

## <a name="see-also"></a>Vea también

- [Marcas de capacidad](../extensibility/capability-flags.md)
