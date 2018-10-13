---
title: Introducción a la plantilla de proyecto VSIX | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dfb70a3ae8321f1c1d0d04299919c82fe9ee2198
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223527"
---
# <a name="getting-started-with-the-vsix-project-template"></a>Introducción a la plantilla de proyecto de VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar la plantilla de proyecto de VSIX para crear una extensión o para una extensión existente para la implementación del paquete. La plantilla de proyecto de VSIX tiene las versiones de Visual Basic y Visual C# y se instala como parte del SDK de Visual Studio.  
  
 La plantilla de proyecto de VSIX solo consta de un archivo source.extension.vsixmanifest, que contiene información acerca de la extensión y los recursos que se incluye.  
  
 Para buscar la plantilla de proyecto VSIX, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="deploying-a-custom-project-template-using-the-vsix-project-template"></a>Implementar una plantilla de proyecto personalizado mediante la plantilla de proyecto de VSIX  
 Los pasos siguientes muestran cómo usar el proyecto VSIX para empaquetar una plantilla de proyecto que se puede compartir con otros desarrolladores o cargar en la Galería de Visual Studio.  
  
1.  Crear una plantilla de proyecto.  
  
    1.  Abra el proyecto desde el que se va a crear una plantilla. Este proyecto puede ser de cualquier tipo de proyecto.  
  
    2.  En el menú **Archivo**, haga clic en **Exportar plantilla**. Complete los pasos del asistente.  
  
         Se crea un archivo .zip en %USERPROFILE%\My Documents\Visual Studio  *\<versión >* \My Exported Templates\\.  
  
2.  Crear un proyecto VSIX vacío.  
  
     En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**. Seleccione **Visual Basic** o **Visual C#**. En el nodo seleccionado, seleccione **extensibilidad**y, a continuación, seleccione **proyecto VSIX**.  
  
3.  Agregue el archivo .zip al proyecto. Establezca su **Copy to Output Directory** propiedad `Copy Always`.  
  
4.  En el **el Explorador de soluciones**, haga doble clic en el `source.extension.vsixmanifest` archivo para abrirlo en el **el Diseñador de manifiestos VSIX**y, a continuación, realice los cambios siguientes:  
  
    -   Establecer el **Product Name** campo **mi plantilla de proyecto**.  
  
    -   Establecer el **Id. de producto** campo **MyProjectTemplate - 1**.  
  
    -   Establecer el **autor** campo **Fabrikam**.  
  
    -   Establecer el **descripción** campo **mi plantilla de proyecto**.  
  
    -   En el **activos** sección, agregue un **Microsoft.VisualStudio.ProjectTemplate** escriba y establezca su ruta de acceso en el nombre del archivo zip.  
  
5.  Guarde y cierre el archivo source.extension.vsixmanifest.  
  
6.  Compile el proyecto.  
  
7.  En el directorio de resultados, haga doble clic en el archivo. vsix.  
  
8.  Un **instalador de VSIX** aparece el cuadro de mensaje. Siga las instrucciones para instalar la extensión.  
  
9. Cierre Visual Studio y, a continuación, vuelva a abrirlo.  
  
10. Seleccione **extensiones y actualizaciones** (en el **herramientas** menú) y seleccione el **plantillas** categoría. Debe ser una de las extensiones disponibles **mi plantilla de proyecto**.  
  
11. La plantilla de proyecto nuevo aparece en la **nuevo proyecto** cuadro de diálogo en el mismo lugar que la plantilla de proyecto original. Por ejemplo, si ha creado una plantilla denominada **VB consola** desde una aplicación de consola de Visual Basic, **VB consola** aparece en el mismo panel, como Visual Basic **aplicación de consola**plantilla.  
  
#### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar la ubicación de la plantilla en el cuadro de diálogo nuevo proyecto  
  
1.  Las carpetas de plantillas se encuentran en el *ruta de instalación de Visual Studio*\Common7\IDE\ProjectTemplates y *ruta de instalación de Visual Studio*\Common7\IDE\ItemTemplates directorios. Los nombres de las secciones de nivel superior en el cuadro de diálogo nuevo proyecto no coincidan con los nombres de las carpetas de plantilla. Si difieren, use el nombre de la carpeta de plantillas.  
  
     Cambie la extensión .vsix del archivo a .zip y, a continuación, abra el archivo.  
  
2.  Cree una nueva carpeta con el mismo nombre que la sección del cuadro de diálogo nuevo proyecto de en que la plantilla debe aparecer.  
  
3.  Si la plantilla que se va a aparecer en una subsección, cree una subcarpeta del mismo nombre.  
  
4.  Mueva el archivo .zip de plantilla en la nueva carpeta.  
  
5.  Cambie la extensión .zip para VSIX.  
  
6.  Abra el manifiesto VSIX.  
  
7.  En el manifiesto de VSIX, actualice el **activos** ruta de acceso de la plantilla de forma que apunte a la raíz del árbol del directorio que contiene el archivo de plantilla. Por ejemplo, si la plantilla está en \CSharp\Windows, la referencia debe apuntar a \CSharp.

