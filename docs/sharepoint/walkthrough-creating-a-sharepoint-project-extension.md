---
title: "Walkthrough: Creating a SharePoint Project Extension | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  En este tutorial se muestra cómo crear una extensión para los proyectos de SharePoint.  Puede utilizar una extensión de proyecto para responder a los eventos de nivel de proyecto como cuando se agrega, se elimina, o cambia un proyecto.  También puede agregar propiedades personalizadas o responder cuando cambia un valor de propiedad.  A diferencia de las extensiones de elemento de proyecto, las extensiones de proyecto no pueden estar asociadas a un tipo de proyecto de SharePoint determinado.  Cuando crea una extensión de proyecto, se carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 En este tutorial, creará una propiedad booleana personalizada que se agrega a cualquier proyecto de SharePoint creado en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Cuando se establece en **True**, la nueva propiedad agrega o asigna una carpeta de recursos Images al proyecto.  Cuando se establece en **False**, se quita la carpeta Images, si existe.  Para obtener más información, vea [Cómo: Agregar y quitar carpetas asignadas](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 En este tutorial se muestran las siguientes tareas:  
  
-   Crear una extensión [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para los proyectos SharePoint que hace lo siguiente:  
  
    -   Agrega una propiedad de proyecto personalizada a la ventana Propiedades.  La propiedad se aplica a cualquier proyecto de SharePoint.  
  
    -   Utiliza el modelo de objetos de proyecto de SharePoint para agregar una carpeta asignada a un proyecto.  
  
    -   Usa el modelo de objetos de automatización \(DTE\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para eliminar una carpeta asignada del proyecto.  
  
-   Compilar un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para implementar el ensamblado de la extensión de propiedad de proyecto.  
  
-   Depurar y probar la propiedad de proyecto.  
  
## Requisitos previos  
 Necesitará los componentes siguientes en el equipo de desarrollo para completar este tutorial:  
  
-   Ediciones compatibles de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint y [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  En este tutorial se utiliza la plantilla **Proyecto VSIX** del [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] para crear un paquete VSIX para implementar la extensión de propiedad de proyecto.  Para obtener más información, vea [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## Crear los proyectos  
 Para completar este tutorial, debe crear dos proyectos:  
  
-   Un proyecto VSIX para crear el paquete VSIX e implementar la extensión de proyecto.  
  
-   Un proyecto de biblioteca de clases que implemente la extensión de proyecto.  
  
 Comience el tutorial creando ambos proyectos.  
  
#### Para crear el proyecto VSIX  
  
1.  Inicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  En la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
3.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación el nodo **Extensibilidad** .  
  
    > [!NOTE]  
    >  Este nodo solo está disponible si instala Visual Studio SDK.  Para obtener más información, vea la sección Requisitos previos, anteriormente en este tema.  
  
4.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework, y elija la plantilla **Proyecto VSIX** .  
  
5.  En el cuadro **Nombre** , escriba **ProjectExtensionPackage**, y elija el botón **Aceptar** .  
  
     El proyecto **ProjectExtensionPackage** aparece en **Explorador de soluciones**.  
  
#### Para crear la extensión de proyecto  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el nodo de la solución, elija **Agregar**y, a continuación **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  En los proyectos [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , el nodo de la solución aparece en **Explorador de soluciones** únicamente si la casilla **Mostrar solución siempre** se selecciona en [General, Proyectos y soluciones, Cuadro de diálogo Opciones](http://msdn.microsoft.com/es-es/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  En el cuadro de diálogo **Nuevo proyecto** , expanda los nodos **Visual c\#** o **Visual Basic** y, a continuación **Windows**.  
  
3.  En la parte superior del cuadro de diálogo, elija **.NET Framework 4,5** en la lista de versiones de .NET Framework, y elija la plantilla de proyecto **Biblioteca de clases** .  
  
4.  En el cuadro **Nombre** , escriba **ProjectExtension**, y elija el botón **Aceptar** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] agrega el proyecto **ProjectExtension** a la solución y abre el archivo de código predeterminado Class1.  
  
5.  Elimine el archivo de código Class1 del proyecto.  
  
## Configurar el proyecto  
 Antes de escribir el código que crea la extensión del elemento de proyecto, tiene que agregar los archivos de código y las referencias de ensamblado al proyecto de extensión.  
  
#### Para configurar el proyecto  
  
1.  Agregue un archivo de código denominado **CustomProperty** al proyecto ProjectExtension.  
  
2.  Abrir el menú contextual para el proyecto **ProjectExtension** y, a continuación **Agregar referencia**.  
  
3.  En el cuadro de diálogo **Administrador de referencia – CustomProperty** , elija el nodo **Framework** , y seleccione la casilla junto a los ensamblados System.ComponentModel.Composition y System.Windows.Forms.  
  
4.  Elija el nodo **Extensiones** , active la casilla junto a los ensamblados Microsoft.VisualStudio.SharePoint y EnvDTE, y después elija el botón **Aceptar** .  
  
5.  En **Explorador de soluciones**, bajo la carpeta **Referencias** para el proyecto **ProjectExtension** , elija **EnvDTE**.  
  
6.  En la ventana **Propiedades**, cambie el valor de **Incrustar tipos de interoperabilidad** a **False**.  
  
## Definir la nueva propiedad de proyecto de SharePoint  
 Cree una clase que defina la extensión de proyecto y el comportamiento de la nueva propiedad.  Para definir la nueva extensión de proyecto, la clase implementa la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implemente esta interfaz siempre que desee definir una extensión para un proyecto de SharePoint.  También agregue <xref:System.ComponentModel.Composition.ExportAttribute> a la clase.  Este atributo permite que [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> al constructor del atributo.  
  
#### Para definir la nueva propiedad de proyecto de SharePoint  
  
1.  Pegue el código siguiente en el archivo de código CustomProperty.  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## Compilar la solución  
 A continuación, compile la solución para asegurarse de que se compila sin errores.  
  
#### Para compilar la solución  
  
1.  En la barra de menú, elija **Generar**, **Compilar solución**.  
  
## Crear un paquete VSIX para implementar la extensión de propiedad de proyecto  
 Para implementar la extensión de proyecto, utilice el proyecto VSIX en la solución para crear un paquete VSIX.  Primero, configure el paquete VSIX modificando el archivo source.extension.vsixmanifest incluido en el proyecto VSIX.  A continuación, cree el paquete VSIX compilando la solución.  
  
#### Para crear y configurar el paquete VSIX  
  
1.  En **Explorador de soluciones**, abra el menú contextual para el archivo source.extension.vsixmanifest, y después elija el botón **Abrir** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] abre el archivo en el diseñador de manifiestos.  La información que aparece en la pestaña **Metadatos** también aparece en **Extensiones y actualizaciones**. Todos los paquetes VSIX requieren el archivo extension.vsixmanifest.  Para obtener más información sobre este archivo, vea [Referencia de esquema de extensión VSIX](http://msdn.microsoft.com/es-es/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  En el cuadro **Nombre de producto** , entre en **Propiedad de proyecto personalizada**.  
  
3.  En el cuadro **Autor** , entre en **Contoso**.  
  
4.  En el cuadro **Descripción** , escriba el **Una propiedad de proyecto de SharePoint personalizada que alterna la asignación de la carpeta de recurso Images al proyecto**.  
  
5.  Elija la ficha **Activos** , y elija el botón **Nuevo** .  
  
     El cuadro de diálogo **Agregar nuevo activo** aparece.  
  
6.  En la lista **Tipo** , elija **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Este valor corresponde al elemento `MEFComponent` del archivo extension.vsixmanifest.  Este elemento especifica el nombre de un ensamblado de extensión en el paquete VSIX.  Para obtener más información, vea [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/es-es/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  En la lista **Origen** , elija el botón de opción **Un proyecto de la solución actual** .  
  
8.  En la lista **Proyecto** , elija **ProjectExtension**.  
  
     Este valor identifica el nombre del ensamblado que está compilando en el proyecto.  
  
9. Elija **Aceptar** para cerrar el cuadro de diálogo **Agregar nuevo activo** .  
  
10. En la barra de menú, elija **Archivo**, **Guardar todos** cuando termine, y luego cierre el diseñador de manifiestos.  
  
11. En la barra de menú, elija **Generar**, **Compilar solución**, y asegúrese de que el proyecto se compila sin errores.  
  
12. En **Explorador de soluciones**, abra el menú contextual para el proyecto **ProjectExtensionPackage** , y elija el botón **Abrir carpeta en el Explorador de archivos** .  
  
13. En **Explorador de archivos**, abra la carpeta de salida de compilación de ProjectExtensionPackage, y después comprueba que la carpeta contiene un archivo ProjectExtensionPackage.vsix.  
  
     De forma predeterminada, la carpeta de resultado de compilación es ..  \\bin\\Debug, que se encuentra bajo la carpeta que contiene el archivo de proyecto.  
  
## Probar la propiedad de proyecto  
 Ya puede probar la propiedad de proyecto personalizada.  Es más fácil depurar y probar la nueva extensión de propiedad de proyecto en una instancia experimental [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Esta instancia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se crea cuando se ejecuta un VSIX u otro proyecto de extensibilidad.  Después de depurar el proyecto, puede instalar la extensión en el sistema y continuar depurándola y probar en una instancia normal [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Para depurar y probar la extensión en una instancia experimental de Visual Studio  
  
1.  Reinicie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con credenciales administrativas, y vuelva a abrir la solución ProjectExtensionPackage.  
  
2.  Inicie una compilación de depuración del proyecto o eligiendo la clave **F5** o, en la barra de menús, eligiendo **Depurar**, **Iniciar depuración**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] instala la extensión a %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Project Property \\ 1,0 e inicia una instancia experimental [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  En la instancia experimental [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], cree un proyecto de SharePoint para una solución de granja, y use los valores predeterminados en los otros valores del asistente.  
  
    1.  En la barra de menú, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
    2.  En la parte superior del cuadro de diálogo **Nuevo proyecto** , elija **.NET Framework 3.5** en la lista de versiones de .NET Framework.  
  
         Las extensiones de herramientas de SharePoint requieren características de esta versión [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Bajo el nodo **Plantillas** , expanda el nodo **Visual c\#** o **Visual Basic** , elija el nodo **SharePoint** y, a continuación el nodo **2010** .  
  
    4.  Elija la plantilla **Proyecto de SharePoint 2010** , y escriba en **ModuleTest** como el nombre del proyecto.  
  
4.  En **Explorador de soluciones**, elija el nodo del proyecto **ModuleTest** .  
  
     Una nueva propiedad **Map Images Folder** personalizado aparece en la ventana **Propiedades** con un valor predeterminado de **False**.  
  
5.  Cambie el valor de esa propiedad en **True**.  
  
     Se agrega una carpeta de recurso Images al proyecto SharePoint.  
  
6.  Cambie el valor de esa propiedad de nuevo a **False**.  
  
     Si elige el botón **Sí** en el cuadro de diálogo **¿Elimine la carpeta Images?** , la carpeta de recurso Images se elimina del proyecto de SharePoint.  
  
7.  Cierre la instancia experimental de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## Vea también  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  