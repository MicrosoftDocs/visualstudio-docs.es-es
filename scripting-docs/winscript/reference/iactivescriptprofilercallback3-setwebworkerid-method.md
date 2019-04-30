---
title: Método Iactivescriptprofilercallback3 | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 47744746-1276-441e-ab60-2a78f550e8e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0798a23b4c8ad4e5859bec73ebfed47a56b322d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993108"
---
# <a name="iactivescriptprofilercallback3setwebworkerid-method"></a>IActiveScriptProfilerCallback3::SetWebWorkerId (Método)
Notifica al generador de perfiles de Id. de trabajo que se usará para esta sesión de generación de perfiles. Si la función no se está ejecutando en el contexto de la página, no se invoca este método. El valor de `webWorkerId` se incrementa en 1 para cada trabajo, comenzando en 1. Los valores de identificador no pretenden ser estable más allá de una sesión y se corresponden con solo el orden en que se crearon los trabajadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetWebWorkerId([in] DWORD webWorkerId);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `webWorkerId`  
 El identificador del trabajo web.  
  
## <a name="return-value"></a>Valor devuelto  
 Se omite el valor devuelto de este método por el motor de scripting.