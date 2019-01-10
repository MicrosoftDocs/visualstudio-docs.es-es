---
title: Editar y continuar no admitidas para F# | Microsoft Docs
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 856940231e65932b208c83bf4ff1231395b04382
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838078"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Tareas Editar y Continuar no admitidas para F# #
No se admite Editar y continuar al depurar código de F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Los cambios de código no se aplican durante la sesión de depuración. Por consiguiente, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.
