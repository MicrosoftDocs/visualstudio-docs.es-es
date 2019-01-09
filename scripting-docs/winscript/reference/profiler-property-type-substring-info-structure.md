---
title: PROFILER_PROPERTY_TYPE_SUBSTRING_INFO (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 5f873cdf2ebd394e48c1513135f1acdcd700c283
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089978"
---
# <a name="profilerpropertytypesubstringinfo-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO (estructura)
Representa información sobre el tipo de subcadena utilizado en la relación. Utilizado en [PROFILER_HEAP_OBJECT_RELATIONSHIP (estructura)](../../winscript/reference/profiler-heap-object-relationship-structure.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Tipo|Descripción|  
|------------|----------|-----------------|  
|longitud|UINT|El objeto es un tipo UINT.|  
|value|LPCWSTR|El objeto es un LPCWSTR.|