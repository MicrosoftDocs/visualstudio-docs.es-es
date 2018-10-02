---
title: Autorrecuperación, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1fc2eb7cb70fbbafc91880d33b01c87f84073dfa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576104"
---
# <a name="autorecover-environment-options-dialog-box"></a>Autorrecuperación, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Autorrecuperación, entorno, cuadro de diálogo Opciones](https://docs.microsoft.com/visualstudio/ide/reference/autorecover-environment-options-dialog-box).  
  
  
Use esta página del cuadro de diálogo Opciones para especificar si se realiza una copia de seguridad de los archivos automáticamente o no. Esta página también le permite especificar si los archivos modificados se restauran cuando el entorno de desarrollo integrado (IDE) se cierra de manera inesperada o no. Puede tener acceso a este cuadro de diálogo seleccionando **Opciones** desde el menú **Herramientas** y, después, pulsando la carpeta **Entorno** y la página **Autorrecuperación**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Guardar información de Autorrecuperación cada \<n> minutos**  
 Use esta opción para personalizar la frecuencia con la que un archivo se guarda automáticamente en el editor. Para los archivos que se han guardado anteriormente, una copia del archivo se guarda en \\...\My Documents\Visual Studio \<*versión*>\Backup Files\\<*nombreDeProyecto*>. Si el archivo es nuevo y no se ha guardado manualmente, el archivo se guarda automáticamente con un nombre de archivo generado aleatoriamente.  
  
 **Guardar información de Autorrecuperación durante \<n> días**  
 Use esta opción para especificar la frecuencia con la que Visual Studio conserva los archivos que se han creado para la autorrecuperación.  
  
## <a name="see-also"></a>Vea también  
 [Opciones (cuadro de diálogo)](../../ide/reference/options-dialog-box-visual-studio.md)



