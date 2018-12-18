---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43affa6db83d34d18a3f485a88f41ccde5d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804422"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define por su presencia si una instancia predeterminada de la [Case Vsgdbg](../debugger/vsgdbg-class.md) clase, que proporciona la interfaz de captura mediante programación, se proporciona.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si se proporciona una instancia predeterminada de la clase `VsgDbg`. Si se define este símbolo, no se proporciona ninguna instancia predeterminada de la clase `VsgDbg`; de lo contrario, se proporciona e inicializa una instancia predeterminada antes de que se ejecute el programa.  
  
 La interfaz de captura mediante programación se proporciona a través de un puntero que tiene ámbito global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentarios  
 La instancia predeterminada suele ser adecuada, pero para utilizar la interfaz de captura mediante programación dentro de un archivo DLL cuando el dispositivo D3D se ha creado fuera de ese archivo DLL, debe crear y administrar su propia instancia de la clase `VsgDbg`. Si va a administrar su propia interfaz a la API de captura mediante programación de esta manera, deshabilite la instancia predeterminada definiendo `VSG_NODEFAULT_INSTANCE` para evitar la sobrecarga.  
  
 Si la instancia predeterminada no está deshabilitada, se inicializa automáticamente antes de que se ejecute el programa y se destruye automáticamente cuando finaliza el programa. No es necesario inicializar o anular la inicialización de esta instancia explícitamente.  
  
 Para deshabilitar la instancia predeterminada, se debe definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` en el programa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo deshabilitar la instancia predeterminada:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```



