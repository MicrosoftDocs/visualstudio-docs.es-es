---
title: Copiar (captura mediante programación) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2d6afc3a5693896c17e49ccb07b5152d906d43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776153"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura mediante programación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Copia el contenido del archivo de registro de gráficos (.vsglog) activo en un nuevo archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szNewVSGLog`  
 Nombre del nuevo archivo de registro de gráficos.  
  
## <a name="remarks"></a>Comentarios  
 Para copiar la información de gráficos a un nuevo archivo, debe haber capturado ya cierta información de gráficos; de lo contrario, no ocurre nada.



