---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteContextTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bba9c5b46aa01cddca4de5c8e1347b540999289
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156449"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Escribe archivos de registro para el contexto actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `intermediateDirectory`  
 El directorio en el que almacenar el registro de seguimiento.  
  
 [in] `tlogRootName`  
 El nombre raíz del nombre del archivo de registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Un [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) con [SUCCEEDED] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) si se ha creado el contexto de seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** FileTracker.h  
  
## <a name="see-also"></a>Consulte también  
 [WriteAllTLogs](../msbuild/writealltlogs.md)
