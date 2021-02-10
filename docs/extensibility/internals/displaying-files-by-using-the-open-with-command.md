---
title: Mostrar archivos mediante el comando abrir con | Microsoft Docs
description: Obtenga información sobre cómo un proyecto puede llamar al comando abrir con del entorno de desarrollo integrado (IDE) de Visual Studio para mostrar archivos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9426b60013ae17eec872a665666a60d1fdfc1bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946727"
---
# <a name="display-files-by-using-the-open-with-command"></a>Mostrar archivos mediante el comando abrir con
Un proyecto puede pedir al IDE que muestre el cuadro de diálogo **abrir con** . Esta solicitud solicita al usuario que abra un archivo que tenga una selección de editores estándar. En los pasos siguientes se describe este proceso:

1. El proyecto llama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , especificando un valor de `OSE_UseOpenWithDialog` para el `OSEOpenDocEditor` parámetro.

2. En función de la extensión de nombre de archivo del documento, el IDE determina los editores que se enumeran en el registro pueden abrir el documento especificado y muestra esta información en el cuadro de diálogo **abrir con** .

    > [!NOTE]
    > Los proyectos que tienen un editor intrínseco que deben incluirse en el cuadro de diálogo **abrir con** deben registrar un generador de editores para cada editor de ese tipo. Los editores intrínsecos solo funcionan juntos con un tipo determinado de proyecto, que se aplica en la implementación del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método. El IDE tiene un generador de editores integrado para el editor de texto básico y el Editor binario. El IDE también crea una instancia de un generador de editores en nombre de cada Asociación de archivos de Windows registrada. Un ejemplo de este tipo de archivo es Microsoft Word.

3. En cuanto el usuario selecciona un elemento en el cuadro de diálogo **abrir con** , el IDE abre el documento mediante una llamada al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método. Para obtener más información, consulte [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vea también
- [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Mostrar archivos mediante el comando Abrir archivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Cómo: abrir editores estándar](../../extensibility/how-to-open-standard-editors.md)
