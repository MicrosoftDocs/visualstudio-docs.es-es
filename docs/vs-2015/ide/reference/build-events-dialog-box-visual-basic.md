---
title: Cuadro de diálogo Eventos de compilación (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- build events, specifying
- pre-build events
- Build Events dialog box
- post-build events
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9fa3b4365f49d172e077ca132b26a49580228c25
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660960"
---
# <a name="build-events-dialog-box-visual-basic"></a>Eventos de compilación (Cuadro de diálogo) (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use el cuadro de diálogo **Eventos de compilación** para especificar las instrucciones de configuración de compilación. También puede especificar las condiciones en las que se ejecutan los eventos anteriores o posteriores a la compilación. Para obtener más información, vea [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

 **Línea de comandos del evento anterior a la compilación** Especifica los comandos que se van a ejecutar antes de que empiece la compilación. Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el cuadro de diálogo [Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.

 **Línea de comandos del evento posterior a la compilación** Especifica los comandos que se van a ejecutar después de que termine la compilación. Para escribir comandos largos, haga clic en **Edición posterior a la compilación** para mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación**.

> [!NOTE]
> Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

 **Ejecutar el evento posterior a la compilación** Especifica las condiciones para que se ejecute el evento posterior a la compilación, como se muestra en la tabla siguiente.

|Opción|Resultado|
|------------|------------|
|**Siempre**|El evento posterior a la compilación se ejecuta independientemente de si la compilación se realiza correctamente.|
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecuta si la compilación se realiza correctamente. El evento se ejecutará incluso para un proyecto actualizado, siempre y cuando la compilación se realice correctamente. Ésta es la configuración predeterminada.|
|**Cuando la compilación actualiza la salida del proyecto**|El evento posterior a la compilación solo se ejecuta si el archivo de salida del compilador (.exe o .dll) es diferente del anterior archivo de salida del compilador. Un evento posterior a la compilación no se ejecuta si un proyecto está actualizado.|

## <a name="see-also"></a>Vea también
 [Página compilar, diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md) [Cómo: especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md) [cuadro de diálogo línea de comandos del evento anterior/posterior a la](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) compilación
