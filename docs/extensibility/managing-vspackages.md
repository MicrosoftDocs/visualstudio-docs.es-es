---
title: Administrar VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 35
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 32e4aa4302f7871e71907d094c12038b00d7e6bb
ms.lasthandoff: 02/22/2017

---
# <a name="managing-vspackages"></a>Administración de VSPackages
En la mayoría de los casos no es necesario preocuparse por administrar VSPackages, ya que las plantillas de proyecto y elemento de registrarán y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias necesitará aprender un poco más para administrar el paquete.  
  
## <a name="using-the-experimental-instance"></a>Uso de la instancia experimental  
 Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registrar y anular el registro VSPackages  
 Para averiguar cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Cargar un paquete VSPackage  
 VSPackages puede establecerse para cargar automáticamente cuando un determinado que CMDUICONTEXT GUID está activado. Para obtener más información, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Utilizar AsyncPackage para cargar VSPackages en segundo plano  
 La clase AsyncPackage permite el paquete de carga en un subproceso en segundo plano para una mejor capacidad de respuesta de interfaz de usuario en Visual Studio. Para obtener más información, consulte [Cómo: usar AsyncPackage a VSPackages carga en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interfaz de usuario basada en reglas para las extensiones  
 Contextos de interfaz de usuario basada en reglas permite a los autores de extensión definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y cargar VSPackages asociado. Para obtener más información, consulte [Cómo: contexto de interfaz de usuario basada en reglas de uso de extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="diagnosing-extension-performance"></a>Diagnóstico de rendimiento de la extensión  
Extensiones pueden afectar al rendimiento de carga de inicio y la solución. Obtenga información acerca de cómo se calcula el impacto de la extensión de Visual Studio y cómo pueden analizarse localmente para probar si una extensión puede mostrarse como un rendimiento que afectan a la extensión. Para obtener más información, consulte [Cómo: diagnosticar el rendimiento de extensión](how-to-diagnose-extension-performance.md). 
  
## <a name="troubleshooting-vspackages"></a>Solucionar problemas de VSPackages  
 Descubra las técnicas para solucionar problemas de VSPackages que no se cargan o está experimentando errores: [VSPackages de solución de problemas](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)
