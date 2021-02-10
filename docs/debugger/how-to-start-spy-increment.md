---
title: Inicio de Spy++ | Microsoft Docs
description: Obtenga información sobre cómo iniciar la herramienta Spy++ en Visual Studio o en un símbolo del sistema cuando quiera depurar una solución.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0e8b1125534e52c810f97c91bd00ea53dfd3d6de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896627"
---
# <a name="how-to-start-spy"></a>Procedimiento Iniciar Spy++

Puede iniciar Spy++ desde Visual Studio o desde un símbolo del sistema.

 Cuando inicie Spy++, si se muestra un mensaje para solicitar permiso para realizar cambios en el equipo, seleccione **Sí**.

> [!NOTE]
> Solo puede ejecutar una instancia de Spy++. Si intenta iniciar una segunda instancia, simplemente hace que la instancia que se está ejecutando actualmente obtenga el foco.

## <a name="prerequisites"></a>Requisitos previos

Spy++ requiere los siguientes componentes. Puede seleccionar estos componentes en el Instalador de Visual Studio si selecciona la pestaña **Componentes individuales** y luego selecciona los componentes siguientes.

* En Depuración y pruebas, seleccione **Herramientas de generación de perfiles de C++** .
* En Actividades de desarrollo, seleccione **Características principales de C++** .

Si realizó algún cambio, siga las indicaciones para instalar estos componentes.

## <a name="start-spy-from-visual-studio"></a>Inicio de Spy++ desde Visual Studio

En el menú **Herramientas**, seleccione **Spy++** .

Como Spy++ se ejecuta de forma independiente, después de iniciarlo puede cerrar Visual Studio.

> [!NOTE]
> Cuando se registran mensajes con Spy++, es posible que el sistema operativo funcione más lentamente.

## <a name="start-spy-at-a-command-prompt"></a>Inicio de Spy++ desde un símbolo del sistema

1. En una ventana Símbolo del sistema, cambie los directorios a la carpeta que contiene spyxx.exe. Normalmente, la ruta de acceso a esta carpeta es ..\\*Carpeta de instalación de Visual Studio*\Common7\Tools\\.

2. Escriba **spyxx.exe**.

## <a name="see-also"></a>Vea también
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)
