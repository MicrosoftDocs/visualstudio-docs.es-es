---
title: VSG_NODEFAULT_INSTANCE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a460110c56775723a3ab1a2933868e4508c18562
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Define por su presencia si una instancia predeterminada de la [VsgDbg (clase)](vsgdbg-class.md) clase, que proporciona la interfaz de captura mediante programación, se proporciona.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
  
 Para deshabilitar la instancia predeterminada, debe definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` en el programa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo deshabilitar la instancia predeterminada:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```