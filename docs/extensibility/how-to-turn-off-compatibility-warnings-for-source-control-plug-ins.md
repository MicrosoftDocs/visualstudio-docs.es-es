---
title: "Desactivar las advertencias de compatibilidad para complementos de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: e1dda3bd8c41efcf74a1b27f764fdfbf817f8d63
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Cómo: desactivar las advertencias de compatibilidad para complementos de Control de código fuente
Un usuario puede ver varias advertencias de compatibilidad al emplear el control de código fuente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Las advertencias presentarlos dependen de las funciones del complemento de control de código fuente y pueden deshabilitarse de forma detallada.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la advertencia: "para garantizar la integración del control de código fuente óptimo con Visual Studio..."  
  
-   Establezca la entrada de registro siguiente (agregando el valor si es necesario):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD:&00000;001  
  
     Esta advertencia se muestra para todas las no -[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] plug-ins.  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la advertencia: "el proveedor de control de código fuente instalado no admite todas las capacidades..."  
  
-   Establecer los dos valores siguientes (agregando los valores si es necesario):  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD:&00000;000  
  
     HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD:&00000;001  
  
     Esta advertencia se muestra si el complemento de control de código fuente no admita explícitamente reentrada para varios proyectos (es decir, si se puede comprobar en un solo archivo y el proyecto a la vez).  
  
     Es mejor admitir la reentrada (`SCC_CAP_REENTRANT` capacidad); al hacerlo quitará esta advertencia. Sin embargo, si esta compatibilidad no es posible, pueden establecer estas entradas del registro.  
  
## <a name="see-also"></a>Vea también  
 [Marcadores de capacidad](../extensibility/capability-flags.md)
