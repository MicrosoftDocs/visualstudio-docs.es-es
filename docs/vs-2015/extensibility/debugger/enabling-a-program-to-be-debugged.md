---
title: Habilitar la depuración de un programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0f0331430a1cc625dee2a7029742fd62d67fb56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155375"
---
# <a name="enabling-a-program-to-be-debugged"></a>Habilitación de un programa que se va a depurar
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Antes de que el motor DE depuración (DE) pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Obtención de un puerto](../../extensibility/debugger/getting-a-port.md)  
 Describe cómo obtener un puerto como primer paso para habilitar un programa que se va a depurar.  
  
 [Registro del programa](../../extensibility/debugger/registering-the-program.md)  
 Explica el siguiente paso para habilitar un programa que se va a depurar: registrarlo con el puerto. Una vez registrado, el programa se puede depurar mediante el proceso de asociar o la depuración Just-in-Time (JIT).  
  
 [Asociación al programa](../../extensibility/debugger/attaching-to-the-program.md)  
 Explica el siguiente paso: adjuntar el depurador al programa.  
  
 [Asociación basada en el inicio](../../extensibility/debugger/launch-based-attachment.md)  
 Describe los datos adjuntos basados en el inicio de un programa, que es automático al iniciarlo el SDM.  
  
 [Envío de los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md)  
 Le guía por los eventos necesarios al crear un motor DE depuración (DE) y asociarlo a un programa.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Define un motor DE depuración (DE) y describe los servicios implementados a través de las interfaces DE y el modo en que el depurador puede pasar de un modo operativo a otro.
