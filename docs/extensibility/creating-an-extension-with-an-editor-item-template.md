---
title: Creación de una extensión con una plantilla de elemento del Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffaadb2ccdf770231abcbbcc5e594644b78ef7e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957870"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Crear una extensión con una plantilla de elementos de editor
Puede usar plantillas de elementos que se incluyen en el SDK de Visual Studio para crear extensiones de editor básico que aumenta el editor de clasificadores, los elementos gráficos y los márgenes. Las plantillas de elementos de editor están disponibles para los proyectos de Visual C# o Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-classifier-extension"></a>Crear una extensión de clasificador  
 La plantilla de elemento de clasificador de Editor crea un clasificador de editor que colorea el texto adecuado (en este caso, todo) en cualquier archivo de texto.  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre** , escriba `TestClassifier`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **clasificador de Editor**. Deje el nombre de archivo predeterminado (*EditorClassifier1.cs*).  
  
3.  Hay cuatro archivos de código, como sigue:  
  
    -   *EditorClassifier1.cs* contiene el `EditorClassifier1` clase.  
  
    -   *EditorClassifier1ClassificationDefinition.cs* contiene el `EditorClassifier1ClassificationDefinition` clase.  
  
    -   *EditorClassifier1Format.cs* contiene el `EditorClassifier1Format` clase.  
  
    -   *EditorClassifier1Provider.cs* contiene el `EditorClassifier1Provider` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
     Si abre un archivo de texto, todo el texto está subrayado con un fondo violeta.  
  
## <a name="create-a-text-relative-adornment-extension"></a>Crear una extensión de elemento gráfico relacionados con texto  
 La plantilla de elemento gráfico de texto del Editor crea un elemento de gráfico relacionados con el texto que está contenido en todas las instancias del carácter 'a' mediante un cuadro que tiene un contorno rojo y un fondo azul. Es relativo a texto porque el cuadro siempre superpuestas "a" caracteres, incluso cuando se mueven o cambian.  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre** , escriba `TestAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **elemento gráfico de Editor de texto**. Deje el nombre de archivo predeterminado (*TextAdornment1.cs/vb*).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   *TextAdornment1.cs* contiene el `TextAdornment1` clase.  
  
    -   *TextAdornment1TextViewCreationListener.cs* contiene el `TextAdornment1TextViewCreationListener` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si abre un archivo de texto, se describen todos los 'a' caracteres en el texto en rojo con un fondo azul.  
  
## <a name="create-a-viewport-relative-adornment-extension"></a>Crear una extensión de elemento de gráfico relativa a la ventanilla  
 La plantilla de elemento de gráfico de área de visualización de Editor crea un elemento de gráfico de ventanilla relativa que agrega un cuadro violeta que tiene un contorno rojo a la esquina superior derecha de la ventanilla.  
  
> [!NOTE]
>  El **ventanilla** es el área de la vista de texto que se muestra actualmente.  
  
### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para crear una extensión de elemento gráfico de área de visualización mediante la plantilla de elemento de gráfico de área de visualización de Editor  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre** , escriba `ViewportAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **elemento gráfico de área de visualización de Editor**. Deje el nombre de archivo predeterminado (*ViewportAdornment1.cs/vb*).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   *ViewportAdornment1.cs* contiene el `ViewportAdornment1` clase.  
  
    -   *ViewportAdornment1TextViewCreationListener.cs* contiene el `ViewportAdornment1TextViewCreationListener` clase  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si crea un nuevo archivo de texto, se muestra un cuadro violeta que tiene un contorno rojo en la esquina superior derecha de la ventanilla.  
  
## <a name="create-a-margin-extension"></a>Crear una extensión de margen  
 La plantilla de margen del Editor crea un margen verde que aparece junto con las palabras **Hola mundo!* debajo de la barra de desplazamiento horizontal.  
  
### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para crear una extensión de margen usando la plantilla del margen del Editor  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre** , escriba `MarginExtension`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **agregar** > **nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **margen del Editor**. Deje el nombre de archivo predeterminado (EditorMargin1.cs/vb).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   *EditorMargin1.cs* contiene el `EditorMargin1` clase.  
  
    -   *EditorMargin1Factory.cs* contiene el `EditorMargin1Factory` clase.  
  
4.  Compilar el proyecto e iniciar la depuración. Aparece la instancia experimental. Si abre un archivo de texto, un margen de color verde que contiene las palabras **Hello EditorMargin1** aparece debajo de la barra de desplazamiento horizontal.  
  
## <a name="see-also"></a>Vea también  
 [Puntos de extensión de editor y el servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
