---
title: Administración de VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c44b31eb8f160695589dda79f19e10389490c38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944025"
---
# <a name="manage-vspackages"></a>Administrar los paquetes VSPackage
En la mayoría de los casos no es necesario preocuparse por administrar los paquetes VSPackage, puesto que las plantillas de proyecto y elemento de registrarán y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias necesitará aprender un poco más con el fin de administrar el paquete.  
  
## <a name="use-the-experimental-instance"></a>Usar la instancia experimental  
 Para obtener más información acerca de la instancia experimental, consulte [la instancia experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="register-and-unregister-vspackages"></a>Registrar y anular el registro de VSPackages  
 Para averiguar cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="load-a-vspackage"></a>Cargar un paquete VSPackage  
 Los VSPackages se puede establecer para cargar automáticamente cuando un determinado que CMDUICONTEXT GUID está activado. Para obtener más información, consulte [carga VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Uso de AsyncPackage para cargar VSPackages en segundo plano  
 La `AsyncPackage` clase habilita la carga del paquete en un subproceso en segundo plano para una mejor capacidad de respuesta de la interfaz de usuario en Visual Studio. Para obtener más información, vea [Cómo: Uso de AsyncPackage para cargar VSPackages en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interfaz de usuario basada en reglas para las extensiones  
 Contextos de interfaz de usuario basada en reglas permite a los autores de extensión definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y cargar VSPackages asociados. Para obtener más información, vea [Cómo: Use el contexto de interfaz de usuario basada en reglas para extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnose-extension-performance"></a>Diagnosticar el rendimiento de la extensión  
Las extensiones pueden afectar el rendimiento de carga de inicio y la solución. Obtenga información sobre cómo se calcula el impacto de la extensión de Visual Studio y cómo se puede analizar localmente para probar si una extensión que se muestren como un rendimiento que afectan a la extensión. Para obtener más información, vea [Cómo: Diagnóstico de rendimiento de la extensión](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshoot-vspackages"></a>Solución de problemas de VSPackages  
 Descubra las técnicas para solucionar problemas de VSPackages que no se cargan o está experimentando errores: [Solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)