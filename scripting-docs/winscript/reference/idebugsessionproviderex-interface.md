---
title: IDebugSessionProviderEx (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 545b60f13e86e59143ce0e57f454b13f61041f11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx (Interfaz)
La interfaz principal proporcionada por un IDE para habilitar la depuración iniciado por el lenguaje y el host del depurador. Establece una sesión de depuración para una aplicación en ejecución. Esta interfaz se implementa mediante el Administrador de depuración de máquina.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSessionProviderEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina si solo en tiempo de depuración es posible con la aplicación especificada.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicia una sesión de depuración con la aplicación especificada.|