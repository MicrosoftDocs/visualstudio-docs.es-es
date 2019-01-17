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
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345154"
---
# <a name="idebugsessionprovider-interface"></a>IDebugSessionProvider (Interfaz)
La interfaz principal proporcionada por un IDE para habilitar el host y el idioma del depurador inicia la depuración. Establece una sesión de depuración para una aplicación en ejecución. Esta interfaz se implementa mediante el Administrador de depuración de la máquina.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSessionProvider` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Inicia una sesión de depuración con la aplicación especificada.|