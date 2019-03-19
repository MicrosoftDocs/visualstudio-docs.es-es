---
title: IDebugStackFrameSniffer (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e753261098133eb97f5010dcef5f602d283aac4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149489"
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer (Interfaz)
Proporciona una manera de enumerar los marcos de pila lógicos conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada con un subproceso determinado.  
  
> [!NOTE]
>  El depurador llama a esta interfaz desde dentro del subproceso de interés. El motor de scripts debe identificar el subproceso actual y devolver un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugStackFrameSniffer` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Devuelve un enumerador de marcos de pila del subproceso actual.|