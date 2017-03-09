---
title: "VSG_NODEFAULT_INSTANCE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define por su presencia si se proporciona una instancia predeterminada de la clase [VsgDbg \(Clase\)](../debugger/vsgdbg-class.md), que proporciona la interfaz de captura mediante programación.  
  
## Sintaxis  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## Valor  
 Símbolo de preprocesador que por su presencia o ausencia determina si se proporciona una instancia predeterminada de la clase `VsgDbg`.  Si se define este símbolo, no se proporciona ninguna instancia predeterminada de la clase `VsgDbg`; de lo contrario, se proporciona e inicializa una instancia predeterminada antes de que se ejecute el programa.  
  
 La interfaz de captura mediante programación se proporciona a través de un puntero que tiene ámbito global, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## Comentarios  
 La instancia predeterminada suele ser adecuada, pero para utilizar la interfaz de captura mediante programación dentro de un archivo DLL cuando el dispositivo D3D se ha creado fuera de ese archivo DLL, debe crear y administrar su propia instancia de la clase `VsgDbg`.  Si va a administrar su propia interfaz a la API de captura mediante programación de esta manera, deshabilite la instancia predeterminada definiendo `VSG_NODEFAULT_INSTANCE` para evitar la sobrecarga.  
  
 Si la instancia predeterminada no está deshabilitada, se inicializa automáticamente antes de que se ejecute el programa y se destruye automáticamente cuando finaliza el programa.  No es necesario inicializar o anular la inicialización de esta instancia explícitamente.  
  
 Para deshabilitar la instancia predeterminada, debe definir `VSG_NODEFAULT_INSTANCE` antes de incluir `vsgcapture.h` en el programa.  
  
## Ejemplo  
 En este ejemplo se muestra cómo deshabilitar la instancia predeterminada:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```