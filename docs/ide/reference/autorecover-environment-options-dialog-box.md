---
title: Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)
description: Aprenda sobre el cuadro de diálogo Autorrecuperación, Entorno, Opciones y cómo se usa para especificar si se realizará una copia de seguridad de los archivos automáticamente.
ms.custom: SEO-VS-2020
ms.date: 08/14/2020
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9a90198ce4cf3dc54eedbf80bbf4ffbad634cbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836493"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)

Use esta página del cuadro de diálogo **Opciones** para especificar si se realiza una copia de seguridad de los archivos automáticamente o no. También puede especificar si quiere restaurar los archivos modificados en caso de que Visual Studio se cierre inesperadamente.

Para acceder a este cuadro de diálogo, vaya a **Herramientas** > **Opciones** > **Entorno** > **Autorrecuperación**.

:::image type="content" source="media/autorecover-options.png" alt-text="Captura de pantalla de la sección Autorrecuperación en el cuadro de diálogo Opciones":::

**Guardar información de Autorrecuperación cada [n] minutos**

::: moniker range="vs-2019"

Use esta opción para personalizar la frecuencia con la que un archivo se guarda automáticamente en el editor. En el caso de los archivos guardados anteriormente, la versión 16.2 y posteriores de Visual Studio 2019 guarda una copia del archivo en ***%LocalAppData%\Microsoft\Visual Studio\BackupFiles\\[nombreDeProyecto]***. Si el archivo es nuevo y aún no lo ha guardado, Visual Studio lo guarda automáticamente con un nombre de archivo generado aleatoriamente.

> [!NOTE]
> Si usa Visual Studio 2019 versión 16.1 o una anterior, la ubicación del archivo es *%USERPROFILE%\Documents\Visual Studio [versión]\Backup Files\\[nombreDeProyecto]* . Para más información, vea la página [Historial de notas de la versión de Visual Studio 2019](/visualstudio/releases/2019/release-notes-history/).

::: moniker-end

::: moniker range="vs-2017"

Use esta opción para personalizar la frecuencia con la que un archivo se guarda automáticamente en el editor. En el caso de los archivos guardados anteriormente, Visual Studio 2017 guarda una copia del archivo en *%USERPROFILE%\Documents\Visual Studio[versión]\Backup Files\\[nombreDeProyecto]* . Si el archivo es nuevo y aún no lo ha guardado, Visual Studio lo guarda automáticamente con un nombre de archivo generado aleatoriamente.

::: moniker-end

**Guardar información de Autorrecuperación durante [n] días**

Use esta opción para especificar la frecuencia con la que Visual Studio conserva los archivos que se han creado para la autorrecuperación.

### <a name="see-also"></a>Consulte también

- [Opciones (cuadro de diálogo)](../../ide/reference/options-dialog-box-visual-studio.md)
