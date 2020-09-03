---
title: Habilitar la depuración de un programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], enabling for programs
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17c6218cd0b25c0cf0134351fd5efd7490b6a1f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738894"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar la depuración de un programa
Antes de que el motor DE depuración (DE) pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.

## <a name="in-this-section"></a>En esta sección
 [Obtener un puerto](../../extensibility/debugger/getting-a-port.md) Describe cómo obtener un puerto como primer paso para habilitar un programa que se va a depurar.

 [Registrar el programa](../../extensibility/debugger/registering-the-program.md) Explica el siguiente paso para habilitar un programa que se va a depurar: registrarlo con el puerto. Una vez registrado, el programa se puede depurar mediante el proceso de asociar o la depuración Just-in-Time (JIT).

 [Adjuntar al programa](../../extensibility/debugger/attaching-to-the-program.md) Explica el siguiente paso: adjuntar el depurador al programa.

 [Asociación basada en el inicio](../../extensibility/debugger/launch-based-attachment.md) Describe los datos adjuntos basados en el inicio de un programa, que es automático al iniciarlo el SDM.

 [Enviar los eventos necesarios](../../extensibility/debugger/sending-the-required-events.md) Le guía por los eventos necesarios al crear un motor DE depuración (DE) y asociarlo a un programa.

## <a name="related-sections"></a>Secciones relacionadas
 [Crear un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) Define un motor DE depuración (DE) y describe los servicios implementados a través de las interfaces DE y el modo en que el depurador puede pasar de un modo operativo a otro.
