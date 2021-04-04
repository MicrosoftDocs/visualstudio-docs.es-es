---
title: 'Tutorial: Mostrar la información sobre herramientas de QuickInfo | Microsoft Docs'
description: Obtenga información sobre cómo mostrar QuickInfo para el contenido de texto mediante este tutorial. QuickInfo muestra firmas de método y descripciones para un nombre de método.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: d374aa41d85b1d64b6623cb99f6183787a2afc53
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217260"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Tutorial: Mostrar información sobre herramientas de QuickInfo
QuickInfo es una característica de IntelliSense que muestra las firmas y descripciones de los métodos cuando el usuario mueve el puntero sobre un nombre de método. Puede implementar características basadas en lenguajes como QuickInfo si define los identificadores para los que desea proporcionar descripciones de QuickInfo y, a continuación, crea una información sobre herramientas en la que mostrar el contenido. Puede definir QuickInfo en el contexto de un servicio de lenguaje, o bien puede definir su propia extensión de nombre de archivo y tipo de contenido, y mostrar el QuickInfo solo para ese tipo o puede mostrar QuickInfo para un tipo de contenido existente (como "texto"). En este tutorial se muestra cómo mostrar QuickInfo para el tipo de contenido "texto".

 En el ejemplo QuickInfo de este tutorial se muestra la información sobre herramientas cuando un usuario mueve el puntero sobre un nombre de método. Este diseño requiere la implementación de estas cuatro interfaces:

- interfaz de origen

- interfaz del proveedor de origen

- interfaz del controlador

- interfaz del proveedor de controlador

  Los proveedores de código fuente y de controlador son elementos de componentes Managed Extensibility Framework (MEF) y son responsables de exportar las clases de código fuente y de controlador, e importar servicios y agentes como <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , que crea el búfer de texto de información sobre herramientas, y <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> , que desencadena la sesión QuickInfo.

  En este ejemplo, el origen de QuickInfo usa una lista codificada de forma rígida de nombres de método y descripciones, pero en implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.

## <a name="prerequisites"></a>Requisitos previos
 A partir de Visual Studio 2015, no es necesario instalar el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad** y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `QuickInfoTest` .

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="implement-the-quickinfo-source"></a>Implementar el origen de QuickInfo
 El origen de QuickInfo es responsable de recopilar el conjunto de identificadores y sus descripciones, y de agregar el contenido al búfer de texto de información sobre herramientas cuando se encuentra uno de los identificadores. En este ejemplo, los identificadores y sus descripciones se agregan simplemente en el constructor de origen.

#### <a name="to-implement-the-quickinfo-source"></a>Para implementar el origen de QuickInfo

1. Agregue un archivo de clase y asígnele el nombre `TestQuickInfoSource`.

2. Agregue una referencia a *Microsoft. VisualStudio. Language. IntelliSense*.

3. Agregue las importaciones siguientes.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet1":::

4. Declare una clase que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> y asígnele el nombre `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet2":::

5. Agregue campos para el proveedor de origen de QuickInfo, el búfer de texto y un conjunto de nombres de método y firmas de método. En este ejemplo, los nombres y las firmas de método se inicializan en el `TestQuickInfoSource` constructor.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet3":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet3":::

6. Agregue un constructor que establezca el proveedor de origen de QuickInfo y el búfer de texto, y rellene el conjunto de nombres de método y las firmas y descripciones de los métodos.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet4":::

7. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. En este ejemplo, el método busca la palabra actual o la palabra anterior si el cursor está al final de una línea o un búfer de texto. Si la palabra es uno de los nombres de método, se agrega la descripción del nombre del método al contenido de QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet5":::

8. También debe implementar un método Dispose (), ya que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable> :

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet6":::

## <a name="implement-a-quickinfo-source-provider"></a>Implementación de un proveedor de origen de QuickInfo
 El proveedor del origen QuickInfo sirve principalmente para exportarse como parte del componente MEF y crear una instancia del origen QuickInfo. Dado que es una parte de componente de MEF, puede importar otras partes de componentes de MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar un proveedor de origen de QuickInfo

1. Declare un proveedor de origen `TestQuickInfoSourceProvider` de QuickInfo denominado que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider> y exporte con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "ToolTip QuickInfo Source", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = "default" y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Text".

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet7":::

2. Importe dos servicios de editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> , como propiedades de `TestQuickInfoSourceProvider` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet8":::

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para devolver un nuevo `TestQuickInfoSource` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet9":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet9":::

## <a name="implement-a-quickinfo-controller"></a>Implementar un controlador de QuickInfo
 Los controladores de QuickInfo determinan cuándo se muestra QuickInfo. En este ejemplo, QuickInfo aparece cuando el puntero se encuentra sobre una palabra que corresponde a uno de los nombres de método. El controlador QuickInfo implementa un controlador de eventos de desplazamiento del mouse que desencadena una sesión de QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Para implementar un controlador de QuickInfo

1. Declare una clase que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController> y asígnele el nombre `TestQuickInfoController` .

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet10":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet10":::

2. Agregue campos privados para la vista de texto, los búferes de texto representados en la vista de texto, la sesión QuickInfo y el proveedor de controlador QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet11":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet11":::

3. Agregue un constructor que establezca los campos y agregue el controlador de eventos de mantener el mouse.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet12":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet12":::

4. Agregue el controlador de eventos de mantener el mouse que desencadena la sesión QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet13":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet13":::

5. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> método para que quite el controlador de eventos de mantener el mouse cuando el controlador se desasocie de la vista de texto.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet14":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet14":::

6. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> método y el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método como métodos vacíos en este ejemplo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet15":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet15":::

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementación del proveedor del controlador QuickInfo
 El proveedor del controlador QuickInfo sirve principalmente para exportarse como una parte del componente MEF y crear una instancia del controlador QuickInfo. Dado que es una parte de componente de MEF, puede importar otras partes de componentes de MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar el proveedor del controlador QuickInfo

1. Declare una clase denominada `TestQuickInfoControllerProvider` que implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider> y expórtelo con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip QuickInfo Controller" y " <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Text":

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet16":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet16":::

2. Importe el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como una propiedad.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet17":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet17":::

3. Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> método creando una instancia del controlador QuickInfo.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb" id="Snippet18":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs" id="Snippet18":::

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución QuickInfoTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar y probar la solución QuickInfoTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya las palabras "Add" y "Retract".

4. Mueva el puntero sobre una de las apariciones de "agregar". Se debe mostrar la firma y la descripción del `add` método.

## <a name="see-also"></a>Consulte también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
