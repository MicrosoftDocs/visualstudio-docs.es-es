---
title: Habilitación de un programa para ser depurado ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738894"
---
# <a name="enable-a-program-to-be-debugged"></a>Habilitar la depuración de un programa
Antes de que el motor de depuración (DE) pueda depurar un programa, primero debe iniciar el DE o adjuntarlo a un programa existente.

## <a name="in-this-section"></a>En esta sección
 [Obtener un puerto](../../extensibility/debugger/getting-a-port.md) Describe cómo obtener un puerto como primer paso para habilitar la depuración de un programa.

 [Registrar el programa](../../extensibility/debugger/registering-the-program.md) Explica el siguiente paso para habilitar la depuración de un programa: registrarlo con el puerto. Una vez registrado, el programa se puede depurar mediante el proceso de asociación o depuración Just-In-Time (JIT).

 [Adjuntar al programa](../../extensibility/debugger/attaching-to-the-program.md) Explica el siguiente paso: adjuntar el depurador al programa.

 [Colocación basada en el lanzamiento](../../extensibility/debugger/launch-based-attachment.md) Describe los datos adjuntos basados en el inicio a un programa, que es automático al iniciarse por el SDM.

 [Enviar los eventos requeridos](../../extensibility/debugger/sending-the-required-events.md) Le guía a través de los eventos necesarios al crear un motor de depuración (DE) y adjuntarlo a un programa.

## <a name="related-sections"></a>Secciones relacionadas
 [Creación de un motor](../../extensibility/debugger/creating-a-custom-debug-engine.md) de depuración personalizado Define un motor de depuración (DE) y describe los servicios implementados a través de las interfaces DE y cómo pueden hacer que el depurador pase entre diferentes modos operativos.
