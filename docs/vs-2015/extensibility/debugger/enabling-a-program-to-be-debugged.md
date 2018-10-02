---
title: Habilitación de un programa que se desea depurar | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f0dcb98df8562a5f35fc0d56d5a4ef6570021664
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581255"
---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitación de un programa que se va a depurar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [habilitación de un programa que se desea depurar](https://docs.microsoft.com/visualstudio/extensibility/debugger/enabling-a-program-to-be-debugged).  
  
Antes de que el motor de depuración (DE) puede depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)  
 Se explica cómo obtener un puerto como el primer paso para habilitar un programa que se desea depurar.  
  
 [Registro del programa](../../extensibility/debugger/registering-the-program.md)  
 Explica el paso siguiente para habilitar un programa que se desea depurar: registrarlo con el puerto. Una vez registrado, se puede depurar el programa mediante el proceso de adjuntar o depuración just-in-time (JIT).  
  
 [Asociación al programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica el siguiente paso: asociar el depurador al programa.  
  
 [Conexión de inicio](../../extensibility/debugger/launch-based-attachment.md)  
 Describe los datos adjuntos en función de inicio para un programa, que es automático al iniciarse por el SDM.  
  
 [Envío de los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)  
 Le guiará por los eventos necesarios al crear un motor de depuración (DE) y conectarlo a un programa.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define un motor de depuración (DE) y describe los servicios implementados a través de las interfaces DE y cómo pueden provocar al depurador en la transición entre distintos modos de funcionamiento.

