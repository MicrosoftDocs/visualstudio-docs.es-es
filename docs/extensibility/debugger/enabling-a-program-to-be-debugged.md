---
title: Habilitar la depuración de un programa | Microsoft Docs
description: Obtenga información sobre cómo iniciar el motor de depuración o adjuntar el motor de depuración a un programa existente para depurar un programa.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ac9a43a0ec539dd978710c23c9b44f27eac81799
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915263"
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
