---
title: Administración de VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b68ad8fb8ce32c2a4a1210d38fb458518d28435
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296353"
---
# <a name="managing-vspackages"></a>Administración de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la mayoría de los casos no es necesario preocuparse por administrar los paquetes VSPackage, puesto que las plantillas de proyecto y elemento de registrarán y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias necesitará aprender un poco más con el fin de administrar el paquete.  
  
## <a name="using-the-experimental-instance"></a>Uso de la instancia experimental  
 Para obtener más información acerca de la instancia experimental, consulte [la instancia Experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registro y anulación del registro de VSPackages  
 Para averiguar cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Cargar un paquete VSPackage  
 Los VSPackages se puede establecer para cargar automáticamente cuando un determinado que CMDUICONTEXT GUID está activado. Para obtener más información, consulte [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Uso de AsyncPackage para cargar VSPackages en segundo plano  
 La clase AsyncPackage permite paquete carga en un subproceso en segundo plano para una mejor capacidad de respuesta de la interfaz de usuario en Visual Studio. Para obtener más información, consulte [Cómo: uso de AsyncPackage para cargar VSPackages en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interfaz de usuario basada en reglas para extensiones  
 Contextos de interfaz de usuario basada en reglas permite a los autores de extensión definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y cargar VSPackages asociados. Para obtener más información, consulte [Cómo: contexto de interfaz de usuario basada en reglas de uso de extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Solución de problemas de VSPackages  
 Descubra las técnicas para solucionar problemas de VSPackages que no se cargan o está experimentando errores: [solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Vea también  
 [VSPackages](../extensibility/internals/vspackages.md)

