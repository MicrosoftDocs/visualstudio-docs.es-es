---
title: Detención de cambios de código | Microsoft Docs
description: Aprenda a dejar de aplicar cambios de código al usar la característica Editar y continuar durante una sesión de depuración de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stop Applying Code Changes command
- code changes, stopping application of
- Edit and Continue, stopping code changes
ms.assetid: 9e72a50c-bb0a-4eaa-9ac1-d00930b68d38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a63a15340c597a7b62735dfb3f6f14d3707262ac
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150709"
---
# <a name="how-to-stop-code-changes"></a>Procedimiento Detención de los cambios en el código
Mientras Editar y continuar se encuentra en proceso de aplicar los cambios del código, puede detener la operación.

> [!CAUTION]
> Detener los cambios de código en el código administrado puede dar lugar a resultados inesperados. La aplicación de cambios a código administrado suele ser un proceso rápido, por lo que normalmente no es necesario detener los cambios de código en el código administrado.

### <a name="to-stop-applying-code-changes"></a>Para detener la aplicación de los cambios en el código

- Elija **Detener la aplicación de cambios en el código** en el menú **Depurar**.

  Este elemento de menú sólo es visible cuando se están aplicando los cambios del código.

  Si elige esta opción, no se confirmará ninguno de los cambios en el código.

## <a name="see-also"></a>Vea también
- [Editar y continuar](../debugger/edit-and-continue.md)
- [Editar y continuar, Depuración, Opciones (Cuadro de diálogo)](./edit-and-continue.md)