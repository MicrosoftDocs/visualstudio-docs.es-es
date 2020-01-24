---
title: 'Cómo: iniciar Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542625"
---
# <a name="how-to-start-spy"></a>Cómo: Iniciar Spy++

Puede iniciar Spy + + desde Visual Studio o en un símbolo del sistema.

 Cuando inicie Spy + +, si se muestra un mensaje para solicitar permiso para realizar cambios en el equipo, seleccione **sí**.

> [!NOTE]
> Solo puede ejecutar una instancia de Spy + +. Si intenta iniciar una segunda instancia, simplemente hace que la instancia que se está ejecutando actualmente obtenga el foco.

## <a name="prerequisites"></a>Requisitos previos

Spy + + requiere los siguientes componentes. Puede seleccionar estos componentes en la Instalador de Visual Studio si selecciona la pestaña **componentes individuales** y, a continuación, selecciona los componentes siguientes.

* En depuración y pruebas, seleccione  **C++ herramientas de generación de perfiles**
* En actividades de desarrollo, seleccione  **C++ características principales.**

Si realizó algún cambio, siga las indicaciones para instalar estos componentes.

## <a name="start-spy-from-visual-studio"></a>Iniciar Spy + + desde Visual Studio

En el menú **herramientas** , seleccione **Spy + +** .

Como Spy + + se ejecuta de forma independiente, después de iniciarlo puede cerrar Visual Studio.

> [!NOTE]
> Cuando se registran mensajes con Spy + +, es posible que el sistema operativo funcione más lentamente.

## <a name="start-spy-at-a-command-prompt"></a>Iniciar Spy + + en un símbolo del sistema

1. En una ventana del símbolo del sistema, cambie los directorios a la carpeta que contiene SPYXX. exe. Normalmente, la ruta de acceso a esta carpeta es..\\la *carpeta de instalación de Visual Studio*\Common7\Tools\\.

2. Escriba **SPYXX. exe**.

## <a name="see-also"></a>Vea también
- [Usar Spy++](../debugger/using-spy-increment.md)
- [Vistas de Spy++](../debugger/spy-increment-views.md)
- [Referencia de Spy++](../debugger/spy-increment-reference.md)
