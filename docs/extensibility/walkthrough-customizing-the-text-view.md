---
title: 'Tutorial: personalizar la vista de texto | Microsoft Docs'
description: Para obtener información sobre cómo personalizar una vista de texto, modifique cualquiera de las distintas propiedades de la asignación de formato de editor mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5ef4d0b408afc00a806e73d1e2eae7a07dde7814
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216857"
---
# <a name="walkthrough-customize-the-text-view"></a>Tutorial: personalizar la vista de texto
Puede personalizar una vista de texto modificando cualquiera de las siguientes propiedades en la asignación de formato del editor:

- Margen del indicador

- Símbolo de intercalación de inserción

- Sobrescribir símbolo de intercalación

- Texto seleccionado

- Texto seleccionado inactivo (es decir, el texto seleccionado que pierde el foco)

- Espacio en blanco visible

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad** y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `ViewPropertyTest` .

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="define-the-content-type"></a>Definir el tipo de contenido

1. Agregue un archivo de clase y asígnele el nombre `ViewPropertyModifier`.

2. Agregue las siguientes directivas `using`:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Declare una clase denominada `TestViewCreationListener` que herede de <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Exporte esta clase con los siguientes atributos:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> para especificar el tipo de contenido al que se aplica este agente de escucha.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> para especificar el rol de este agente de escucha.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. En esta clase, importe <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Cambiar las propiedades de la vista

1. Configure el <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> método para que las propiedades de la vista se cambien cuando se abra la vista. Para hacer el cambio, busque primero el <xref:System.Windows.ResourceDictionary> que corresponde al aspecto de la vista que desea buscar. A continuación, cambie la propiedad adecuada en el Diccionario de recursos y establezca las propiedades. Procesa por lotes las llamadas al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> método llamando al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> método antes de establecer las propiedades y, a continuación, <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> después de establecer las propiedades.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Compilar y probar el código

1. Compile la solución.

     Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

2. Cree un archivo de texto y escriba algún texto.

    - El símbolo de intercalación de inserción debe ser magenta y el símbolo de intercalación de sobrescritura debe ser turquesa.

    - El margen del indicador (a la izquierda de la vista de texto) debe ser verde claro.

3. Seleccione el texto que escribió. El color del texto seleccionado debe ser rosa claro.

4. Mientras el texto está seleccionado, haga clic en cualquier lugar fuera de la ventana de texto. El color del texto seleccionado debe ser rosa oscuro.

5. Active el espacio en blanco visible. (En el menú **edición** , seleccione **avanzadas** y, a continuación, haga clic en **Ver espacio en blanco**). Escriba algunas pestañas en el texto. Deben mostrarse las flechas rojas que representan las pestañas.

## <a name="see-also"></a>Consulte también
- [Puntos de extensión de editor y servicio de lenguaje](../extensibility/language-service-and-editor-extension-points.md)
