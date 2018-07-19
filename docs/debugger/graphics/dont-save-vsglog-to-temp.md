---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82726226e4ea26db0dd2cb8e37e32f9daa1869b9
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433100"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario. Si se define este símbolo, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio actual de la aplicación capturada o es una ruta de acceso absoluta; de lo contrario, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio de archivos temporales del usuario y no puede ser una ruta de acceso absoluta.  
  
## <a name="remarks"></a>Comentarios  
 Según los privilegios del usuario, el archivo de registro de gráficos quizás no se pueda guardar en una ubicación arbitraria. Se recomienda guardar los registros de gráficos en el directorio de archivos temporales del usuario, o en otra ubicación conocida, si no se sabe con seguridad si el usuario puede escribir en la ubicación que se elegiría.  
  
 Para evitar que el archivo de registro de gráficos que se guardan en el directorio de archivos temporales, debe definir `DONT_SAVE_VSGLOG_TO_TEMP` antes de incluir `vsgcapture.h`.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo guardar el archivo de registro de gráficos en una ruta de acceso absoluta en el equipo host.  
  
```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Vea también  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
