---
title: IDebugHelper (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f0f70ecb8ead264d0d4b074f8fc1d9e3a6091eb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelper-interface"></a>IDebugHelper (Interfaz)
Actúa como un generador para los exploradores de objetos y puntos de conexión simple. El Administrador de depuración de procesos (PDM) implementa esta interfaz, que es utilizada por los motores de scripts.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugHelper` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Devuelve un explorador de propiedades que contiene una variante.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Devuelve un explorador de propiedades que contiene una variante y permite la conversión personalizada de valores de tipo VARIANT o tipos VARTYPE a cadenas.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Devuelve una interfaz de evento que contenga un determinado `IDispatch` objeto.|