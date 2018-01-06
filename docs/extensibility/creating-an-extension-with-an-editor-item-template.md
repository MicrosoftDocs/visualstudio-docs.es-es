---
title: "Crear una extensión con una plantilla de elemento de Editor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fb66dfffaf8fa8339ce9060c912dc358fb454a7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-extension-with-an-editor-item-template"></a>Crear una extensión con una plantilla de elemento de Editor
Puede usar plantillas de elementos que se incluyen en el SDK de Visual Studio para crear extensiones de editor básico que aumenta el editor de clasificadores, opciones gráficas y los márgenes. Las plantillas de elementos de editor están disponibles para los proyectos de Visual C# o Visual Basic VSIX.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-classifier-extension"></a>Crear una extensión de clasificador  
 La plantilla de elemento de clasificador de Editor crea un clasificador de editor que colorea el texto adecuado (en este caso, todo el contenido) en cualquier archivo de texto.  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre**, escriba `TestClassifier`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **clasificador de Editor**. Deje el nombre de archivo predeterminado (EditorClassifier1.cs).  
  
3.  Hay tres archivos de código, como se indica a continuación:  
  
    -   EditorClassifier1.cs contiene el `EditorClassifier1` clase.  
  
    -   EditorClassifier1ClassificationDefinition.cs contiene el `OEditorClassifier1ClassificationDefinition` clase.  
  
    -   EditorClassifier1Format.cs contiene el `EditorClassifier1Format` clase.  
  
    -   EditorClassifier1Provider.cs contiene el `EditorClassifier1Provider` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
     Si abre un archivo de texto, todo el texto está subrayado con un fondo violeta.  
  
## <a name="creating-a-text-relative-adornment-extension"></a>Crear una extensión de elementos gráficos relacionados con texto  
 La plantilla de elementos gráficos de texto del Editor crea un elemento de gráfico de texto relativo que decora todas las instancias de los caracteres de texto 'a' mediante el uso de un cuadro con un contorno de color rojo y un fondo azul. Es texto relativo porque el cuadro siempre se superpone 'a' caracteres, incluso cuando se mueven o se vuelve a dar formato.  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre**, escriba `TestAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **elementos de gráficos de Editor de texto**. Deje el nombre de archivo predeterminado (TextAdornment1.cs/vb).  
  
3.  Hay dos archivos de código, como se indica a continuación:  
  
    -   TextAdornment1.cs contiene el `TextAdornment1` clase.  
  
    -   extAdornment1TextViewCreationListener.cs contiene el `TextAdornment1TextViewCreationListener` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si abre un archivo de texto, la 'a' de los caracteres en el texto aparecen destacados en rojo con un fondo azul.  
  
## <a name="creating-a-viewport-relative-adornment-extension"></a>Crear una extensión de elemento gráfico relativa de la ventanilla  
 La plantilla de elementos gráficos de área de visualización de Editor crea un elemento de gráfico relativa de la ventanilla que agrega un cuadro violeta con un contorno de color rojo a la esquina superior derecha de la ventanilla.  
  
> [!NOTE]
>  El *ventanilla* es el área de la vista de texto que se muestra actualmente.  
  
#### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Para crear una extensión de elementos gráficos de área de visualización mediante la plantilla de elemento de gráfico de área de visualización de Editor  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre**, escriba `ViewportAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **elementos gráficos de área de visualización de Editor**. Deje el nombre de archivo predeterminado (ViewportAdornment1.cs/vb).  
  
3.  Hay dos archivos de código, como se indica a continuación:  
  
    -   ViewportAdornment1.cs contiene el `ViewportAdornment1` clase.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contiene el `ViewportAdornment1TextViewCreationListener` (clase)  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si crea un nuevo archivo de texto, se muestra un cuadro violeta con un contorno de color rojo en la esquina superior derecha de la ventanilla.  
  
## <a name="creating-a-margin-extension"></a>Crear una extensión de margen  
 La plantilla de margen de Editor crea un margen verde que aparece junto con las palabras "¡Hello world!" por debajo de la barra de desplazamiento horizontal.  
  
#### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Para crear una extensión de margen usando la plantilla de margen de Editor  
  
1.  En el **nuevo proyecto** cuadro de diálogo, expanda **Visual C#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el cuadro **Nombre**, escriba `MarginExtension`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar / nuevo elemento**. Vaya a Visual C# **extensibilidad** nodo y seleccione **elementos gráficos de área de visualización de Editor**. Deje el nombre de archivo predeterminado (EditorMargin1.cs/vb).  
  
3.  Hay dos archivos de código, como se indica a continuación:  
  
    -   EditorMargin1.cs contiene el `EditorMargin1` clase.  
  
    -   EditorMargin1Factory.cs contiene el `EditorMargin1Factory` clase.  
  
4.  Este proyecto de compilación e iniciar la depuración. Aparece la instancia experimental. Si abre un archivo de texto, un margen verde con las palabras "Hello EditorMargin1" aparece debajo de la barra de desplazamiento horizontal.  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y puntos de extensión del editor](../extensibility/language-service-and-editor-extension-points.md)