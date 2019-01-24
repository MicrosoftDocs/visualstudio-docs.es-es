---
title: IDispError (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345843"
---
# <a name="idisperror-interface"></a>IDispError (Interfaz)
Proporciona información detallada del error contextual.  
  
> [!NOTE]
>  No se implementa esta interfaz.  
  
 Además de los métodos heredados de `IUnknown`, el `IDispError` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Recupera un tipo determinado de información de error.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Recupera el siguiente `IDispError` objeto.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Recupera el código de error desde el `IDispError` objeto.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Devuelve el identificador de programación dependiente del idioma para la clase o aplicación que generó el error.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Devuelve la ruta de acceso del archivo de ayuda y el identificador de contexto del tema que explica el error, si es posible.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Devuelve una descripción textual del error.|