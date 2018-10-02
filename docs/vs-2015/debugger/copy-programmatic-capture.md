---
title: Copiar (captura mediante programación) | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 171dd04a4f2c933272a7addc787554f611b1449f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578346"
---
# <a name="copy-programmatic-capture"></a>Copiar (captura mediante programación)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [copiar (captura mediante programación)](https://docs.microsoft.com/visualstudio/debugger/graphics/copy-programmatic-capture).  
  
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



