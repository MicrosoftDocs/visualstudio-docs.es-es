---
title: Elegir una estrategia de implementación del motor de depuración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c3715bac00b25cd2080a1162c8e2ce8cb33e63a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Elegir una estrategia de implementación del motor de depuración
Usar la arquitectura de tiempo de ejecución para determinar la estrategia de implementación (Alemania) del motor de depuración. El motor de depuración puede crearse en proceso para el programa esté depurado, en proceso para el Administrador de depuración de sesión de Visual Studio (SDM), o fuera de proceso a ambos. Las instrucciones siguientes le ayudará a elegir entre estas tres estrategias.  
  
## <a name="guidelines"></a>Instrucciones  
 Aunque es posible que la DE ser fuera de proceso para el SDM tanto el programa va a depurar, no suele haber ninguna razón para hacerlo. Las llamadas entre límites de procesos son relativamente lentas.  
  
 Depurar motores ya se proporcionan para el entorno de tiempo de ejecución nativo de Win32 y para el entorno de common language runtime. Si tiene que reemplazar la DE para cada uno de estos entornos, debe crear el DE proceso con el SDM.  
  
 En caso contrario, puede elegir entre crear el Alemania en proceso para el SDM o en proceso para el programa que desea depurar. Es importante tener en cuenta si el evaluador de expresiones de la DE necesita acceso frecuente al almacén de símbolos de programa y, si se puede cargar el almacén de símbolos en memoria para un acceso rápido. También tenga en cuenta lo siguiente:  
  
-   Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si no se puede leer el almacén de símbolos en el espacio de memoria SDM, creará el Alemania en proceso para el SDM. Debe devolver el CLSID del motor de depuración para el SDM cuando se une al programa. El SDM utiliza este CLSID para crear una instancia en curso de la DE.  
  
-   Si la DE debe llamar al programa para acceder al almacén de símbolos, cree el DE proceso con el programa. En este caso, el programa crea la instancia de la DE.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)