---
title: Administración de VSPackages | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9e3241bae84b89b53e30c3d0949e4f8551110e7d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140139"
---
# <a name="managing-vspackages"></a>Administrar paquetes VSPackage
En la mayoría de los casos no tiene que preocuparse sobre cómo administrar paquetes VSPackage, ya que las plantillas de proyecto y elemento de registrarán y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias necesite obtener una explicación más detallada para administrar el paquete.  
  
## <a name="using-the-experimental-instance"></a>Uso de la instancia experimental  
 Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrar y anular el registro de VSPackages  
 Para obtener más información sobre cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Cargar un paquete VSPackage  
 VSPackages puede establecerse para cargar automáticamente cuando un determinado que CMDUICONTEXT GUID está activado. Para obtener más información, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Utilizar AsyncPackage para cargar VSPackages en segundo plano  
 La clase AsyncPackage permite cargar en un subproceso en segundo plano para una mejor capacidad de respuesta de interfaz de usuario en Visual Studio de paquete. Para obtener más información, consulte [Cómo: usar AsyncPackage a VSPackages de carga en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interfaz de usuario basada en reglas para las extensiones  
 Contextos de interfaz de usuario basada en reglas y permite a los autores de extensión definir las condiciones exactas en las que se activa un contexto de la interfaz de usuario y cargar VSPackages asociados. Para obtener más información, consulte [Cómo: contexto de interfaz de usuario basada en reglas de uso de extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnóstico de rendimiento de extensión  
Las extensiones pueden afectar el rendimiento de carga de inicio y la solución. Obtenga información acerca de cómo se calcula el impacto de la extensión de Visual Studio y cómo puede analizarse localmente para probar si una extensión puede mostrarse como un rendimiento que afectan a la extensión. Para obtener más información, consulte [Cómo: diagnosticar el rendimiento de extensión](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Solucionar problemas de VSPackages  
 Descubra las técnicas para solucionar problemas de VSPackages que no se cargan o se experimentan errores: [solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)