---
title: AddMessage | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de3460a345dba21e3a8f481adb510b9e3bdd4990
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473353"
---
# <a name="addmessage"></a>AddMessage
Agrega un mensaje personalizado al diagnóstico de gráficos *HUD* (visualización frontal).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szMessage`  
 Mensaje que se va a agregar al HUD.  
  
## <a name="remarks"></a>Comentarios  
 El HUD de diagnóstico de gráficos se muestra en la esquina superior izquierda de la aplicación que se ejecuta bajo diagnóstico de gráficos. Muestra información en tiempo de ejecución sobre la aplicación y sobre la captura de información de gráficos, y los mensajes que se agregan al llamar a esta función.  
  
 Para agregar un mensaje al HUD, no tiene que ser capturaba activamente información de gráficos, es decir, se puede agregar un mensaje a través de una instancia de la `VsgDbg` (clase), pero la [Init](init.md) hace de la función de miembro para que no se llamará en primer lugar. Los mensajes solo se muestran en el HUD, no se registran en el archivo de registro de gráficos.