---
title: VSG_DEFAULT_RUN_FILENAME | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 303bce554ff6345a37719a8d2f529f3c1ffe02e2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472030"
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