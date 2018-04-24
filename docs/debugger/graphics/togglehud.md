---
title: ToggleHUD | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
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