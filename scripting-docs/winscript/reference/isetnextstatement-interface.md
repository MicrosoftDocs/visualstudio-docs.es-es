---
title: ISetNextStatement (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148430"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement (Interfaz)
Esta interfaz se implementa mediante un intérprete para permitir que el Administrador de procesos de depuración actualizar la instrucción actual. Se implementa desde un objeto de marco de pila y el PDM obtiene esta interfaz a través de QueryInterface.  
  
 interfaz proporciona métodos que son útiles para establecer el punto de ejecución, que determina la siguiente instrucción que se ejecutará.  
  
 Además de los métodos heredados de `IUnknown`, el `ISetNextStatement` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina si se puede establecer el punto de ejecución a la ubicación especificada.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Establece el punto de ejecución en la ubicación especificada.|