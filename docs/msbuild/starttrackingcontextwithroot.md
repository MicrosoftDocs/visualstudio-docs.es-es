---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: StartTrackingContextWithRoot
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0d49543bde0195144fb4918e9a9f173f8f9435ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
Inicia un contexto de seguimiento con un archivo de respuesta que especifica un marcador raíz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp 
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `intermediateDirectory`  
 El directorio en el que almacenar el registro de seguimiento.  
  
 [in] `taskName`  
 Identifica el contexto de seguimiento. Este nombre se usa para crear el nombre del archivo de registro.  
  
 [in] `rootMarkerResponseFile`  
 El nombre de ruta de acceso de un archivo de respuesta que contiene un marcador raíz. El nombre de raíz se usa para agrupar todo el seguimiento de un contexto conjuntamente.  
  
## <a name="return-value"></a>Valor devuelto  
 Un elemento **HRESULT** con el conjunto de bits **SUCCEEDED** si el contexto de seguimiento se ha creado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Vea también  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)