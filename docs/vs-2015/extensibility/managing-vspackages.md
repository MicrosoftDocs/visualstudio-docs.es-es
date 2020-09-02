---
title: Administrar VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194379"
---
# <a name="managing-vspackages"></a>Administración de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la mayoría de los casos no es necesario preocuparse por la administración de VSPackages, ya que las plantillas de proyecto y de elemento registran y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias, puede que tenga que aprender un poco más para administrar el paquete.  
  
## <a name="using-the-experimental-instance"></a>Usar la instancia experimental  
 Para obtener más información sobre la instancia experimental, vea [la instancia experimental](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Registro y anulación del registro de VSPackages  
 Para obtener información sobre cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
## <a name="loading-a-vspackage"></a>Carga de un VSPackage  
 Los VSPackages se pueden configurar para que se carguen de forma autocarga cuando se activa un GUID de CMDUICONTEXT determinado. Para obtener más información, vea [cargar VSPackages](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Usar AsyncPackage para cargar VSPackages en segundo plano  
 La clase AsyncPackage habilita la carga de paquetes en un subproceso en segundo plano para mejorar la capacidad de respuesta de la interfaz de usuario en Visual Studio. Para obtener más información, vea [Cómo: usar AsyncPackage para cargar VSPackages en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Contexto de la interfaz de usuario basada en reglas para las extensiones  
 Los contextos de la interfaz de usuario basados en reglas permiten a los autores de extensiones definir las condiciones precisas en las que se activa un contexto de la interfaz de usuario y se cargan los VSPackages asociados. Para obtener más información, consulte [Cómo: usar el contexto de interfaz de usuario basado en reglas para las extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Solución de problemas de VSPackages  
 Descubra las técnicas para solucionar problemas de los VSPackages que no cargan o están experimentando errores: [solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages](../extensibility/internals/vspackages.md)
