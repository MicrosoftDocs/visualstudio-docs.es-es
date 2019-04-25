---
title: IProvideExpressionContexts (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b40825884b3c63af6be6d8bc852a5da4805f8975
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152056"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts (Interfaz)
Proporciona una manera de enumerar los contextos de expresión que un componente determinado conoce. Motores de script normalmente implementan esta interfaz.  
  
 El Administrador de depuración del proceso usa esta interfaz para encontrar todos los contextos de expresión global asociados a un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama desde dentro del subproceso de interés. Es responsabilidad del implementador para identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IProvideExpressionContexts` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Devuelve un enumerador de contextos de expresión que se conoce por este componente.|