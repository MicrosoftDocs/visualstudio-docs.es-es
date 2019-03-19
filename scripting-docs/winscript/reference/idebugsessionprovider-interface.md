---
title: IDebugSessionProvider (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe73901d92cb42675ff9ec981bd9b90dcca5d546
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148992"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider (Interfaz)
La interfaz principal proporcionada por un IDE para habilitar el host y el idioma del depurador inicia la depuración. Establece una sesión de depuración para una aplicación en ejecución. Esta interfaz se implementa mediante el Administrador de depuración de la máquina.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSessionProvider` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicia una sesión de depuración con la aplicación especificada.|