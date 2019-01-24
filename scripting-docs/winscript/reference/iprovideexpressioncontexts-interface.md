---
title: IProvideExpressionContexts (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 91f4251fec57001ba6c7a4ea1804ec72371418bb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345102"
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