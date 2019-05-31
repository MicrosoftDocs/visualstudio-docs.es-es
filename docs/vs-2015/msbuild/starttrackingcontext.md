---
title: StartTrackingContext | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContext
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da002fe757d623a665b39c16cc10e77e492e2660
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59657200"
---
# <a name="starttrackingcontext"></a>StartTrackingContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Inicia un contexto de seguimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `intermediateDirectory`  
 El directorio en el que almacenar el registro de seguimiento.  
  
 [in] `taskName`  
 Identifica el contexto de seguimiento. Este nombre se usa para crear el nombre del archivo de registro.  
  
## <a name="return-value"></a>Valor devuelto  
 Una ([HRESULT]<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) con el ([correcto]<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) conjunto de bits si se creó el contexto de seguimiento.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado**: FileTracker.h
