---
title: IActiveScriptErrorDebug110 (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72f545f5a48fc7b8aa3f9250b13a62ba659e94bc
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436057"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 (Interfaz)
Agrega funcionalidad a la [IActiveScriptDebug (interfaz)](../../winscript/reference/iactivescriptdebug-interface.md). Esta interfaz se implementa mediante el motor de JavaScript para determinar por qué se ha producido un evento BREAKREASON_ERROR.  
  
> [!IMPORTANT]
> Esta interfaz se implementa mediante PDM v11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="methods"></a>Métodos  
 La interfaz `IActiveScriptErrorDebug110` expone los métodos siguientes.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Devuelve la clase de la excepción producida.|