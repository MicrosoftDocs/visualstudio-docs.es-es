---
title: Desactivar las advertencias de compatibilidad para complementos de Control de código fuente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e096b52bdf6e3e0065eefbba708d7bda18ab189
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498053"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Cómo: desactivar las advertencias de compatibilidad para complementos de control de código fuente
Un usuario que vea varias advertencias de compatibilidad al emplear el control de código fuente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Las advertencias presentarlos dependen de las capacidades del complemento de control de código fuente y se pueden deshabilitar como detallados aquí.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la advertencia: "para garantizar la integración del control de código fuente óptimo con Visual Studio"  
  
-   Establezca la siguiente entrada del registro (agregando el valor si es necesario):  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001**  
  
     Esta advertencia se muestra para todos los que no sean de[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] los complementos.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la advertencia: "el proveedor de control de código fuente instalado no admite todas las capacidades"  
  
-   Establezca los siguientes dos valores del registro (agregando los valores si es necesario):  
  
     **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000**  
  
    **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001**  
  
     Esta advertencia se muestra si el complemento de control de código fuente no admita explícitamente la reentrada para varios proyectos (es decir, si puede comprobar en un solo archivo y proyecto a la vez).  
  
     Es mejor admitir la reentrada (`SCC_CAP_REENTRANT` capacidad); al hacerlo eliminará esta advertencia. Sin embargo, si esta compatibilidad no es posible, pueden establecer estas entradas del registro.  
  
## <a name="see-also"></a>Vea también  
 [Marcadores de capacidad](../extensibility/capability-flags.md)