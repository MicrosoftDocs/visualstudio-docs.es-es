---
title: Tareas Editar y Continuar no admitidas para F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851166"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Tareas Editar y Continuar no admitidas para F# #
No se admite Editar y continuar al depurar código de F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Los cambios de código no se aplican durante la sesión de depuración. Por consiguiente, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.
