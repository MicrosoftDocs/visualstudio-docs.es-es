---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define por su presencia si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.  
  
## Sintaxis  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si el archivo de registro de gráficos se guarda en el directorio de archivos temporales del usuario.  Si se define este símbolo, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio actual de la aplicación capturada o es una ruta de acceso absoluta; de lo contrario, el nombre de archivo especificado por `VSG_DEFAULT_RUN_FILENAME` es relativo al directorio de archivos temporales del usuario y no puede ser una ruta de acceso absoluta.  
  
## Comentarios  
 Según los privilegios del usuario, el archivo de registro de gráficos quizás no se pueda guardar en una ubicación arbitraria.  Se recomienda guardar los registros de gráficos en el directorio de archivos temporales del usuario, o en otra ubicación conocida, si no se sabe con seguridad si el usuario puede escribir en la ubicación que se elegiría.  
  
 Para impedir que el archivo de registro de gráficos se guarde en el directorio de archivos temporales, debe definir `DONT_SAVE_VSGLOG_TO_TEMP` antes de incluir `vsgcapture.h`.  
  
## Ejemplo  
 En este ejemplo se muestra cómo guardar el archivo de registro de gráficos en una ruta de acceso absoluta en el equipo host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## Vea también  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)