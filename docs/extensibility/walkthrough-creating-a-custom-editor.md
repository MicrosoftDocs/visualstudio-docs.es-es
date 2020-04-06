---
title: 'Tutorial: Creación de un editor personalizado ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697687"
---
# <a name="walkthrough-create-a-custom-editor"></a>Tutorial: Crear un editor personalizado
La plantilla de proyecto de VSPackage puede crear un editor personalizado simple en C++. La plantilla de proyecto de VSPackage ya no admite proyectos de Visual Basic o de C. Para obtener más información, vea SDK de [Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Prerrequisitos
 Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="the-visual-studio-package-project-template"></a>La plantilla de proyecto Paquete de Visual Studio
 Puede encontrar la plantilla de proyecto Paquete de Visual Studio en el **cuadro de** diálogo Nuevo proyecto en la carpeta **Desmiensibilidad** de C++.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para crear un VSPackage mediante la plantilla de paquete de Visual Studio

1. Cree un proyecto con la plantilla Paquete de Visual Studio.

2. Seleccione la opción **Editor personalizado** y haga clic en **Siguiente**. Aparece la página Opciones del **editor.**

3. Escriba el nombre del editor en el cuadro Nombre del **editor.** Escriba la extensión de archivo que desea asociar con el editor en el cuadro **Extensión de** archivo. El editor está disponible para archivos con esta extensión. La extensión de archivo solo está registrada para Visual Studio, no para Windows. Escriba el nombre de archivo predeterminado para los nuevos documentos creados con el editor en el cuadro Nombre de archivo **predeterminado.**

4. Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.

### <a name="to-test-your-custom-editor"></a>Para probar el editor personalizado

1. En el menú **Archivo,** seleccione **Nuevo** y, a continuación, haga clic en **Archivo**.

2. En el panel **Plantillas instaladas** del cuadro de diálogo **Nuevo archivo,** seleccione la plantilla de archivo y, a continuación, el tipo de archivo que registró.

3. Haga clic en **Abrir** para ver y editar el documento.

     El editor admite operaciones de cortar y pegar, buscar y reemplazar y abrir y cargar.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
