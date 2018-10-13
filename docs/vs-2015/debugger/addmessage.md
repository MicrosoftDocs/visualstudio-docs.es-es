---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b60f8bac24b01e39327357b89e9e96c04765077
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249007"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agrega un mensaje personalizado al diagnóstico de gráficos *HUD* (visualización).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szMessage`  
 Mensaje que se va a agregar al HUD.  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a esta función.  
  
 Para agregar un mensaje al HUD, no tiene que estar capturando activamente información de gráficos, es decir, se puede agregar un mensaje a través de una instancia de la `VsgDbg` (clase), pero la [Init](../debugger/init.md) función miembro no tiene que para llamar primero. Los mensajes solo se muestran en el HUD, no se registran en el archivo de registro de gráficos.



