---
title: Creación de minivolcados con todas las pilas de llamadas
description: Obtenga información sobre cómo crear minivolcados para un proceso de Visual Studio que incluye información para todas las pilas de llamadas.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: d5cf6add1a20a0ee45ec69ade0d5f2839483bb9f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560881"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Creación de minivolcados para un proceso de Visual Studio con todas las pilas de llamadas

En algunos casos, Microsoft podría solicitar un minivolcado de un proceso de Visual Studio en ejecución con la información de todas las pilas de llamadas. Para recopilar esta información, siga estos pasos:

## <a name="create-the-minidump-file"></a>Creación del archivo de minivolcado

1. Inicie una nueva instancia de Visual Studio.
1. En el menú principal, elija **Depurar** > **Asociar al proceso**.
1. Compruebe que están activas las correspondientes casilla **Administrado** y **Nativo** y presione **Asociar**.

   ![Asociar al proceso](../ide/media/attach-to-process.png)

1. Seleccione la otra instancia de Visual Studio a la que asociar de la lista de procesos en ejecución.
1. En el menú principal, seleccione **Depurar** > **Interrumpir todo**.
1. En el menú principal, seleccione **Depurar** > **Guardar volcado como**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obtención de las pilas de llamadas desde el minivolcado

1. Abra el archivo de volcado en Visual Studio.
1. Vaya a **Herramientas** > **Opciones** > **Depuración** > **Símbolos** y asegúrese de que **Servidores de símbolos de Microsoft** tiene activado **Ubicaciones del archivo de símbolos (.pdb)** .
1. Abra la ventana **Comando** (**Ver** > **Otras ventanas** > **Ventana Comandos**).
1. Escriba "~*k". La ventana muestra las pilas de llamadas de todos los subprocesos.
1. Copie todo el texto de la ventana Comandos y guárdelo en un archivo de texto.
1. Asocie el archivo .txt al error.
