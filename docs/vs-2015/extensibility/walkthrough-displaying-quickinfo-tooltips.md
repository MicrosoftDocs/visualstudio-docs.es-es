---
title: 'Tutorial: Mostrar información rápida | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 79ce531d36b21ab26cf4c6e6dc76e8c4d98d8763
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997582"
---
# <a name="walkthrough-displaying-quickinfo-tooltips"></a>Tutorial: Mostrar información sobre herramientas de QuickInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Información rápida es una característica de IntelliSense que muestra las firmas de método y descripciones cuando un usuario mueve el puntero sobre un nombre de método. Puede implementar las características de lenguaje como QuickInfo definiendo los identificadores para el que desea proporcionar descripciones de QuickInfo y, a continuación, crear una información sobre herramientas en el que se va a mostrar el contenido. Puede definir información rápida en el contexto de un servicio de lenguaje, o puede definir su propio tipo de contenido y la extensión de nombre de archivo y mostrar la información rápida para solo ese tipo, o puede mostrar información rápida para un tipo de contenido existente (por ejemplo, "text"). En este tutorial se muestra cómo mostrar información rápida para el tipo de contenido "text".  
  
 El ejemplo de información rápida en este tutorial muestra la información sobre herramientas cuando el usuario mueve el puntero sobre un nombre de método. Este diseño requiere que implementan estas cuatro interfaces:  
  
- interfaz de origen  
  
- interfaz del proveedor de origen  
  
- interfaz de controlador  
  
- interfaz del proveedor de controlador  
  
  Los proveedores de origen y el controlador son partes de componentes de Managed Extensibility Framework (MEF) y son responsables de la exportación de las clases de origen y el controlador e importar servicios y agentes, como el <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, que crea el texto de información sobre herramientas búfer y el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, lo que desencadena la sesión de información rápida.  
  
  En este ejemplo, el origen de QuickInfo usa una lista codificada de forma rígida de los nombres de método y descripciones, pero en implementaciones completas, el servicio de lenguaje y la documentación del lenguaje son responsables de proporcionar ese contenido.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `QuickInfoTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-the-quickinfo-source"></a>Implementar el origen de información rápida  
 El origen de QuickInfo es responsable de recopilar el conjunto de identificadores y sus descripciones y agregar el contenido en el búfer de texto de información sobre herramientas cuando se encuentra uno de los identificadores. En este ejemplo, los identificadores y sus descripciones se acaba de agregar en el constructor de origen.  
  
#### <a name="to-implement-the-quickinfo-source"></a>Para implementar el origen de información rápida  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestQuickInfoSource`.  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Agregue las siguientes importaciones.  
  
     [!code-csharp[VSSDKQuickInfoTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#1)]
     [!code-vb[VSSDKQuickInfoTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#1)]  
  
4.  Declare una clase que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>y asígnele el nombre `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#2)]
     [!code-vb[VSSDKQuickInfoTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#2)]  
  
5.  Agregar campos para el proveedor de código fuente de información rápida, el búfer de texto y un conjunto de firmas de método y los nombres de método. En este ejemplo, las firmas y los nombres de método se inicializan en el `TestQuickInfoSource` constructor.  
  
     [!code-csharp[VSSDKQuickInfoTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#3)]
     [!code-vb[VSSDKQuickInfoTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#3)]  
  
6.  Agregue un constructor que establece el proveedor de código fuente de QuickInfo y el búfer de texto y rellena el conjunto de nombres de método y las firmas de método y las descripciones.  
  
     [!code-csharp[VSSDKQuickInfoTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#4)]
     [!code-vb[VSSDKQuickInfoTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#4)]  
  
7.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. En este ejemplo, el método busca la palabra actual o la palabra anterior si el cursor está al final de una línea o un búfer de texto. Si la palabra es uno de los nombres de método, la descripción de ese nombre de método se agrega el contenido de QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#5)]
     [!code-vb[VSSDKQuickInfoTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#5)]  
  
8.  También debe implementar un método Dispose(), ya que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable>:  
  
     [!code-csharp[VSSDKQuickInfoTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#6)]
     [!code-vb[VSSDKQuickInfoTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#6)]  
  
## <a name="implementing-a-quickinfo-source-provider"></a>Implementar un proveedor de origen de QuickInfo  
 El proveedor del origen de QuickInfo sirve principalmente para exportar a sí mismo como parte del componente MEF y crear una instancia del origen de información rápida. Dado que es un componente MEF, pueden importar otros componentes de MEF.  
  
#### <a name="to-implement-a-quickinfo-source-provider"></a>Para implementar un proveedor de código fuente de información rápida  
  
1.  Declarar un proveedor de código fuente de QuickInfo denominado `TestQuickInfoSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de información sobre herramientas QuickInfo "origen", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de Before = "default" y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text".  
  
     [!code-csharp[VSSDKQuickInfoTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#7)]
     [!code-vb[VSSDKQuickInfoTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#7)]  
  
2.  Importar dos servicios del editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, como propiedades de `TestQuickInfoSourceProvider`.  
  
     [!code-csharp[VSSDKQuickInfoTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#8)]
     [!code-vb[VSSDKQuickInfoTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#8)]  
  
3.  Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para devolver un nuevo `TestQuickInfoSource`.  
  
     [!code-csharp[VSSDKQuickInfoTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#9)]
     [!code-vb[VSSDKQuickInfoTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#9)]  
  
## <a name="implementing-a-quickinfo-controller"></a>Implementar un controlador de QuickInfo  
 Los controladores de QuickInfo determinan cuándo se debe mostrar información rápida. En este ejemplo, información rápida se muestra cuando el puntero está sobre una palabra que se corresponde con uno de los nombres de método. El controlador de QuickInfo implementa un controlador de eventos de al mantener el puntero del mouse que desencadena una sesión de información rápida.  
  
#### <a name="to-implement-a-quickinfo-controller"></a>Para implementar un controlador de QuickInfo  
  
1.  Declare una clase que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>y asígnele el nombre `TestQuickInfoController`.  
  
     [!code-csharp[VSSDKQuickInfoTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#10)]
     [!code-vb[VSSDKQuickInfoTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#10)]  
  
2.  Agregue los campos privados de la vista de texto, los búferes de texto representados en la vista de texto, la sesión de QuickInfo y el proveedor del controlador de QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#11)]
     [!code-vb[VSSDKQuickInfoTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#11)]  
  
3.  Agregue un constructor que establece los campos y agrega el controlador de eventos al mantener el puntero del mouse.  
  
     [!code-csharp[VSSDKQuickInfoTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#12)]
     [!code-vb[VSSDKQuickInfoTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#12)]  
  
4.  Agregue el controlador de eventos de al mantener el puntero del mouse que desencadena la sesión de información rápida.  
  
     [!code-csharp[VSSDKQuickInfoTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#13)]
     [!code-vb[VSSDKQuickInfoTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#13)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> método por lo que TI quita el controlador de eventos al mantener el puntero del mouse cuando se desasocia el controlador de la vista de texto.  
  
     [!code-csharp[VSSDKQuickInfoTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#14)]
     [!code-vb[VSSDKQuickInfoTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#14)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> método y el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método como métodos vacíos en este ejemplo.  
  
     [!code-csharp[VSSDKQuickInfoTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#15)]
     [!code-vb[VSSDKQuickInfoTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#15)]  
  
## <a name="implementing-the-quickinfo-controller-provider"></a>Implementar el proveedor del controlador de QuickInfo  
 El proveedor del controlador de QuickInfo sirve principalmente para exportar a sí mismo como parte del componente MEF y crear una instancia del controlador de QuickInfo. Dado que es un componente MEF, pueden importar otros componentes de MEF.  
  
#### <a name="to-implement-the-quickinfo-controller-provider"></a>Para implementar el proveedor del controlador de QuickInfo  
  
1.  Declare una clase llamada `TestQuickInfoControllerProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "Controlador de QuickInfo información sobre herramientas" y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text":  
  
     [!code-csharp[VSSDKQuickInfoTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#16)]
     [!code-vb[VSSDKQuickInfoTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#16)]  
  
2.  Importe el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como una propiedad.  
  
     [!code-csharp[VSSDKQuickInfoTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#17)]
     [!code-vb[VSSDKQuickInfoTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#17)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> método al crear una instancia del controlador de QuickInfo.  
  
     [!code-csharp[VSSDKQuickInfoTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkquickinfotest/cs/testquickinfosource.cs#18)]
     [!code-vb[VSSDKQuickInfoTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkquickinfotest/vb/testquickinfosource.vb#18)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución QuickInfoTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-quickinfotest-solution"></a>Para compilar y probar la solución QuickInfoTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto que incluye las palabras "Agregar" y "restar".  
  
4.  Mueva el puntero sobre una de las apariciones de "Agregar". La firma y la descripción de la `add` método se debe mostrar.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Vinculación de un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
