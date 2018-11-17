---
title: VSG_DEFAULT_RUN_FILENAME | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07407dc0a50da935d8d5a9fa0eed213633adbe4f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801061"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define el nombre de archivo predeterminado del archivo de registro de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Parámetros  
 `filename`  
 Nombre de archivo que se asigna de forma predeterminada al archivo de registro de gráficos cuando la información de gráficos se captura mediante programación.  
  
## <a name="value"></a>Valor  
 Literal de cadena que representa el nombre del archivo de registro de gráficos. De forma predeterminada,, L"default.vsglog".  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Comentarios  
 Si se define el símbolo de preprocesador `DONT_SAVE_VSGLOG_TO_TEMP`, el nombre de archivo es relativo al directorio actual de la aplicación capturada o es una ruta de acceso absoluta; de lo contrario, es relativo al directorio de archivos temporales del usuario y no puede ser una ruta de acceso absoluta.  
  
 Para cambiar el nombre de archivo, debe volver a definirlo antes de incluir `vsgcapture.h` en el programa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo cambiar el nombre de archivo predeterminado del archivo de captura:  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Vea también  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)



