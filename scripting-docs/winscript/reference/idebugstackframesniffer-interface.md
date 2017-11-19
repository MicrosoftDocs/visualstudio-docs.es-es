---
title: IDebugStackFrameSniffer (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugStackFrameSniffer interface
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c104d24f27900a6ff0eb8e8f72644f820bf5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframesniffer-interface"></a>IDebugStackFrameSniffer (Interfaz)
Proporciona una manera para enumerar los marcos de pila lógica conocidos por un componente. Motores de script normalmente implementan esta interfaz. El Administrador de depuración de proceso utiliza esta interfaz para buscar todos los marcos de pila asociada a un subproceso determinado.  
  
> [!NOTE]
>  El depurador llama a esta interfaz desde dentro del subproceso de interés. El motor de scripts debe identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IDebugStackFrameSniffer` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Devuelve un enumerador de los marcos de pila del subproceso actual.|