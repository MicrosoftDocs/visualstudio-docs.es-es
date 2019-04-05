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
ms.openlocfilehash: 80e9e34547580560e79d408935fd10f17b577037
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995103"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Elección de una estrategia de implementación del motor de depuración
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use la arquitectura en tiempo de ejecución para determinar la estrategia de implementación del motor DE depuración. El motor de depuración se puede crear en proceso en el programa que debe depurado, en proceso en el Administrador de depuración de sesión de Visual Studio (SDM) o fuera de proceso a ambos. Las instrucciones siguientes le ayudarán a elegir entre estas tres estrategias.  
  
## <a name="guidelines"></a>Instrucciones  
 Aunque es posible que la DE ser fuera de proceso para el SDM tanto el programa que se desea depurar, no suele haber ninguna razón para hacerlo. Las llamadas entre procesos son relativamente lentas.  
  
 Depurar motores ya se proporcionan para el entorno de tiempo de ejecución nativo Win32 y para el entorno de common language runtime. Si tiene que reemplazar la DE cualquiera de estos entornos, debe crear el DE proceso con el SDM.  
  
 En caso contrario, puede elegir entre la creación de la DE en proceso en el SDM o en proceso en el programa que se desea depurar. Es importante tener en cuenta si debe el evaluador de expresiones de la DE acceso frecuente al almacén de símbolos de programa y, si se puede cargar el almacén de símbolos en memoria para un acceso rápido. También tenga en cuenta lo siguiente:  
  
-   Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si se puede leer el almacén de símbolos en el espacio de memoria SDM, cree el DE en proceso en el SDM. Debe devolver el CLSID del motor de depuración para el SDM cuando adjunta a su programa. El SDM utiliza este CLSID para crear una instancia en curso de la DE.  
  
-   Si la DE debe llamar al programa para obtener acceso al almacén de símbolos, cree el DE proceso con el programa. En este caso, el programa crea la instancia de la DE.  
  
## <a name="see-also"></a>Vea también  
 [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
