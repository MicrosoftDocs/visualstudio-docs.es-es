---
title: ICanHandleException (interfaz) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICanHandleException interface
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 363a52cfeb409d293ba3589b9d869bbc4fdf5918
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991355"
---
# <a name="icanhandleexception-interface"></a>ICanHandleException (Interfaz)
Permite al llamador de un motor de secuencia de comandos para especificar las excepciones que el llamador identificadores.  
  
## <a name="methods"></a>Métodos  
 Además de los métodos heredados de `IUnknown`, el `ICanHandleException` interfaz expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|Determina si el autor de llamada del motor de secuencia de comandos puede controlar una excepción especificada.|