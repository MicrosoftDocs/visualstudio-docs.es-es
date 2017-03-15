---
title: "Introducci&#243;n a la plantilla de proyecto VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SDK de Visual Studio, la plantilla de proyecto de VSIX"
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Introducci&#243;n a la plantilla de proyecto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede utilizar la plantilla de proyecto VSIX para crear una extensión o empaquetar una extensión existente para la implementación. La plantilla de proyecto de VSIX tiene las versiones de Visual Basic y Visual C\# y se instala como parte del SDK de Visual Studio.  
  
 La plantilla de proyecto de VSIX sólo consta de un archivo source.extension.vsixmanifest, que contiene información sobre la extensión y los activos que se distribuye.  
  
 Para buscar la plantilla de proyecto VSIX, debe instalar el SDK de Visual Studio. Para obtener más información, consulta [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Implementación de una plantilla de proyecto personalizada mediante la plantilla de proyecto de VSIX  
 Los pasos siguientes muestran cómo utilizar el proyecto VSIX para empaquetar una plantilla de proyecto que puede compartir con otros desarrolladores o cargar en la Galería de Visual Studio.  
  
1.  Crear una plantilla de proyecto.  
  
    1.  Abra el proyecto desde el que se va a crear una plantilla. Este proyecto puede ser de cualquier tipo de proyecto.  
  
    2.  En el menú **Archivo**, haga clic en **Exportar plantilla**. Complete los pasos del asistente.  
  
         Se crea un archivo .zip en %USERPROFILE%\\My Documents\\Visual Studio *\< versión \>*\\My Exported Templates\\.  
  
2.  Cree un proyecto VSIX vacío.  
  
     En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**. Seleccione **Visual Basic** o **Visual C\#**. En el nodo seleccionado, seleccione **extensibilidad**, y, a continuación, seleccione **proyecto VSIX**.  
  
3.  Agregue el archivo .zip en el proyecto. Establezca su **Copiar en el directorio de salida** propiedad `Copy Always`.  
  
4.  En el **el Explorador de soluciones**, haga doble clic en el `source.extension.vsixmanifest` para abrirlo en el **Diseñador de manifiestos VSIX**, y, a continuación, realice los siguientes cambios:  
  
    -   Establecer el **Product Name** campo **mi plantilla de proyecto**.  
  
    -   Establecer el **Id. de producto** campo **MyProjectTemplate \- 1**.  
  
    -   Establecer el **autor** campo **Fabrikam**.  
  
    -   Establecer el **descripción** campo **mi plantilla de proyecto**.  
  
    -   En el **activos** sección, agregue un **Microsoft.VisualStudio.ProjectTemplate** tipo y establecer su ruta de acceso en el nombre del archivo zip.  
  
5.  Guarde y cierre el archivo source.extension.vsixmanifest.  
  
6.  Compile el proyecto.  
  
7.  En el directorio de resultados, haga doble clic en el archivo. vsix.  
  
8.  Un **instalador VSIX** aparece el cuadro de mensaje. Siga las instrucciones para instalar la extensión.  
  
9. Cierre Visual Studio y, a continuación, vuelva a abrirlo.  
  
10. Seleccione **extensiones y actualizaciones** \(en el **herramientas** menú\) y seleccione el **plantillas** categoría. Debe ser una de las extensiones disponibles **mi plantilla de proyecto**.  
  
11. La plantilla de proyecto nuevo aparece en el **nuevo proyecto** cuadro de diálogo en el mismo lugar que la plantilla de proyecto original. Por ejemplo, si ha creado una plantilla denominada **consola VB** desde una aplicación de consola de Visual Basic, **consola VB** aparece en el mismo panel, como Visual Basic **aplicación de consola** plantilla.  
  
#### Para especificar la ubicación de la plantilla en el cuadro de diálogo nuevo proyecto  
  
1.  Carpetas de plantilla se encuentran en el *ruta de instalación de Visual Studio*\\Common7\\IDE\\ProjectTemplates y *ruta de instalación de Visual Studio*\\Common7\\IDE\\ItemTemplates directorios. Los nombres de las secciones de nivel superior en el cuadro de diálogo nuevo proyecto no coincidan con los nombres de las carpetas de plantilla. Si difieren, utilice el nombre de la carpeta de plantillas.  
  
     Cambie la extensión de archivo .vsix a .zip y, a continuación, abra el archivo.  
  
2.  Crear una nueva carpeta con el mismo nombre que la sección del cuadro de diálogo nuevo proyecto de en que la plantilla debe aparecer.  
  
3.  Si la plantilla va a aparecer en una subsección, cree una subcarpeta del mismo nombre.  
  
4.  Mueva el archivo .zip de plantilla en la nueva carpeta.  
  
5.  Cambie la extensión de .zip a .vsix.  
  
6.  Abra el manifiesto de VSIX.  
  
7.  En el manifiesto de VSIX, actualice el **activos** ruta de acceso de la plantilla de modo que apunte a la raíz del árbol del directorio que contiene el archivo de plantilla. Por ejemplo, si la plantilla está en \\CSharp\\Windows, la referencia debe señalar a \\CSharp.