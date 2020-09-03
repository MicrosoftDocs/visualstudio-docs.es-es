---
title: Elegir una estrategia de implementación del motor de depuración | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183471"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Elección de una estrategia de implementación del motor de depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la arquitectura en tiempo de ejecución para determinar la estrategia DE implementación del motor DE depuración (DE). El motor de depuración se puede crear en proceso para el programa que se va a depurar, en proceso para el administrador de depuración de sesión de Visual Studio (SDM) o fuera de proceso para ambos. Las instrucciones siguientes le ayudarán a elegir entre estas tres estrategias.  
  
## <a name="guidelines"></a>Directrices  
 Aunque es posible que el DE sea fuera de proceso para el SDM y el programa que se va a depurar, no suele haber ninguna razón para hacerlo. Las llamadas a través de los límites del proceso son relativamente lentas.  
  
 Los motores de depuración ya se proporcionan para el entorno de tiempo de ejecución nativo de Win32 y para el entorno de Common Language Runtime. Si debe reemplazar el de para cualquiera de estos entornos, debe crear el de en proceso con el SDM.  
  
 De lo contrario, puede elegir entre crear el de en proceso para el SDM o en proceso para el programa que se va a depurar. Es importante tener en cuenta si el evaluador de expresiones de de necesita acceso frecuente al almacén de símbolos del programa y si el almacén de símbolos se puede cargar en memoria para un acceso rápido. Tenga en cuenta lo siguiente:  
  
- Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si el almacén de símbolos se puede leer en el espacio de memoria de SDM, cree la de en proceso para el SDM. Debe devolver el CLSID del motor de depuración al SDM cuando se asocia al programa. El SDM usa este CLSID para crear una instancia en proceso de de.  
  
- Si el método DE debe llamar al programa para tener acceso al almacén de símbolos, cree el DE en proceso con el programa. En este caso, el programa crea la instancia de de.  
  
## <a name="see-also"></a>Consulte también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
