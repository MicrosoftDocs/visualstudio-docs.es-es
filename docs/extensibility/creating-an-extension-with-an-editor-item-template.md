---
title: "Crear una extensi&#243;n con una plantilla de elemento de Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos - extensiones"
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Crear una extensi&#243;n con una plantilla de elemento de Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar plantillas de elementos que se incluyen en el SDK de Visual Studio para crear extensiones de editor básico que agregue clasificadores, adornos y márgenes al editor. Las plantillas de elementos de editor están disponibles para proyectos de Visual C\# o Visual Basic VSIX.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear una extensión de clasificador  
 La plantilla de elemento de clasificador Editor crea un clasificador de editor que colorea el texto adecuado \(en este caso, todo el contenido\) en cualquier archivo de texto.  
  
1.  En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el **nombre** escriba `TestClassifier`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. Vaya a Visual C\# **extensibilidad** nodo y seleccione **clasificador Editor**. Deje el nombre de archivo predeterminado \(EditorClassifier1.cs\).  
  
3.  Hay tres archivos de código, como sigue:  
  
    -   EditorClassifier1.cs contiene el `EditorClassifier1` clase.  
  
    -   EditorClassifier1ClassificationDefinition.cs contiene el `OEditorClassifier1ClassificationDefinition` clase.  
  
    -   EditorClassifier1Format.cs contiene el `EditorClassifier1Format`  clase.  
  
    -   EditorClassifier1Provider.cs contiene el `EditorClassifier1Provider` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental de Visual Studio.  
  
     Si abre un archivo de texto, todo el texto está subrayado con un fondo de color violeta.  
  
## Crear una extensión de elemento gráfico texto relativo  
 La plantilla de elementos gráficos de texto del Editor crea un elemento gráfico texto relativo que decora todas las instancias del carácter 'a' mediante un cuadro con un contorno rojo y un fondo azul. Es texto relativo porque el cuadro siempre superposiciones 'a' caracteres, incluso cuando se mueven o cambian.  
  
1.  En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el **nombre** escriba `TestAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. Vaya a Visual C\# **extensibilidad** nodo y seleccione **elementos gráficos de Editor de texto**. Deje el nombre de archivo predeterminado \(TextAdornment1.cs\/vb\).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   TextAdornment1.cs contiene el `TextAdornment1` clase.  
  
    -   extAdornment1TextViewCreationListener.cs contiene el `TextAdornment1TextViewCreationListener` clase.  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si abre un archivo de texto, se describen los 'a' de los caracteres en el texto en rojo con un fondo azul.  
  
## Crear una extensión de elemento gráfico relativa de la ventanilla  
 La plantilla de elemento de gráfico de área de visualización de Editor crea un elemento de gráfico relativa de la ventanilla que agrega un cuadro violeta con un contorno rojo a la esquina superior derecha de la ventanilla.  
  
> [!NOTE]
>  El *ventanilla* es el área de la vista de texto que se muestra actualmente.  
  
#### Para crear una extensión de elemento gráfico viewport mediante la plantilla de elemento de gráfico de área de visualización de Editor  
  
1.  En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el **nombre** escriba `ViewportAdornment`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. Vaya a Visual C\# **extensibilidad** nodo y seleccione **elementos gráficos de ventanilla Editor**. Deje el nombre de archivo predeterminado \(ViewportAdornment1.cs\/vb\).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   ViewportAdornment1.cs contiene el `ViewportAdornment1` clase.  
  
    -   ViewportAdornment1TextViewCreationListener.cs contiene el `ViewportAdornment1TextViewCreationListener` \(clase\)  
  
4.  Compile la solución y comience la depuración. Aparece la instancia experimental. Si crea un nuevo archivo de texto, se muestra un cuadro violeta con un contorno rojo en la esquina superior derecha de la ventanilla.  
  
## Crear una extensión de margen  
 La plantilla de margen del Editor crea un margen de color verde que aparece junto con las palabras "Hello world\!" debajo de la barra de desplazamiento horizontal.  
  
#### Para crear una extensión de margen usando la plantilla de margen del Editor  
  
1.  En el **nuevo proyecto** diálogo cuadro, expanda **Visual C\#** o **Visual Basic** y, a continuación, haga clic en **extensibilidad**. En el **plantillas** panel, seleccione **proyecto VSIX**. En el **nombre** escriba `MarginExtension`. Haga clic en **Aceptar**.  
  
2.  En el **el Explorador de soluciones**, haga clic en el nodo del proyecto y seleccione **Agregar \/ nuevo elemento**. Vaya a Visual C\# **extensibilidad** nodo y seleccione **elementos gráficos de ventanilla Editor**. Deje el nombre de archivo predeterminado \(EditorMargin1.cs\/vb\).  
  
3.  Hay dos archivos de código, como sigue:  
  
    -   EditorMargin1.cs contiene el `EditorMargin1` clase.  
  
    -   EditorMargin1Factory.cs contiene el `EditorMargin1Factory` clase.  
  
4.  Compile este proyecto e iniciar la depuración. Aparece la instancia experimental. Si abre un archivo de texto, se muestra un margen de color verde que contiene las palabras "Hello EditorMargin1" debajo de la barra de desplazamiento horizontal.  
  
## Vea también  
 [Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)