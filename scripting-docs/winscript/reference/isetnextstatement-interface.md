---
title: "ISetNextStatement (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement (Interfaz)
Esta interfaz se implementa por un intérprete para permitir que el administrador de la depuración actualice el fragmento actual.  Se implementa de un objeto del marco de pila, y el PDM obtiene esta interfaz con QueryInterface.  
  
 la interfaz proporciona métodos que son útiles para establecer el punto de ejecución, que determina el fragmento siguiente que se va a ejecutar.  
  
 Además de los métodos heredados de `IUnknown`, la interfaz `ISetNextStatement` expone los métodos siguientes.  
  
## métodos en el orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina si el punto de ejecución se puede establecer en la ubicación especificada.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Establece el punto de ejecución en la ubicación especificada.|