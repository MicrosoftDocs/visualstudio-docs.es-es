---
title: Copiar (captura mediante programación) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa79ffc2081ba92b905838658fe6aa758a675192
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68161513"
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
