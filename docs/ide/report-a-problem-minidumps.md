---
title: Creación de minivolcados con todas las pilas de llamadas
ms.date: 06/27/2019
ms.topic: conceptual
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
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271188"
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
