---
title: Tareas Editar y Continuar no admitidas para F# | Microsoft Docs
description: Editar y Continuar no se admite para la depuración en F#. Las modificaciones del código durante la depuración no se aplican al código fuente, por lo que el código que se depura no coincidirá con el código fuente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863093"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Tareas Editar y Continuar no admitidas para F# #
No se admite Editar y continuar al depurar código de F#. Es posible editar código de F# durante una sesión de depuración pero se debería evitar. Los cambios de código no se aplican durante la sesión de depuración. Por consiguiente, si se realizan cambios en el código de F# durante la depuración, el código fuente no se corresponderá con el código objeto de la depuración.
