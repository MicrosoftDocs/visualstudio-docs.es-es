---
title: IDebugSessionProvider (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 4e61b1e5e794c68e34250f958cdda0f50b68334c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727145"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider (Interfaz)
La interfaz principal proporcionada por un depurador IDE para habilitar el host y el idioma inicia la depuración. Establece una sesión de depuración para una aplicación en ejecución. Esta interfaz se implementa mediante el Administrador de depuración de la máquina.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSessionProvider` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicia una sesión de depuración con la aplicación especificada.|