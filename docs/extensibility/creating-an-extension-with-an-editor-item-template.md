---
title: Creación de una extensión con una plantilla de elemento de editor ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739507"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Crear una extensión con una plantilla de elemento de editor
Puede usar plantillas de elementos que se incluyen en el SDK de Visual Studio para crear extensiones de editor básicas que agreguen clasificadores, adornos y márgenes al editor. Las plantillas de elemento seditor están disponibles para proyectos de Visual C o VSIX de Visual Basic.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-classifier-extension"></a>Crear una extensión clasificadora
 La plantilla de elemento Clasificador de editor crea un clasificador de editor que colorea el texto adecuado (en este caso, todo) en cualquier archivo de texto.

1. En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual C** o Visual **Basic** y, a continuación, haga clic en **Extensibilidad**. En el panel **Plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `TestClassifier`. Haga clic en **OK**.

2. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C- y seleccione **Clasificador**de editor . Deje el nombre de archivo predeterminado (*EditorClassifier1.cs*).

3. Hay cuatro archivos de código, como se indica a continuación:

    - *EditorClassifier1.cs* contiene `EditorClassifier1` la clase.

    - *EditorClassifier1ClassificationDefinition.cs* contiene `EditorClassifier1ClassificationDefinition` la clase.

    - *EditorClassifier1Format.cs* contiene `EditorClassifier1Format` la clase.

    - *EditorClassifier1Provider.cs* contiene `EditorClassifier1Provider` la clase.

4. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

     Si abre un archivo de texto, todo el texto se subraya con un fondo violeta.

## <a name="create-a-text-relative-adornment-extension"></a>Crear una extensión de adorno relativo al texto
 La plantilla Adornación de texto del editor crea un adorno relativo al texto que decora todas las instancias del carácter de texto 'a' mediante un cuadro que tiene un contorno rojo y un fondo azul. Es relativo al texto porque el cuadro siempre se superpone a los caracteres 'a', incluso cuando se mueven o se reformatean.

1. En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual C** o Visual **Basic** y, a continuación, haga clic en **Extensibilidad**. En el panel **Plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `TestAdornment`. Haga clic en **OK**.

2. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C- y seleccione **Editor Text Adornment**. Deje el nombre de archivo predeterminado (*TextAdornment1.cs/vb*).

3. Hay dos archivos de código, como se indica a continuación:

    - *TextAdornment1.cs* contiene `TextAdornment1` la clase.

    - *TextAdornment1TextViewCreationListener.cs* contiene `TextAdornment1TextViewCreationListener` la clase.

4. Compile la solución y comience la depuración. Aparece la instancia experimental. Si abre un archivo de texto, todos los caracteres 'a' del texto se describen en rojo sobre un fondo azul.

## <a name="create-a-viewport-relative-adornment-extension"></a>Crear una extensión de adorno relativo a la ventana gráfica
 La plantilla Adornación de ventana gráfica del editor crea un adorno relativo a la ventana gráfica que agrega un cuadro violeta que tiene un contorno rojo en la esquina superior derecha de la ventana gráfica.

> [!NOTE]
> La **ventana gráfica** es el área de la vista de texto que se muestra actualmente.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para crear una extensión de adorno de ventana gráfica mediante la plantilla Adornar ventana gráfica del Editor

1. En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual C** o Visual **Basic** y, a continuación, haga clic en **Extensibilidad**. En el panel **Plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `ViewportAdornment`. Haga clic en **OK**.

2. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C- y seleccione **Editor Viewport Adornment**. Deje el nombre de archivo predeterminado (*ViewportAdornment1.cs/vb*).

3. Hay dos archivos de código, como se indica a continuación:

    - *ViewportAdornment1.cs* contiene `ViewportAdornment1` la clase.

    - *ViewportAdornment1TextViewCreationListener.cs* contiene `ViewportAdornment1TextViewCreationListener` la clase

4. Compile la solución y comience la depuración. Aparece la instancia experimental. Si crea un nuevo archivo de texto, se muestra un cuadro violeta que tiene un contorno rojo en la esquina superior derecha de la ventana gráfica.

## <a name="create-a-margin-extension"></a>Crear una extensión de margen
 La plantilla Margen del editor crea un margen verde que aparece junto con las palabras **¡Hola mundo!* debajo de la barra de desplazamiento horizontal.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para crear una extensión de margen mediante la plantilla Margen de editor

1. En el cuadro de diálogo **Nuevo proyecto** , expanda **Visual C** o Visual **Basic** y, a continuación, haga clic en **Extensibilidad**. En el panel **Plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `MarginExtension`. Haga clic en **OK**.

2. En el **Explorador**de soluciones , haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar** > **nuevo elemento**. Vaya al nodo **Extensibilidad** de Visual C- y seleccione Margen del **editor**. Deje el nombre de archivo predeterminado (EditorMargin1.cs/vb).

3. Hay dos archivos de código, como se indica a continuación:

    - *EditorMargin1.cs* contiene `EditorMargin1` la clase.

    - *EditorMargin1Factory.cs* contiene `EditorMargin1Factory` la clase.

4. Compile este proyecto e inicie la depuración. Aparece la instancia experimental. Si abre un archivo de texto, se muestra un margen verde que tiene las palabras **Hello EditorMargin1** debajo de la barra de desplazamiento horizontal.

## <a name="see-also"></a>Vea también
- [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)
