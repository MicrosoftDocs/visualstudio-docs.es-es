---
title: ISetNextStatement (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement (Interfaz)
Esta interfaz se implementa mediante un intérprete para permitir que el Administrador de procesos de depuración actualizar la instrucción actual. Se implementa en un objeto de marco de pila y la PDM obtiene esta interfaz a través de QueryInterface.  
  
 interfaz proporciona métodos que son útiles para establecer el punto de ejecución, que determina la siguiente instrucción que se va a ejecutar.  
  
 Además de los métodos heredados de `IUnknown`, el `ISetNextStatement` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina si se puede establecer el punto de ejecución a la ubicación especificada.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Establece el punto de ejecución en la ubicación especificada.|