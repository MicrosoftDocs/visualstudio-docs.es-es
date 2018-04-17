---
title: Init | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e81b5ac1b49e9ab021a2436013b0db3dff9a5e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="init"></a>Init
Prepara el componente de aplicación de diagnóstico de gráficos para capturar y grabar activamente información de gráficos en un archivo de registro de gráficos.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
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
 [UnInit](init.md)