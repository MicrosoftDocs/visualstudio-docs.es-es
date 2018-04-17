---
title: ToggleHUD | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8839e41048a68adf09380e6fa428087299a12801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="togglehud"></a>ToggleHUD
Activa o desactiva el diagnóstico de gráficos *HUD* (visualización frontal) de superposición activado o desactivado.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información de tiempo de ejecución acerca de la aplicación y captura de información de gráficos y los mensajes que se agregan mediante una llamada a la [AddMessage](addmessage.md) función miembro.  
  
 Para alternar el HUD, no tiene que ser capturaba activamente información de gráficos, es decir, se pueden alternar a través de una instancia de la `VsgDbg` (clase), pero la [Init](init.md) función miembro no tiene que llamar primero.