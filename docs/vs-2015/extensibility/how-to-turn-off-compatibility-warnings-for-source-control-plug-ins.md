---
title: 'Cómo: desactivar advertencias de compatibilidad para complementos de control de código fuente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, turning off compatibility warnings
- compatibility warnings, turning off
ms.assetid: ba318e12-921b-4b7a-a8c2-12c712be1dbf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a4397b2710a7de4addd97bfcbdb4f8e80e2b9c70
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204051"
---
# <a name="how-to-turn-off-compatibility-warnings-for-source-control-plug-ins"></a>Desactivación de advertencias de compatibilidad para complementos de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un usuario puede ver varias advertencias de compatibilidad al utilizar el control de código fuente en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Las advertencias presentadas dependen de las capacidades del complemento de control de código fuente y se pueden deshabilitar tal y como se detalla aquí.  
  
### <a name="to-disable-the-warning-to-ensure-optimal-source-control-integration-with-visual-studio"></a>Para deshabilitar la ADVERTENCIA: "para garantizar la integración óptima del control de código fuente con Visual Studio..."  
  
- Establezca la siguiente entrada del registro (agregando el valor si es necesario):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\DontDisplayCheckDotNETCompatible = DWORD: 00000001  
  
     Esta advertencia se muestra para todos los complementos que no son de [!INCLUDE[vsvss](../includes/vsvss-md.md)] .  
  
### <a name="to-disable-the-warning-the-installed-source-control-provider-does-not-support-all-the-capabilities"></a>Para deshabilitar la ADVERTENCIA: "el proveedor de control de código fuente instalado no es compatible con todas las funcionalidades..."  
  
- Establezca los dos valores del registro siguientes (agregando los valores si es necesario):  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\WarnedOldMSSCCIProvider = DWORD: 00000000  
  
     HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl\UseOldSCC = DWORD: 00000001  
  
     Esta advertencia se muestra si el complemento de control de código fuente no admite explícitamente la reentrada para varios proyectos (es decir, si solo puede proteger un archivo y proyecto a la vez).  
  
     Es mejor admitir la reentrada ( `SCC_CAP_REENTRANT` capacidad); si lo hace, se quitará esta advertencia. Sin embargo, si esta compatibilidad no es posible, se pueden establecer estas entradas del registro.  
  
## <a name="see-also"></a>Consulte también  
 [Marcas de capacidad](../extensibility/capability-flags.md)
