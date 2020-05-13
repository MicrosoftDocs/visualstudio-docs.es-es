---
title: 'Tutorial: Visualización de información sobre herramientas de QuickInfo ( QuickInfo Tooltips) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697434"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Tutorial: Mostrar información sobre herramientas quickInfo
QuickInfo es una característica de IntelliSense que muestra las firmas y descripciones del método cuando un usuario mueve el puntero sobre un nombre de método. Puede implementar características basadas en lenguaje como QuickInfo definiendo los identificadores para los que desea proporcionar descripciones de QuickInfo y, a continuación, creando una información sobre herramientas en la que mostrar el contenido. Puede definir QuickInfo en el contexto de un servicio de lenguaje, o puede definir su propia extensión de nombre de archivo y tipo de contenido y mostrar QuickInfo solo para ese tipo, o puede mostrar QuickInfo para un tipo de contenido existente (por ejemplo, "texto"). En este tutorial se muestra cómo mostrar QuickInfo para el tipo de contenido "texto".

 El ejemplo QuickInfo de este tutorial muestra la información sobre herramientas cuando un usuario mueve el puntero sobre un nombre de método. Este diseño requiere que usted implemente estas cuatro interfaces:

- interfaz de fuente

- interfaz del proveedor de fuentes

- interfaz del controlador

- interfaz del proveedor del controlador

  Los proveedores de origen y controlador son componentes de Managed Extensibility Framework (MEF) y son responsables <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>de exportar las clases <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>de origen y controlador e importar servicios y intermediarios como el , que crea el búfer de texto de información sobre herramientas y el , que desencadena la sesión QuickInfo.

  En este ejemplo, el origen QuickInfo usa una lista codificada de forma rígida de nombres de método y descripciones, pero en las implementaciones completas, el servicio de lenguaje y la documentación de idioma son responsables de proporcionar ese contenido.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no es necesario instalar el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `QuickInfoTest`nombre a la solución .

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="implement-the-quickinfo-source"></a>Implementar el origen QuickInfo
 El origen QuickInfo es responsable de recopilar el conjunto de identificadores y sus descripciones y agregar el contenido al búfer de texto de información sobre herramientas cuando se encuentra uno de los identificadores. En este ejemplo, los identificadores y sus descripciones se agregan en el constructor de origen.

#### <a name="to-implement-the-quickinfo-source"></a>Para implementar el origen QuickInfo

1. Agregue un archivo de clase y asígnele el nombre `TestQuickInfoSource`.

2. Agregue una referencia a *Microsoft.VisualStudio.Language.IntelliSense*.

3. Agregue las importaciones siguientes.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Declare una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>que implemente `TestQuickInfoSource`y asímóctela .

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Agregue campos para el proveedor de origen QuickInfo, el búfer de texto y un conjunto de nombres de método y firmas de método. En este ejemplo, los nombres de método `TestQuickInfoSource` y las firmas se inicializan en el constructor.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Agregue un constructor que establezca el proveedor de origen QuickInfo y el búfer de texto y rellene el conjunto de nombres de método y las firmas y descripciones del método.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. En este ejemplo, el método busca la palabra actual, o la palabra anterior si el cursor está al final de una línea o un búfer de texto. Si la palabra es uno de los nombres de método, la descripción de ese nombre de método se agrega al contenido de QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. También debe implementar un método Dispose(), ya que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> <xref:System.IDisposable>implementa:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Implementar un proveedor de origen QuickInfo
 El proveedor del origen QuickInfo sirve principalmente para exportarse a sí mismo como una parte de componente MEF y crear instancias del origen QuickInfo. Debido a que es una pieza de componente MEF, puede importar otras piezas de componentes MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar un proveedor de origen QuickInfo

1. Declare un proveedor de `TestQuickInfoSourceProvider` código <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>fuente QuickInfo denominado <xref:Microsoft.VisualStudio.Utilities.NameAttribute> que implemente y expórtelo con un de "ToolTip QuickInfo Source", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before-"default" y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Importe dos servicios <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>de editor `TestQuickInfoSourceProvider`y , como propiedades de .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Implementar <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para devolver `TestQuickInfoSource`un nuevo archivo .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Implementar un controlador QuickInfo
 Los controladores QuickInfo determinan cuándo se muestra QuickInfo. En este ejemplo, QuickInfo aparece cuando el puntero está sobre una palabra que corresponde a uno de los nombres de método. El quickInfo controlador implementa un controlador de eventos de desplazamiento del mouse que desencadena una sesión QuickInfo.

### <a name="to-implement-a-quickinfo-controller"></a>Para implementar un controlador QuickInfo

1. Declare una clase <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>que implemente `TestQuickInfoController`y asímóctela .

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Agregue campos privados para la vista de texto, los búferes de texto representados en la vista de texto, la sesión QuickInfo y el proveedor de controlador QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Agregue un constructor que establezca los campos y agregue el controlador de eventos de desplazamiento del mouse.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Agregue el controlador de eventos de desplazamiento del mouse que desencadena la sesión QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> el método para que quite el controlador de eventos de desplazamiento del mouse cuando el controlador se separa de la vista de texto.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> el método <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> y el método como métodos vacíos para este ejemplo.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Implementación del proveedor de controladorquick QuickInfo
 El proveedor del controlador QuickInfo sirve principalmente para exportarse a sí mismo como una parte de componente MEF y crear instancias del controlador QuickInfo. Debido a que es una pieza de componente MEF, puede importar otras piezas de componentes MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar el proveedor de controlador QuickInfo

1. Declare una `TestQuickInfoControllerProvider` clase denominada <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>que implemente y <xref:Microsoft.VisualStudio.Utilities.NameAttribute> expórtela con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "ToolTip QuickInfo Controller" y un de "text":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Importe el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como una propiedad.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> el método creando una instancia del controlador QuickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Construir y probar el Código
 Para probar este código, compile la solución QuickInfoTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar y probar la solución QuickInfoTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya las palabras "añadir" y "restar".

4. Mueva el puntero sobre una de las apariciones de "add". Se deben mostrar la `add` firma y la descripción del método.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
