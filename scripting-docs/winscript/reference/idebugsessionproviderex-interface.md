---
title: IDebugSessionProviderEx (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9bf341adeaeb17c8986b1b30b12f58113aef562
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979001"
---
# <a name="idebugsessionproviderex-interface"></a>IDebugSessionProviderEx (Interfaz)
La interfaz principal proporcionada por un IDE para habilitar la depuración iniciado por el lenguaje y el host del depurador. Establece una sesión de depuración para una aplicación en ejecución. Esta interfaz se implementa mediante el Administrador de depuración de la máquina.  
  
 Además de los métodos heredados de `IUnknown`, el `IDebugSessionProviderEx` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Determina si es posible con la aplicación especificada solo en tiempo de depuración.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Inicia una sesión de depuración con la aplicación especificada.|