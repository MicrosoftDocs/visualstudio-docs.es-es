---
title: Crear una extensión con una plantilla de elemento de editor | Microsoft Docs
description: Aprenda a usar plantillas de elementos en el SDK de Visual Studio para crear extensiones de editor básicas que agreguen clasificadores, elementos gráficos y márgenes al editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 06c3fbfabb4eccc08e528aef913e1c1ba502cbf1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089139"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Crear una extensión con una plantilla de elemento de editor
Puede usar plantillas de elementos que se incluyen en el SDK de Visual Studio para crear extensiones de editor básicas que agreguen clasificadores, elementos gráficos y márgenes al editor. Las plantillas de elementos del editor están disponibles para proyectos de Visual C# o Visual Basic VSIX.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Crear una extensión de clasificador
 La plantilla de elemento clasificador de editor crea un clasificador de editor que colorea el texto correspondiente (en este caso, todo) en cualquier archivo de texto.

1. En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el panel **plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `TestClassifier`. Haga clic en **OK**.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. Vaya al nodo **extensibilidad** de Visual C# y seleccione **clasificador de editor**. Deje el nombre de archivo predeterminado (*EditorClassifier1. CS*).

3. Hay cuatro archivos de código, como se indica a continuación:

    - *EditorClassifier1. CS* contiene la `EditorClassifier1` clase.

    - *EditorClassifier1ClassificationDefinition. CS* contiene la `EditorClassifier1ClassificationDefinition` clase.

    - *EditorClassifier1Format. CS* contiene la `EditorClassifier1Format`  clase.

    - *EditorClassifier1Provider. CS* contiene la `EditorClassifier1Provider` clase.

4. Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.

     Si abre un archivo de texto, todo el texto se subraya con respecto a un fondo violeta.

## <a name="create-a-text-relative-adornment-extension"></a>Crear una extensión de adornos relativa a texto
 La plantilla de gráfico de texto del editor crea un elemento gráfico relativo al texto que decora todas las instancias del carácter de texto ' a ' mediante un cuadro que tiene un contorno rojo y un fondo azul. Es relativo al texto porque el cuadro siempre superpone los caracteres "a", incluso cuando se mueven o se cambian de formato.

1. En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el panel **plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `TestAdornment`. Haga clic en **OK**.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. Vaya al nodo **extensibilidad** de Visual C# y seleccione **gráfico de texto del editor**. Deje el nombre de archivo predeterminado (*TextAdornment1. CS/VB*).

3. Hay dos archivos de código, como se indica a continuación:

    - *TextAdornment1. CS* contiene la `TextAdornment1` clase.

    - *TextAdornment1TextViewCreationListener. CS* contiene la `TextAdornment1TextViewCreationListener` clase.

4. Compile la solución y comience la depuración. Aparece la instancia experimental. Si abre un archivo de texto, todos los caracteres "a" del texto se describen en rojo con un fondo azul.

## <a name="create-a-viewport-relative-adornment-extension"></a>Crear una extensión de adornos relativa a viewport
 La plantilla de elemento gráfico de la ventanilla de editor crea un elemento gráfico relativo a la ventanilla que agrega un cuadro violeta que tiene un contorno rojo en la esquina superior derecha de la ventanilla.

> [!NOTE]
> La **ventanilla** es el área de la vista de texto que se muestra actualmente.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para crear una extensión de elemento gráfico de ventanilla mediante la plantilla de elemento gráfico de la ventanilla de editor

1. En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el panel **plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `ViewportAdornment`. Haga clic en **OK**.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. Vaya al nodo **extensibilidad** de Visual C# y seleccione **elemento gráfico** de la ventanilla del editor. Deje el nombre de archivo predeterminado (*ViewportAdornment1. CS/VB*).

3. Hay dos archivos de código, como se indica a continuación:

    - *ViewportAdornment1. CS* contiene la `ViewportAdornment1` clase.

    - *ViewportAdornment1TextViewCreationListener. CS* contiene la `ViewportAdornment1TextViewCreationListener` clase.

4. Compile la solución y comience la depuración. Aparece la instancia experimental. Si crea un nuevo archivo de texto, se muestra un cuadro violeta con un contorno rojo en la esquina superior derecha de la ventanilla.

## <a name="create-a-margin-extension"></a>Crear una extensión de margen
 La plantilla de margen del editor crea un margen verde que aparece junto con las palabras **Hola mundo.* debajo de la barra de desplazamiento horizontal.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para crear una extensión de margen mediante la plantilla de margen del editor

1. En el cuadro de diálogo **nuevo proyecto** , expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el panel **plantillas** , seleccione **Proyecto VSIX**. En el cuadro **Nombre**, escriba `MarginExtension`. Haga clic en **OK**.

2. En el **Explorador de soluciones**, haga clic con el botón secundario en el nodo del proyecto y seleccione **Agregar**  >  **nuevo elemento**. Vaya al nodo **extensibilidad** de Visual C# y seleccione **margen del editor**. Deje el nombre de archivo predeterminado (EditorMargin1. CS/VB).

3. Hay dos archivos de código, como se indica a continuación:

    - *EditorMargin1. CS* contiene la `EditorMargin1` clase.

    - *EditorMargin1Factory. CS* contiene la `EditorMargin1Factory` clase.

4. Compile este proyecto e inicie la depuración. Aparece la instancia experimental. Si abre un archivo de texto, se muestra un margen verde con las palabras **Hello EditorMargin1** debajo de la barra de desplazamiento horizontal.

## <a name="see-also"></a>Consulte también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
