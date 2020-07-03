---
title: Introducción con la plantilla de Proyecto VSIX | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ca9672b22120718f63638d8668812d0e42e41f
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905877"
---
# <a name="get-started-with-the-vsix-project-template"></a>Introducción a la plantilla de proyecto de VSIX

Puede usar la plantilla de Proyecto VSIX para crear una extensión o empaquetar una extensión existente para la implementación. La plantilla de Proyecto VSIX tiene dos Visual Basic y versiones de Visual C#, y se instala como parte del SDK de Visual Studio.

 La plantilla de Proyecto VSIX solo consta de un archivo *source. Extension. vsixmanifest* , que contiene información sobre la extensión y los recursos que se suministran.

 Para buscar la plantilla de proyecto de VSIX, debe instalar el SDK de Visual Studio. Para obtener más información, vea el [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Implementar una plantilla de proyecto personalizada mediante la plantilla de Proyecto VSIX

 En los pasos siguientes se muestra cómo usar el Proyecto VSIX para empaquetar una plantilla de proyecto que puede compartir con otros desarrolladores o cargar en la galería de Visual Studio.

1. Cree una plantilla de proyecto.

    1. Abra el proyecto desde el que se va a crear una plantilla. Este proyecto puede ser de cualquier tipo de proyecto.

    2. En el menú **Proyecto**, haga clic en **Exportar plantilla**. Complete los pasos del asistente.

         Se crea un archivo *. zip* en *%userprofile%\My documentos\Visual Studio {version} \My Exported templates \\ *.

2. Cree un proyecto VSIX vacío.

     Seleccione **File (Archivo)**  > **New (Nuevo)**  > **Project (Proyecto)** . En el cuadro de búsqueda, escriba "VSIX" y seleccione la versión de **C#** o **Visual Basic** del **Proyecto VSIX**.

3. Agregue el archivo *. zip* al proyecto. Establezca su propiedad **Copiar en el directorio de salida** en `Copy Always` .

4. En **Explorador de soluciones**, haga doble clic en el archivo *source. Extension. vsixmanifest* para abrirlo en el **Diseñador de manifiestos VSIX**y, a continuación, realice los cambios siguientes:

    - Establezca el campo **nombre de producto** en **mi plantilla de proyecto**.

    - Establezca el campo ID. de **producto** en **MyProjectTemplate-1**.

    - Establezca el campo **autor** en **Fabrikam**.

    - Establezca el campo **Descripción** en **mi plantilla de proyecto**.

    - En la sección **activos** , agregue un tipo **Microsoft. VisualStudio. ProjectTemplate** y establezca su ruta de acceso en el nombre del archivo *. zip* .

5. Guarde y cierre el archivo *source. Extension. vsixmanifest* .

6. Compile el proyecto.

7. En el directorio de salida, haga doble clic en el archivo *. vsix* .

8. Aparece un cuadro de mensaje del **instalador de VSIX** . Siga las instrucciones para instalar la extensión.

9. Cierre Visual Studio y vuelva a abrirlo.

::: moniker range="vs-2017"

10. Seleccione **extensiones y actualizaciones** (en el menú **herramientas** ) y seleccione la categoría **plantillas** . Una de las extensiones disponibles debe ser **mi plantilla de proyecto**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Seleccione **administrar extensiones** (en el menú **extensiones** ) y seleccione la categoría **plantillas** . Una de las extensiones disponibles debe ser **mi plantilla de proyecto**.

::: moniker-end

11. La nueva plantilla de proyecto aparece en el cuadro de diálogo **nuevo proyecto** en el mismo lugar que la plantilla de proyecto original. Por ejemplo, si creó una plantilla denominada **consola de VB** desde una aplicación de consola de Visual Basic, la **consola de VB** aparece en el mismo panel que la plantilla de aplicación de **consola** de Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Para especificar la ubicación de la plantilla en el cuadro de diálogo nuevo proyecto

1. Las carpetas de plantillas se encuentran en los directorios *{ruta de instalación de Visual Studio} \Common7\IDE\ProjectTemplates* y *{ruta de instalación de Visual Studio} \Common7\IDE\ItemTemplates* . Los nombres de las secciones de nivel superior del cuadro de diálogo **nuevo proyecto** no coinciden exactamente con los nombres de las carpetas de plantilla. En qué difieren, use el nombre de la carpeta de plantillas.

    Cambie la extensión de archivo *. vsix* a *. zip*y, a continuación, abra el archivo.

2. Cree una nueva carpeta con el mismo nombre que la sección del cuadro de diálogo **nuevo proyecto** en el que debe aparecer la plantilla.

3. Si la plantilla va a aparecer en una subsección, cree una subcarpeta con el mismo nombre.

4. Mueva el archivo *. zip* de la plantilla a la nueva carpeta.

5. Cambie la extensión *. zip* a *. vsix*.

6. Abra el manifiesto de VSIX.

7. En el manifiesto de VSIX, actualice la ruta de acceso del **recurso** de la plantilla para que apunte a la raíz del árbol de directorio que contiene el archivo de plantilla. Por ejemplo, si la plantilla está en *\CSharp\Windows*, la referencia debe apuntar a *\CSharp*.
