---
title: IProvideExpressionContexts (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 402b439da6f1fa369accacb27f987ac77119e343
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts (Interfaz)
Proporciona una manera para enumerar los contextos de expresión que se conoce por un componente determinado. Motores de script normalmente implementan esta interfaz.  
  
 El Administrador de depuración de procesos usa esta interfaz para buscar todos los contextos de expresión global asociados a un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama desde el subproceso de interés. Es responsabilidad del implementador para identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IProvideExpressionContexts` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Devuelve un enumerador de contextos de expresión que se conoce por este componente.|