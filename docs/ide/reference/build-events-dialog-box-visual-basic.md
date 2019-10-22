---
title: Eventos de compilación (Cuadro de diálogo) (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4cd0a46e5ab4cc9c3a9e00773818d536b84891
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461447"
---
# <a name="build-events-dialog-box-visual-basic"></a>Eventos de compilación (Cuadro de diálogo) (Visual Basic)

Use el cuadro de diálogo **Eventos de compilación** para especificar las instrucciones de configuración de compilación. También puede especificar las condiciones en las que se ejecutan los eventos anteriores o posteriores a la compilación. Para obtener más información, consulte [Instrucciones: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

**Línea de comandos del evento anterior a la compilación**

Especifica los comandos que se van a ejecutar antes de que empiece la compilación. Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el cuadro de diálogo [Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.

**Línea de comandos del evento posterior a la compilación**

Especifica los comandos que se van a ejecutar después de que finalice la compilación. Para escribir comandos largos, haga clic en **Edición posterior a la compilación** para mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación**.

> [!NOTE]
> Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.

**Ejecutar el evento posterior a la compilación**

Especifica las condiciones para que se ejecute el evento posterior a la compilación, como se muestra en la tabla siguiente.

|Opción|Resultado|
|------------|------------|
|**Siempre**|El evento posterior a la compilación se ejecuta independientemente de si la compilación se realiza correctamente.|
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecuta si la compilación se realiza correctamente. El evento se ejecutará incluso para un proyecto actualizado, siempre y cuando la compilación se realice correctamente. Esta es la configuración predeterminada.|
|**Cuando la compilación actualiza la salida del proyecto**|El evento posterior a la compilación solo se ejecuta si el archivo de salida del compilador (.exe o .dll) es diferente del anterior archivo de salida del compilador. Un evento posterior a la compilación no se ejecuta si un proyecto está actualizado.|

## <a name="see-also"></a>Vea también

- [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
- [Uso de Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Cuadro de diálogo Línea de comandos del evento anterior/posterior a la compilación](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)