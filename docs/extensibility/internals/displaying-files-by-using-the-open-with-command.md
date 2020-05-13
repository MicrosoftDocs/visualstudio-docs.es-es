---
title: Visualización de archivos mediante el uso de la apertura con el comando de comandos de la página de comandos de la página de comandos de Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708576"
---
# <a name="display-files-by-using-the-open-with-command"></a>Mostrar archivos mediante el comando Abrir con
Un proyecto puede pedir al IDE que muestre el cuadro de diálogo **Abrir con.** Esta solicitud solicita al usuario que abra un archivo que tiene una selección de editores estándar. Los pasos siguientes describen este proceso:

1. El proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>llama , especificando un valor de `OSE_UseOpenWithDialog` para el `OSEOpenDocEditor` parámetro.

2. En función de la extensión de nombre de archivo del documento, el IDE determina qué editores enumerados en el registro pueden abrir el documento especificado y muestra esta información en el cuadro de diálogo **Abrir con.**

    > [!NOTE]
    > Los proyectos que tienen un editor intrínseco que se debe incluir en el cuadro de diálogo **Abrir** con deben registrar un generador de editores para cada uno de estos editores. Los editores intrínsecos solo funcionan junto con un tipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> determinado de proyecto, que se aplica en la implementación del método. El IDE tiene un generador de editores integrado para el editor de texto principal y el editor binario. El IDE también crea una instancia de un generador de editores en nombre de cada asociación de archivos de Windows registrada. Un ejemplo de este tipo de archivo es Microsoft Word.

3. Tan pronto como el usuario selecciona un elemento desde el **abrir con** cuadro <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> de diálogo, el IDE, a continuación, abre el documento mediante una llamada a método. Para obtener más información, consulte [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vea también
- [Abrir y guardar elementos del proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Cómo: Abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)
