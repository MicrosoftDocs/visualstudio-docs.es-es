---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4655b6105a940b7f2c742ba8bcd0812d0be5ab95
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433190"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Define por su presencia si una instancia predeterminada de la [Case Vsgdbg](vsgdbg-class.md) clase, que proporciona la interfaz de captura mediante programación, se proporciona.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si se proporciona una instancia predeterminada de la clase `VsgDbg`. Si se define este símbolo, no se proporciona ninguna instancia predeterminada de la clase `VsgDbg`; de lo contrario, se proporciona e inicializa una instancia predeterminada antes de que se ejecute el programa.  
  
 La interfaz de captura mediante programación se proporciona a través de un puntero que tiene ámbito global, `g_pVsgDbg`.  
  
```cpp
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Comentarios  
 La instancia predeterminada suele ser adecuada, pero para utilizar la interfaz de captura mediante programación dentro de un archivo DLL cuando el dispositivo D3D se ha creado fuera de ese archivo DLL, debe crear y administrar su propia instancia de la clase `VsgDbg`. Si va a administrar su propia interfaz a la API de captura mediante programación de esta manera, deshabilite la instancia predeterminada definiendo `VSG_NODEFAULT_INSTANCE` para evitar la sobrecarga.  
  
 Si la instancia predeterminada no está deshabilitada, se inicializa automáticamente antes de que se ejecute el programa y se destruye automáticamente cuando finaliza el programa. No es necesario inicializar o anular la inicialización de esta instancia explícitamente.  
  
 Para deshabilitar la instancia predeterminada, se debe definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` en el programa.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se muestra cómo deshabilitar la instancia predeterminada:  
  
```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
