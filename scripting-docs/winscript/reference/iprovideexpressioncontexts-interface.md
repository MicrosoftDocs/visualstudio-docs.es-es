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
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410059"
---
# <a name="iprovideexpressioncontexts-interface"></a>IProvideExpressionContexts (Interfaz)
Proporciona una manera de enumerar los contextos de expresión que un componente determinado conoce. Motores de script normalmente implementan esta interfaz.  
  
 El Administrador de depuración del proceso usa esta interfaz para encontrar todos los contextos de expresión global asociados a un subproceso determinado.  
  
> [!NOTE]
> Esta interfaz se llama desde dentro del subproceso de interés. Es responsabilidad del implementador para identificar el subproceso actual y devuelve un enumerador correspondiente.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `IProvideExpressionContexts` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Devuelve un enumerador de contextos de expresión que se conoce por este componente.|