---
title: "Tutorial: Crear una extensión de proyecto de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1974f32731d8ba45b2210b9d9231a7e69d6905f4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-sharepoint-project-extension"></a>Tutorial: Crear una extensión de proyecto de SharePoint
  Este tutorial muestra cómo crear una extensión para los proyectos de SharePoint. Puede utilizar una extensión de proyecto para responder a eventos de nivel de proyecto, como cuando se agrega, elimina o cambiar el nombre de un proyecto. También puede agregar propiedades personalizadas o responder cuando cambia un valor de propiedad. A diferencia de las extensiones de elemento de proyecto, las extensiones de proyecto no se pueden asociadas con un determinado tipo de proyecto de SharePoint. Cuando se crea una extensión de proyecto, la extensión de carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 En este tutorial, creará una propiedad booleana personalizada que se agrega a cualquier proyecto de SharePoint creado en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Cuando se establece en **True**, la nueva propiedad agrega o asigna una carpeta de recursos de imágenes al proyecto. Cuando se establece en **False**, se quita la carpeta Images, si existe. Para obtener más información, consulte [Cómo: agregar y quitar carpetas asignado](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensión para los proyectos de SharePoint que hace lo siguiente:  
  
    -   Agrega una propiedad de proyecto personalizada a la ventana Propiedades. La propiedad se aplica a cualquier proyecto de SharePoint.  
  
    -   Usa el modelo de objetos de proyecto de SharePoint para agregar una carpeta asignada a un proyecto.  
  
    -   Usa el [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (DTE) para eliminar una carpeta asignada desde el proyecto de modelo de objetos de automatización.  
  
-   Creación de un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para implementar el ensamblado de la extensión de la propiedad proyecto.  
  
-   Depurar y probar la propiedad del proyecto.  
  
## <a name="prerequisites"></a>Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint y [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Este tutorial se utiliza la **proyecto VSIX** plantilla en el [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] para crear un paquete VSIX para implementar la extensión de propiedad de proyecto. Para obtener más información, consulte [extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="creating-the-projects"></a>Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX para implementar la extensión de proyecto.  
  
-   Un proyecto de biblioteca de clases que implementa la extensión de proyecto.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### <a name="to-create-the-vsix-project"></a>Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija la **extensibilidad** nodo.  
  
    > [!NOTE]  
    >  Este nodo está disponible solo si se instala el SDK de Visual Studio. Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework y, a continuación, elija la **proyecto VSIX** plantilla.  
  
5.  En el **nombre** cuadro, escriba **ProjectExtensionPackage**y, a continuación, elija la **Aceptar** botón.  
  
     El **ProjectExtensionPackage** proyecto aparece en **el Explorador de soluciones**.  
  
#### <a name="to-create-the-extension-project"></a>Para crear la extensión de proyecto  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del nodo de solución, elija **agregar**y, a continuación, elija **nuevo proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo, expanda el **Visual C#** o **Visual Basic** nodos y, a continuación, elija **Windows**.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4.5** en la lista de versiones de .NET Framework y, a continuación, elija la **biblioteca de clases** plantilla de proyecto.  
  
4.  En el **nombre** cuadro, escriba **ProjectExtension**y, a continuación, elija la **Aceptar** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Agrega el **ProjectExtension** proyecto a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## <a name="configuring-the-project"></a>Configurar el proyecto  
 Antes de escribir código para crear la extensión de proyecto, agregar archivos de código y las referencias de ensamblado al proyecto de extensión.  
  
#### <a name="to-configure-the-project"></a>Para configurar el proyecto  
  
1.  Agregar un archivo de código que se denomina **CustomProperty** al proyecto ProjectExtension.  
  
2.  Abra el menú contextual para el **ProjectExtension** del proyecto y, a continuación, elija **Agregar referencia**.  
  
3.  En el **Administrador de referencias - CustomProperty** diálogo cuadro, elija la **Framework** nodo y, a continuación, seleccione la casilla situada junto a los ensamblados System.ComponentModel.Composition y System.Windows.Forms.  
  
4.  Elija la **extensiones** nodo, active la casilla situada junto a los ensamblados Microsoft.VisualStudio.SharePoint y EnvDTE y, a continuación, elija la **Aceptar** botón.  
  
5.  En **el Explorador de soluciones**, en la **referencias** carpeta para la **ProjectExtension** proyecto, elija **EnvDTE**.  
  
6.  En el **propiedades** ventana, cambiar la **incrustar tipos de interoperabilidad** propiedad **False**.  
  
## <a name="defining-the-new-sharepoint-project-property"></a>Definir la nueva propiedad de proyecto de SharePoint  
 Cree una clase que defina la extensión de proyecto y el comportamiento de la nueva propiedad de proyecto. Para definir la nueva extensión de proyecto, la clase implementa la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz. Implemente esta interfaz siempre que desee definir una extensión para un proyecto de SharePoint. Además, agregue el <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] detecte y cargue el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementación. Pasar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al constructor del atributo.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Para definir la nueva propiedad de proyecto de SharePoint  
  
1.  Pegue el código siguiente en el archivo de código de CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="building-the-solution"></a>Compilar la solución  
 A continuación, compile la solución para asegurarse de que se compila sin errores.  
  
#### <a name="to-build-the-solution"></a>Para compilar la solución  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-property-extension"></a>Crear un paquete VSIX para implementar la extensión de propiedad de proyecto  
 Para implementar la extensión de proyecto, utilice el proyecto VSIX en la solución para crear un paquete VSIX. Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX. A continuación, cree el paquete VSIX compilando la solución.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Para crear y configurar el paquete VSIX  
  
1.  En **el Explorador de soluciones**, abra el menú contextual del archivo source.extension.vsixmanifest y, a continuación, elija la **abrir** botón.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Abre el archivo en el Diseñador de manifiestos. La información que aparece en el **metadatos** ficha también aparece en la **extensiones y actualizaciones**. Todos los paquetes VSIX requieren el archivo extension.vsixmanifest. Para obtener más información acerca de este archivo, consulte [referencia de 1.0 de esquema de extensión VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el **Product Name** cuadro, escriba **Custom Project Property**.  
  
3.  En el **autor** cuadro, escriba **Contoso**.  
  
4.  En el **descripción** cuadro, escriba **una propiedad de proyecto de SharePoint personalizada que alterna la asignación de la carpeta de recursos de imágenes al proyecto**.  
  
5.  Elija la **activos** ficha y, a continuación, elija la **New** botón.  
  
     El **Agregar nuevo activo** aparece el cuadro de diálogo.  
  
6.  En el **tipo** elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MEFComponent` del archivo extension.vsixmanifest. Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX. Para obtener más información, consulte [elemento MEFComponent (Esquema VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En el **origen** lista, elija la **un proyecto de la solución actual** botón de opción.  
  
8.  En el **proyecto** elija **ProjectExtension**.  
  
     Este valor identifica el nombre del ensamblado que va a compilar en el proyecto.  
  
9. Elija **Aceptar** para cerrar el **Agregar nuevo activo** cuadro de diálogo.  
  
10. En la barra de menús, elija **archivo**, **guardar todo** cuando termine de y, a continuación, cierre el Diseñador de manifiestos.  
  
11. En la barra de menús, elija **generar**, **generar solución**y, a continuación, asegúrese de que el proyecto se compila sin errores.  
  
12. En **el Explorador de soluciones**, abra el menú contextual para el **ProjectExtensionPackage** del proyecto y elija la **Abrir carpeta en el Explorador de archivos** botón.  
  
13. En **Explorador de archivos**, abra la carpeta de salida de compilación para el proyecto ProjectExtensionPackage y, a continuación, compruebe que la carpeta contiene un archivo que se denomina ProjectExtensionPackage.vsix.  
  
     De forma predeterminada, la carpeta de salida de la compilación es \bin\Debug, ubicada bajo la carpeta que contiene el archivo de proyecto.  
  
## <a name="testing-the-project-property"></a>Probar la propiedad de proyecto  
 Ahora está listo para probar la propiedad de proyecto personalizadas. Es más fácil de depurar y probar la extensión de propiedad de proyecto nuevo en una instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Esta instancia de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se crea al ejecutar un VSIX u otro proyecto de extensibilidad. Cuando haya depurado el proyecto, puede instalar la extensión en el sistema y, a continuación, continuar al depurar y probar en una instancia normal de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Para depurar y probar la extensión en una instancia experimental de Visual Studio  
  
1.  Reinicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas y, a continuación, abra la solución ProjectExtensionPackage.  
  
2.  Iniciar una compilación de depuración del proyecto de ello, elija la **F5** clave o, en la barra de menús, elija **depurar**, **Iniciar depuración**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]instala la extensión en %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1.0 e inicia una instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  En la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de SharePoint para una solución de granja de servidores y usar los valores predeterminados para los demás valores en el asistente.  
  
    1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
    2.  En la parte superior de la **nuevo proyecto** diálogo cuadro, elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.  
  
         Extensiones de herramientas de SharePoint requieren características de esta versión de la [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  En el **plantillas** nodo, expanda el **Visual C#** o **Visual Basic** nodo, elija la **SharePoint** nodo y, a continuación, elija la **2010** nodo.  
  
    4.  Elija la **proyecto de SharePoint 2010** plantilla y, a continuación, escriba **ModuleTest** como el nombre del proyecto.  
  
4.  En **el Explorador de soluciones**, elija la **ModuleTest** nodo del proyecto.  
  
     Una nueva propiedad personalizada **carpeta de imágenes de mapa** aparece en la **propiedades** ventana con un valor predeterminado de **False**.  
  
5.  Cambie el valor de esa propiedad para **True**.  
  
     Una carpeta de recursos de imágenes se agrega al proyecto de SharePoint.  
  
6.  Volver a cambiar el valor de esa propiedad a **False**.  
  
     Si elige la **Sí** botón en el **elimine la carpeta imágenes?** cuadro de diálogo, las imágenes se elimina la carpeta de recursos del proyecto de SharePoint.  
  
7.  Cierre la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Extender proyectos de SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Cómo: agregar una propiedad a los proyectos de SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Conversión entre tipos de sistema de proyecto de SharePoint y otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Guardar datos en las extensiones del sistema del proyecto de SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Asociación de datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  