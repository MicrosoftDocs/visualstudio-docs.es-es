---
title: Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865cf2ec43071a01a333961e118beab14abab82b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651898"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)

Use esta página del cuadro de diálogo **Opciones** para especificar si se realiza una copia de seguridad de los archivos automáticamente o no. También puede especificar si quiere restaurar los archivos modificados en caso de que Visual Studio se cierre inesperadamente.

Para obtener acceso a este cuadro de diálogo seleccione el menú **Herramientas**, después seleccione **Opciones** y luego **Entorno** > **Autorrecuperación**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.

**Guardar información de Autorrecuperación cada [n] minutos**

Use esta opción para personalizar la frecuencia con la que un archivo se guarda automáticamente en el editor. En el caso de los archivos guardados anteriormente, una copia del archivo se guarda en *%USERPROFILE%\Documents\Visual Studio\\[versión]\Backup Files\\[nombreDeProyecto]* . Si el archivo es nuevo y aún no lo ha guardado, el archivo se guarda automáticamente con un nombre de archivo generado aleatoriamente.

**Guardar información de Autorrecuperación durante [n] días**

Use esta opción para especificar la frecuencia con la que Visual Studio conserva los archivos que se han creado para la autorrecuperación.

### <a name="see-also"></a>Vea también

- [Cuadro de diálogo Opciones](../../ide/reference/options-dialog-box-visual-studio.md)