---
title: Elegir una estrategia de implementación del motor de depuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 97b3c82a59736b72a58237f1e53ff39e9e3b86b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53818357"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Elegir una estrategia de implementación del motor de depuración
Use la arquitectura en tiempo de ejecución para determinar la estrategia de implementación del motor DE depuración. Puede crear el motor en-proceso de depuración para el programa que está depurando. Cree la depuración motor en proceso en el Administrador de depuración de sesión de Visual Studio (SDM). O bien, cree la depuración motor fuera de proceso a ambos. Las instrucciones siguientes le ayudarán a elegir entre estas tres estrategias.  
  
## <a name="guidelines"></a>Instrucciones  
 Aunque es posible que la DE ser fuera de proceso para el SDM y el programa se está depurando, normalmente hay ninguna razón para hacerlo. Las llamadas entre procesos son relativamente lentas.  
  
 Depurar motores ya se proporcionan para el entorno de tiempo de ejecución nativo Win32 y para el entorno de common language Runtime. Si tiene que reemplazar la DE para cualquier entorno, debe crear el DE proceso con el SDM.  
  
 En caso contrario, puede crear el DE en proceso en el SDM o en proceso en el programa que está depurando. Deberá considerar si el evaluador de expresiones de la DE requiere acceso frecuente al almacén de símbolos de programa. O bien, si el almacén de símbolos se puede cargar en memoria para un acceso rápido. Además, tenga en cuenta los siguientes enfoques:  
  
-   Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si se puede leer el almacén de símbolos en el espacio de memoria SDM, cree el DE en proceso en el SDM. Debe devolver el CLSID del motor de depuración para el SDM cuando adjunta a su programa. El SDM utiliza este CLSID para crear una instancia en curso de la DE.  
  
-   Si la DE debe llamar al programa para obtener acceso al almacén de símbolos, cree el DE proceso con el programa. En este caso, el programa crea la instancia de la DE.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)