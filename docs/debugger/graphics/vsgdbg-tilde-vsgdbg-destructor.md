---
title: 'VsgDbg:: ~ VsgDbg (Destructor) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8d34fc9ac09f944fea44baff3ceea4a121a8009
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destructor)
Destruye una instancia de la clase `VsgDbg`. Si se está grabando activamente información de gráficos, el archivo de registro de gráficos se finaliza y se cierra, y se liberan los recursos utilizados mientras se capturaba activamente información de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vea también  
 [VsgDbg::VsgDbg (Constructor)](vsgdbg-vsgdbg-constructor.md)