---
title: Init | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58996614"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prepara el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos en un archivo de registro de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `vsgLogGetter`  
 Entidad a la que se puede llamar (como una función, un puntero a función, lambda o un objeto de función) que toma como parámetros la longitud de un búfer compuesto por `wchar_t` y un puntero a ese búfer, y devuelve `void`. Cuando se invoca, la entidad a la que se puede llamar determina el nombre de archivo que se utilizará para registrar información de gráficos y lo escribe en el búfer especificado antes de volver.  
  
## <a name="remarks"></a>Comentarios  
 Se llama automáticamente a la función `Init` cuando una instancia de la clase `VsgDbg` se construye especificando el parámetro `bDefaultInit` de su constructor como `true`; de lo contrario, se debe llamar explícitamente a `Init` antes de poder capturar y registrar activamente información de gráficos.  
  
 Para finalizar y cerrar el archivo de registro de gráficos activo, llame a `UnInit` y, a continuación, para capturar y registrar más información de gráficos en un nuevo archivo de registro de gráficos, vuelva a llamar a `Init`. Se puede repetir tantas veces como se desee crear varios archivos de registro de gráficos independientes utilizando la misma instancia de `VsgDbg`.  
  
## <a name="see-also"></a>Vea también  
 [UnInit](../debugger/init.md)
