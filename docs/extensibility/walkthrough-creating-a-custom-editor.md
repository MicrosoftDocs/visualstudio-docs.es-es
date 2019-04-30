---
title: 'Tutorial: Crear un Editor personalizado | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f85963712fa1b051ea7256e6f805fe8e7c7e70d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952911"
---
# <a name="walkthrough-create-a-custom-editor"></a>Tutorial: Crear un editor personalizado
La plantilla de proyecto VSPackage puede crear un editor personalizado simple en C++. La plantilla de proyecto VSPackage ya no admite proyectos de C# o Visual Basic. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Requisitos previos
 Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>La plantilla de proyecto de paquete de Visual Studio
 Puede encontrar la plantilla de proyecto de paquete de Visual Studio en el **nuevo proyecto** cuadro de diálogo en el **C++ extensibilidad** carpeta.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para crear un VSPackage mediante la plantilla de paquete de Visual Studio

1. Cree un proyecto con la plantilla de paquete de Visual Studio.

2. Seleccione el **Editor personalizado** opción y haga clic en **siguiente**. El **opciones del Editor** aparece la página.

3. Escriba el nombre del editor en el **nombre de Editor** cuadro. Escriba la extensión de archivo que desea que se asociará con el editor en el **extensión de archivo** cuadro. El editor está disponible para los archivos con esta extensión. La extensión de archivo está registrada para Visual Studio solo, no para Windows. Escriba el nombre de archivo predeterminado para nuevos documentos creados con el editor en el **nombre de archivo predeterminado** cuadro.

4. Haga clic en **Finalizar** para crear el VSPackage en la carpeta que especificó.

### <a name="to-test-your-custom-editor"></a>Para probar el editor personalizado

1. En el **archivo** menú, elija **New** y, a continuación, haga clic en **archivo**.

2. En el **plantillas instaladas** panel de la **nuevo archivo** cuadro de diálogo, seleccione la plantilla de archivo y, a continuación, el archivo de tipo se registrado.

3. Haga clic en **abierto** para ver y editar el documento.

     El editor admite operaciones de cortar y pegar, buscar y reemplazar y abierto y carga.

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)