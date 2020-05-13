---
title: Elección de una estrategia de implementación del motor de depuración ( Debug Engine Implementation Strategy ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739126"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Elija una estrategia de implementación del motor de depuración
Utilice la arquitectura en tiempo de ejecución para determinar la estrategia de implementación del motor de depuración (DE). Puede crear el motor de depuración en proceso en el programa que está depurando. Cree el motor de depuración en proceso en el Administrador de depuración de sesión (SDM) de Visual Studio. O bien, cree el motor de depuración fuera de proceso para ambos. Las siguientes pautas deben ayudarle a elegir entre estas tres estrategias.

## <a name="guidelines"></a>Directrices
 Si bien es posible que el DE esté fuera de proceso tanto para el SDM como para el programa que está depurando, normalmente no hay razón para hacerlo. Las llamadas a través de los límites del proceso son relativamente lentas.

 Los motores de depuración ya se proporcionan para el entorno de tiempo de ejecución nativo de Win32 y para el entorno de tiempo de ejecución de lenguaje común. Si usted tiene que substituir el DE para cualquier entorno, usted debe crear el DE en proceso con el SDM.

 De lo contrario, puede crear el DE en proceso en el SDM o en proceso en el programa que está depurando. Deberá tener en cuenta si el evaluador de expresiones de la DE requiere acceso frecuente al almacén de símbolos del programa. O bien, si el almacén de símbolos se puede cargar en la memoria para un acceso rápido. Además, considere los siguientes enfoques:

- Si no hay muchas llamadas entre el evaluador de expresiones y el almacén de símbolos, o si el almacén de símbolos se puede leer en el espacio de memoria SDM, cree el DE en proceso en el SDM. Debe devolver el CLSID del motor de depuración al SDM cuando se asocia al programa. El SDM utiliza este CLSID para crear una instancia en proceso del DE.

- Si el DE debe llamar al programa para acceder al almacén de símbolos, cree el DE en proceso con el programa. En este caso, el programa crea la instancia de LA.

## <a name="see-also"></a>Vea también
- [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
