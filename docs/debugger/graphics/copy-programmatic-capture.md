---
title: Copiar (captura mediante programación) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a658f458b6f2dac48ad19f60e2491ad9d6e94406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="copy-programmatic-capture"></a>Copiar (captura mediante programación)
Copia el contenido del archivo de registro de gráficos (.vsglog) activo en un nuevo archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `szNewVSGLog`  
 Nombre del nuevo archivo de registro de gráficos.  
  
## <a name="remarks"></a>Comentarios  
 Para copiar la información de gráficos a un nuevo archivo, debe haber capturado ya cierta información de gráficos; de lo contrario, no ocurre nada.