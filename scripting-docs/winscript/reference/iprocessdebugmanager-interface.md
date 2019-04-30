---
title: IProcessDebugManager (interfaz) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68c044cdc3d523841cc56814b8ca34bcd8aa037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944797"
---
# <a name="iprocessdebugmanager-interface"></a>IProcessDebugManager (Interfaz)
Interfaz principal del administrador de depuración del proceso. Esta interfaz puede crear, agregar o quitar una aplicación virtual de un proceso. Puede enumerar los marcos de pila y subprocesos de la aplicación.  
  
 Además de los métodos heredados de `IUnknown`, el `IProcessDebugManager` interfaz expone los métodos siguientes.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
  
|Método|Descripción|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Crea un nuevo objeto de aplicación de depuración para esta aplicación.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Devuelve un objeto de aplicación predeterminado para el proceso actual.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Agrega una aplicación a la lista del Administrador de máquina depuración de aplicaciones en ejecución.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Quita el que se ejecuta en una aplicación lista de aplicaciones.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Crea una nuevo auxiliar de documento de depuración para esta aplicación.|