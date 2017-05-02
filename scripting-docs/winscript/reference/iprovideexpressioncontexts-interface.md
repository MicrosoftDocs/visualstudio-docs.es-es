---
title: "IProvideExpressionContexts (Interfaz) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProvideExpressionContexts (interfaz)"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts (Interfaz)
Proporciona una manera de mostrar los contextos de expresión conocidos por un componente.  Los motores de scripts implementan normalmente esta interfaz.  
  
 El administrador de la depuración utiliza esta interfaz para buscar todos los contextos globales de la expresión asociados a un subproceso determinado.  
  
> [!NOTE]
>  Esta interfaz se llama en el subproceso de interés.  Depende del implementador para identificar el subproceso actual y devolver un enumerador adecuado.  
  
## Métodos  
 Además de los métodos heredados de `IUnknown`, la interfaz `IProvideExpressionContexts` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Devuelve un enumerador de los contextos de expresión conocidos por este componente.|