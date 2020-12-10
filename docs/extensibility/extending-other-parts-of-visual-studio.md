---
title: Extender otras partes de Visual Studio | Microsoft Docs
description: Obtenga información sobre las partes de la interfaz de usuario de Visual Studio que puede extender. Puede crear un VSPackage, escribir en el registro de actividad y extender el cuadro de herramientas y la barra de estado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cc9a471b141cfd3302814844d63a2ce8d5b74c6
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995842"
---
# <a name="extend-other-parts-of-visual-studio"></a>Extender otras partes de Visual Studio

Hay muchas más partes de la interfaz de usuario de Visual Studio que puede extender. Aquí le mostramos solo algunos.

## <a name="create-a-vspackage"></a>Crear un VSPackage

Los bloques de creación básicos de extensibilidad de Visual Studio son VSPackages.  Más información sobre cómo agregar un VSPackage: [creación de una extensión con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

## <a name="extend-the-toolbox"></a>Extender el cuadro de herramientas

Obtenga información sobre cómo agregar nuevos controles y otros elementos al cuadro de herramientas y cómo usar la funcionalidad del cuadro de herramientas:

- [Crear un control de cuadro de herramientas de WPF](../extensibility/creating-a-wpf-toolbox-control.md)

- [Crear un control de cuadro de herramientas de Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md)

## <a name="extend-the-status-bar"></a>Extender la barra de estado

Obtenga información sobre cómo leer y escribir en la barra de estado y en la barra de progreso, y cómo proporcionar animaciones y otra interfaz de usuario: [extienda la barra de estado](../extensibility/extending-the-status-bar.md).

::: moniker range="vs-2017"

## <a name="create-custom-start-pages"></a>Crear páginas de inicio personalizadas

Obtenga información sobre cómo crear su propia página de inicio, ya sea desde cero o desde un ejemplo de página de inicio descargable: [creación de una página de inicio personalizada](../extensibility/creating-a-custom-start-page.md).

::: moniker-end

## <a name="write-to-the-activity-log"></a>Escribir en el registro de actividad

Obtenga información sobre cómo escribir en el registro de actividad: [Cómo: usar el registro de actividad](../extensibility/how-to-use-the-activity-log.md).
