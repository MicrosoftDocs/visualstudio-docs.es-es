---
title: Autorrecuperación, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660973"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta página del cuadro de diálogo Opciones para especificar si se realiza una copia de seguridad de los archivos automáticamente o no. Esta página también le permite especificar si los archivos modificados se restauran cuando el entorno de desarrollo integrado (IDE) se cierra de manera inesperada o no. Puede tener acceso a este cuadro de diálogo seleccionando **Opciones** desde el menú **Herramientas** y, después, pulsando la carpeta **Entorno** y la página **Autorrecuperación**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 **Guardar información de autorrecuperación cada \<n> minutos** use esta opción para personalizar la frecuencia con que se guarda un archivo automáticamente en el editor. En el caso de los archivos guardados anteriormente, se guarda una copia del archivo en \\ . ..\Mis documentos\Visual Studio \<*version*> \copia files \\ < *projectname*>. Si el archivo es nuevo y no se ha guardado manualmente, el archivo se guarda automáticamente con un nombre de archivo generado aleatoriamente.

 **Mantener la información de Autorrecuperación durante \<n> días** use esta opción para especificar el tiempo que Visual Studio conserva los archivos creados para la Autorrecuperación.

## <a name="see-also"></a>Consulte también
 [Cuadro de diálogo Opciones](../../ide/reference/options-dialog-box-visual-studio.md)
