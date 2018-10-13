---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488baf1b2b01fe1491ccd00247e245e1642424d1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200010"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario. Si se define este símbolo, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio actual de la aplicación capturada o es una ruta de acceso absoluta; de lo contrario, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio de archivos temporales del usuario y no puede ser una ruta de acceso absoluta.  
  
## <a name="remarks"></a>Comentarios  
 Según los privilegios del usuario, el archivo de registro de gráficos quizás no se pueda guardar en una ubicación arbitraria. Se recomienda guardar los registros de gráficos en el directorio de archivos temporales del usuario, o en otra ubicación conocida, si no se sabe con seguridad si el usuario puede escribir en la ubicación que se elegiría.  
  
 Para evitar que el archivo de registro de gráficos que se guardan en el directorio de archivos temporales, debe definir `DONT_SAVE_VSGLOG_TO_TEMP` antes de incluir `vsgcapture.h`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo guardar el archivo de registro de gráficos en una ruta de acceso absoluta en el equipo host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



