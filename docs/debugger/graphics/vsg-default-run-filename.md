---
title: VSG_DEFAULT_RUN_FILENAME | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7fe31b96911329089174772094784c0d0f3371c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Define el nombre de archivo predeterminado del archivo de registro de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre de archivo que se asigna de forma predeterminada al archivo de registro de gráficos cuando la información de gráficos se captura mediante programación.  
  
## <a name="value"></a>Valor  
 Literal de cadena que representa el nombre del archivo de registro de gráficos. De forma predeterminada,, L"default.vsglog".  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se define el símbolo de preprocesador `DONT_SAVE_VSGLOG_TO_TEMP`, el nombre de archivo es relativo al directorio actual de la aplicación capturada o es una ruta de acceso absoluta; de lo contrario, es relativo al directorio de archivos temporales del usuario y no puede ser una ruta de acceso absoluta.  
  
 Para cambiar el nombre de archivo definido, debe volver a definirlo antes de incluir `vsgcapture.h` en el programa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo cambiar el nombre de archivo predeterminado del archivo de captura:  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Vea también  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)