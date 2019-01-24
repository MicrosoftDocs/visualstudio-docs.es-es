---
title: IDebugHelper (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347481"
---
# <a name="idebughelper-interface"></a>IDebugHelper (Interfaz)
Actúa como un generador para los exploradores de objetos y puntos de conexión simple. El Administrador de depuración del proceso (PDM) implementa esta interfaz, que consume los motores de scripts.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugHelper` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Devuelve un explorador de propiedades que encapsula una variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Devuelve un explorador de propiedades que contiene una variante y permite la conversión personalizada de valores VARIANT o tipos VARTYPE en cadenas.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Devuelve una interfaz de evento que encapsula un determinado `IDispatch` objeto.|