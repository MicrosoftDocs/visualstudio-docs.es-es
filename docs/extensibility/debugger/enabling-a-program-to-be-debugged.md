---
title: Habilitación de un programa que se desea depurar | Microsoft Docs
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
ms.openlocfilehash: ad6e8e9cb8dd34e3cd084bde1eb94ff5774dd4ba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204393"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar un programa que se desea depurar
Antes de que el motor de depuración (DE) puede depurar un programa, primero debe iniciar la DE o adjuntarlo a un programa existente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Obtener un puerto](../../extensibility/debugger/getting-a-port.md)  
 Se explica cómo obtener un puerto como el primer paso para habilitar un programa que se desea depurar.  
  
 [Registrar el programa](../../extensibility/debugger/registering-the-program.md)  
 Explica el paso siguiente para habilitar un programa que se desea depurar: registrarlo con el puerto. Una vez registrado, se puede depurar el programa mediante el proceso de adjuntar o depuración just-in-time (JIT).  
  
 [Adjunte al programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica el siguiente paso: asociar el depurador al programa.  
  
 [Conexión de inicio](../../extensibility/debugger/launch-based-attachment.md)  
 Describe los datos adjuntos en función de inicio para un programa, que es automático al iniciarse por el SDM.  
  
 [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)  
 Le guiará por los eventos necesarios al crear un motor de depuración (DE) y conectarlo a un programa.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define un motor de depuración (DE) y describe los servicios implementados a través de las interfaces DE y cómo pueden provocar al depurador en la transición entre distintos modos de funcionamiento.