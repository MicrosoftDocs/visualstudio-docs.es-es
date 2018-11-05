---
title: Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed5ad6259ede32304cfe15ef4e79c6b3e56dbd9d
ms.sourcegitcommit: 1abb9cf4c3ccb90e3481ea8079272c98aad12875
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/26/2018
ms.locfileid: "50143312"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)

Use esta página del cuadro de diálogo **Opciones** para especificar si se realiza una copia de seguridad de los archivos automáticamente o no. Esta página también le permite especificar si desea restaurar los archivos modificados si Visual Studio se cierra inesperadamente.

Para obtener acceso a este cuadro de diálogo seleccione el menú **Herramientas**, después seleccione **Opciones** y luego **Entorno** > **Autorrecuperación**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

**Guardar información de Autorrecuperación cada [n] minutos**

Use esta opción para personalizar la frecuencia con la que un archivo se guarda automáticamente en el editor. Para los archivos que se han guardado anteriormente, una copia del archivo se guarda en *%USERPROFILE%\Documents\Visual Studio \<versión>\Backup Files\\<projectname>*. Si el archivo es nuevo y aún no lo ha guardado, el archivo se guarda automáticamente con un nombre de archivo generado aleatoriamente.

**Guardar información de Autorrecuperación durante [n] días**

Use esta opción para especificar la frecuencia con la que Visual Studio conserva los archivos que se han creado para la autorrecuperación.

## <a name="see-also"></a>Vea también

- [Opciones (cuadro de diálogo)](../../ide/reference/options-dialog-box-visual-studio.md)