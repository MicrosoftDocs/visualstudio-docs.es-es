---
title: VsgDbg::~VsgDbg (Destructor) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995379"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destructor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Destruye una instancia de la clase `VsgDbg`. Si se está grabando activamente información de gráficos, el archivo de registro de gráficos se finaliza y se cierra, y se liberan los recursos utilizados mientras se capturaba activamente información de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vea también  
 [VsgDbg::VsgDbg (Constructor)](../debugger/vsgdbg-vsgdbg-constructor.md)
