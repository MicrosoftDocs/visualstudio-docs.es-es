---
title: "Introducción al servicio de lenguaje y extensiones de Editor | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introducción al servicio de lenguaje y extensiones de Editor
Puede utilizar extensiones de editor para agregar características del servicio de lenguaje como la esquematización, coincidencia de llaves, IntelliSense y las bombillas a su propio lenguaje de programación o a cualquier tipo de contenido. También puede personalizar la apariencia y el comportamiento del editor de Visual Studio, por ejemplo, texto de color, los márgenes, elementos gráficos y otros elementos visuales. También puede definir su propio tipo de contenido y especificar la apariencia y el comportamiento de las vistas de texto en el que aparece el contenido.  
  
 Para empezar a escribir extensiones de editor, use las plantillas de proyecto de editor que se instalan como parte del SDK de Visual Studio. El SDK de Visual Studio es un conjunto de herramientas que facilitan el desarrollo de extensiones de Visual Studio mediante VSPackages o utilizando Managed Extensibility Framework (MEF) que se puede descargar.  
  
> [!NOTE]
>  Para obtener más información sobre el SDK de Visual Studio, consulte [SDK de Visual Studio](../extensibility/visual-studio-sdk.md).  
  
 Se recomienda que conozca los siguientes conceptos y tecnologías antes de escribir sus propias extensiones de editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) y extensiones de Editor  
 La interfaz de usuario del editor de Visual Studio (IU) se implementa mediante Windows Presentation Foundation (WPF). WPF proporciona una experiencia visual enriquecida y un modelo de programación coherente que separa los aspectos visuales del código de la lógica de negocios. Puede utilizar muchas características y elementos de WPF al crear extensiones de editor. Para obtener más información, consulte [Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) y extensiones de Editor  
 El editor de Visual Studio utiliza Managed Extensibility Framework (MEF) para administrar sus componentes y extensiones. MEF también permite a los desarrolladores más fácil crear extensiones para una aplicación host como Visual Studio. En este marco, defina una extensión según un contrato MEF y expórtelo como un componente MEF. La aplicación host administra las partes componentes encontrarlos, registrarlos y asegurándose de que se aplican al contexto correcto.  
  
> [!NOTE]
>  Para obtener más información acerca de MEF en el editor, vea [Managed Extensibility Framework en el Editor de](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Puntos de extensión del Editor de Visual Studio y extensiones  
 Puntos de extensión del Editor son partes de componentes MEF que puede personalizar y ampliar. En algunos casos se amplía el punto de extensión implementando una interfaz y exportarlo junto con los metadatos correctos. En otros casos simplemente declarar una extensión y expórtelo como un tipo determinado.  
  
 Éstos son algunos de los tipos básicos de extensiones de editor:  
  
-   Márgenes y barras de desplazamiento  
  
-   Etiquetas  
  
-   Elementos gráficos  
  
-   Opciones  
  
-   IntelliSense  
  
 Para obtener más información acerca de los puntos de extensión del editor, vea [servicio de lenguaje y los puntos de extensión del Editor de](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Implementar extensiones de Editor  
 En Visual Studio, implementar extensiones de editor agregando un archivo de metadatos denominado source.extension.vsixmanifest a la solución, compilar la solución y, a continuación, una copia de los archivos binarios y el manifiesto en una carpeta que se conoce a Visual Studio. El archivo de manifiesto define los hechos básicos acerca de la extensión (por ejemplo, nombre, autor, versión y tipo de contenido). Para obtener más información sobre el archivo de manifiesto de VSIX y cómo implementar extensiones, consulte [envío extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Cuando se instala una extensión en un equipo, incluyen los archivos binarios y el manifiesto en una subcarpeta de la carpeta que se conoce a Visual Studio.  
  
> [!WARNING]
>  No tiene que preocuparse por los detalles de los manifiestos y ubicaciones de implementación si utiliza una de las plantillas de extensibilidad de editor que se incluyen en Visual Studio. Las plantillas contienen todo lo necesario para registrar e implementar una extensión.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Ejecuta las extensiones en la instancia Experimental  
 Puede aislar su versión de Visual Studio mientras desarrolla una extensión mediante la implementación en la siguiente carpeta experimental (en Windows Vista y Windows 7):  
  
 *% LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*empresa*\\*ExtensionID*  
  
 donde *% LOCALAPPDATA %* es el nombre del usuario ha iniciado sesión, *empresa* es el nombre de la empresa que posee la extensión y *ExtensionID* es el identificador de la extensión.  
  
 Al implementar una extensión a la ubicación experimental, se ejecuta en modo de depuración. Se inicia una segunda instancia de Visual Studio y se denomina **Microsoft Visual Studio - instancia Experimental**.  
  
## <a name="managing-extensions"></a>Administración de extensiones  
 Se muestran las extensiones de Visual Studio en **extensiones y actualizaciones** (en el **herramientas** menú). Si va a probar una extensión en la instancia experimental, aparece en **extensiones y actualizaciones** en la instancia experimental, pero no aparece en la instancia de desarrollo.  
  
 Para obtener más información, consulte [búsqueda y uso de extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Usar plantillas para crear extensiones de Editor  
 Puede utilizar plantillas de editor para crear extensiones MEF que personalizar clasificadores, adornos y los márgenes. Hay plantillas para proyectos de C# y Visual Basic. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 También puede utilizar la plantilla de proyecto VSIX para crear extensiones. Esta plantilla proporciona solo los elementos necesarios para implementar cualquier tipo de extensión e incluya el archivo source.extension.vsixmanifest, las referencias de ensamblado necesarias y un archivo de proyecto que incluye las tareas de compilación que le permiten implementar la extensión. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
 También puede crear editor componentes MEF desde una extensión de paquete de Visual Studio. Vea los siguientes tutoriales para obtener más información:  
  
-   [Tutorial: Usar un comando de Shell con una extensión del Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Tutorial: Usar una tecla de método abreviado con una extensión del Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vea también  
 [Servicio de lenguaje y los puntos de extensión del Editor](../extensibility/language-service-and-editor-extension-points.md)
