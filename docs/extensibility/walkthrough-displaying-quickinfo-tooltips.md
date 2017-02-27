---
title: "Tutorial: Mostrar informaci&#243;n sobre herramientas de QuickInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos - información rápida"
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Tutorial: Mostrar informaci&#243;n sobre herramientas de QuickInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Información rápida es una característica de IntelliSense que muestra las firmas de método y descripciones cuando un usuario mueve el puntero sobre un nombre de método. Puede implementar características de lenguaje como QuickInfo definiendo los identificadores para los que desea proporcionar descripciones de QuickInfo y, a continuación, crear una información sobre herramientas en la que se va a mostrar el contenido. Puede definir información rápida en el contexto de un servicio de lenguaje, puede definir su propio tipo de contenido y la extensión de nombre de archivo y mostrar la información rápida para ese tipo o puede mostrar información rápida para un tipo de contenido existente \(por ejemplo, "text"\). Este tutorial muestra cómo mostrar información rápida para el tipo de contenido "text".  
  
 En el ejemplo de QuickInfo en este tutorial se muestra la información sobre herramientas cuando un usuario mueve el puntero sobre un nombre de método. Este diseño requiere que implementan estas cuatro interfaces:  
  
-   interfaz de origen  
  
-   interfaz del proveedor de origen  
  
-   interfaz de controlador  
  
-   interfaz del proveedor de controlador  
  
 Los proveedores de origen y el controlador son componentes de Managed Extensibility Framework \(MEF\) y están responsables de la exportación de las clases de origen y el controlador e importar servicios y negocia como el <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, que crea el búfer de texto de información sobre herramientas y el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, que desencadena la sesión de información rápida.  
  
 En este ejemplo, el origen de información rápida usa una lista codificada de forma rígida de nombres de método y descripciones, pero en implementaciones completas, el servicio de lenguaje y la documentación de lenguaje son responsables de proporcionar ese contenido.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto MEF  
  
#### Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de VSIX de C\#. \(En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C\# \/ extensibilidad**, a continuación, **proyecto VSIX**.\) El nombre de la solución `QuickInfoTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## Implementar el origen de información rápida  
 El origen de información rápida es responsable de recopilar el conjunto de identificadores y sus descripciones y agregar el contenido en el búfer de texto de información sobre herramientas cuando se encuentra uno de los identificadores. En este ejemplo, los identificadores y sus descripciones se acaba de agregar en el constructor de origen.  
  
#### Para implementar el origen de información rápida  
  
1.  Agregue un archivo de clase y asígnele el nombre `TestQuickInfoSource`.  
  
2.  Agregue una referencia a Microsoft.VisualStudio.Language.IntelliSense.  
  
3.  Agregue las siguientes importaciones.  
  
     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-cs[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]  
  
4.  Declare una clase que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>, y asígnele el nombre `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-cs[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]  
  
5.  Agregar campos para el proveedor de código fuente de información rápida, el búfer de texto y un conjunto de nombres de método y las firmas de método. En este ejemplo, los nombres de método y las firmas se inicializan en el `TestQuickInfoSource` constructor.  
  
     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-cs[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]  
  
6.  Agregue un constructor que establece el proveedor de código fuente de información rápida y el búfer de texto y rellena el conjunto de nombres de método y las firmas de método y descripciones.  
  
     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-cs[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]  
  
7.  Implemente el método <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. En este ejemplo, el método busca la palabra actual o la palabra anterior si el cursor está al final de una línea o un búfer de texto. Si la palabra es uno de los nombres de método, la descripción de ese nombre de método se agrega el contenido de QuickInfo.  
  
     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-cs[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]  
  
8.  También debe implementar un método Dispose\(\), ya que <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> implementa <xref:System.IDisposable>:  
  
     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-cs[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]  
  
## Implementación de un proveedor de origen de información rápida  
 El proveedor del origen de QuickInfo sirve principalmente para exportar como un componente MEF y crear una instancia del origen de información rápida. Dado que es un componente MEF, puede importar otros componentes MEF.  
  
#### Para implementar un proveedor de código fuente de información rápida  
  
1.  Declarar un proveedor de origen de QuickInfo denominado `TestQuickInfoSourceProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>, y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "Origen de información rápida de información sobre herramientas", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de antes de \= "default" y una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto".  
  
     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-cs[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]  
  
2.  Importar dos servicios de editor, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> y <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, como propiedades de `TestQuickInfoSourceProvider`.  
  
     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-cs[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]  
  
3.  Implemente <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> para devolver un nuevo `TestQuickInfoSource`.  
  
     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-cs[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]  
  
## Implementar un controlador de información rápida  
 Controladores de QuickInfo determinan cuándo se debe mostrar la información rápida. En este ejemplo, se muestra información rápida cuando el puntero está sobre una palabra que corresponde a uno de los nombres de método. El controlador de QuickInfo implementa un controlador de eventos de desplazamiento del mouse que activa una sesión de información rápida.  
  
#### Para implementar un controlador de información rápida  
  
1.  Declare una clase que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>, y asígnele el nombre `TestQuickInfoController`.  
  
     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-cs[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]  
  
2.  Agregue campos privados para la vista de texto, los búferes de texto que se representan en la vista de texto, la sesión de información rápida y el proveedor del controlador de QuickInfo.  
  
     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-cs[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]  
  
3.  Agregue un constructor que establece los campos y agrega el controlador de eventos del mouse al mantener el mouse.  
  
     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-cs[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]  
  
4.  Agregue el controlador de eventos de desplazamiento del mouse que activa la sesión de información rápida.  
  
     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-cs[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]  
  
5.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> método por lo que TI quita el controlador de eventos del mouse al mantener el mouse cuando se desasocia el controlador de la vista de texto.  
  
     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-cs[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]  
  
6.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> método y <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> método como métodos vacíos para este ejemplo.  
  
     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-cs[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]  
  
## Implementar el proveedor del controlador de información rápida  
 El proveedor del controlador QuickInfo sirve principalmente para exportar como un componente MEF y crear una instancia del controlador de QuickInfo. Dado que es un componente MEF, puede importar otros componentes MEF.  
  
#### Para implementar el proveedor del controlador de información rápida  
  
1.  Declare una clase denominada `TestQuickInfoControllerProvider` que implementa <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>, y se exporta con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "Controlador de información rápida de información sobre herramientas" y un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto":  
  
     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-cs[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]  
  
2.  Importar el <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> como una propiedad.  
  
     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-cs[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]  
  
3.  Implemente el <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> método creando una instancia del controlador de QuickInfo.  
  
     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-cs[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]  
  
## Compilar y probar el código  
 Para probar este código, compile la solución QuickInfoTest y ejecútelo en la instancia experimental.  
  
#### Para compilar y probar la solución QuickInfoTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Crear un archivo de texto, escriba algún texto que incluye las palabras "Agregar" y "subtract".  
  
4.  Mueva el puntero sobre una de las apariciones de "Agregar". La firma y la descripción de la `add` método debe mostrarse.  
  
## Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)