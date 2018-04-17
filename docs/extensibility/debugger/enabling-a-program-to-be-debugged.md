---
title: Habilitar un programa que se va a depurar | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f8dc37e5d59738e6ef326be71e773c1e4e57351
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitar un programa que se va a depurar
Antes de que el motor de depuración (Alemania) puede depurar un programa, primero debe iniciar el Alemania o adjuntarlo a un programa existente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)  
 Describe cómo obtener un puerto como el primer paso para habilitar un programa que desea depurar.  
  
 [Registro del programa](../../extensibility/debugger/registering-the-program.md)  
 Explica el paso siguiente para habilitar un programa que se va a depurar: registrarlo con el puerto. Una vez registrado, se puede depurar el programa mediante el proceso de adjuntar o depuración just-in-time (JIT).  
  
 [Asociación al programa](../../extensibility/debugger/attaching-to-the-program.md)  
 El siguiente paso se explica: asociar el depurador al programa.  
  
 [Adjuntar basada en Inicio](../../extensibility/debugger/launch-based-attachment.md)  
 Describe basada en Inicio, datos adjuntos a un programa, que es automático cuando iniciarse por el SDM.  
  
 [Envío de los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)  
 Lo guía a través de los eventos necesarios al crear un motor de depuración (Alemania) y adjuntarlo a un programa.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define un motor de depuración (Alemania) y describe los servicios implementados a través de las interfaces de Alemania y cómo pueden hacer que el depurador para la transición entre distintos modos de funcionamiento.