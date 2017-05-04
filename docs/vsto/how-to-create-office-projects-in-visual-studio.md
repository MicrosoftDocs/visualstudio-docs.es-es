---
title: "C&#243;mo: Crear proyectos de Office en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.SelectDocWizard.Page1"
  - "VST.SelectDocWizard.Http"
  - "VST.SelectDocWizard.Extension"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "complementos [desarrollo de Office en Visual Studio], crear proyectos"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], crear proyectos"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], crear"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], crear"
  - "proyectos de Office [desarrollo de Office en Visual Studio]"
  - "proyectos [desarrollo de Office en Visual Studio], crear"
ms.assetid: 0037dbd8-0d2a-4766-90ea-81c819379582
caps.latest.revision: 96
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 95
---
# C&#243;mo: Crear proyectos de Office en Visual Studio
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] se puede usar para crear complementos de VSTO y personalizaciones en el nivel de documento para aplicaciones de Microsoft Office. Para obtener más información sobre estos tipos de proyectos, vea el artículo de [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Para crear un proyecto de complemento de VSTO  
  
1.  En el menú **Archivo**, elija **Nuevo**, **Proyecto**.  Si su entorno de desarrollo integrado \(IDE\) está configurado para usar la configuración de desarrollo de [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], en el menú **Archivo** elija **Nuevo** y, a continuación, **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  De forma predeterminada, los proyectos de Office tienen como destino [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Para obtener más información, vea el artículo de [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  En el panel de plantillas, debajo del nodo del lenguaje que desee usar, expanda **Office\/SharePoint**.  
  
3.  Elija el nodo **Complementos de Office**.  
  
4.  En la lista de plantillas de proyecto, seleccione una plantilla de proyecto de complemento de VSTO.  Para ver la lista de plantillas de proyectos de complemento de VSTO disponibles, consulte [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Si al seleccionar el nodo **Complementos de Office**, no ve las plantillas de proyecto, asegúrese de que **.NET Framework 4** o una versión posterior se haya seleccionado en el cuadro combinado de la parte superior del cuadro de diálogo.  Las plantillas de proyecto de Office se pueden ver para ambas versiones de .NET Framework.  
  
5.  En el cuadro **Nombre**, escriba un nombre para el proyecto.  De forma predeterminada, el nombre del proyecto también se usa como nombre de la solución.  
  
6.  En el cuadro **Ubicación**, escriba la ruta de acceso donde desea crear el proyecto.  Puede usar rutas de acceso absolutas y UNC.  No use HTTP, FTP ni otras rutas de acceso de protocolo.  
  
     Las ubicaciones tienen los siguientes formatos:  
  
    -   \[*unidad*\]:\\  
  
    -   \\\\*Servidor*\\*Recurso\_compartido*  
  
     No use estos caracteres en la ubicación:  
  
    -   Asterisco \(\*\)  
  
    -   Barra vertical \(|\)  
  
    -   Dos puntos \(:\) \(Excepto después de la letra de unidad\)  
  
    -   Comillas dobles \("\) \(Las rutas de acceso que contienen espacios no requieren comillas\)  
  
    -   Menor que \(\<\)  
  
    -   Mayor que \(\>\)  
  
    -   Signo de interrogación \(?\)  
  
    -   Signo de porcentaje \(%\)  
  
7.  Elija el botón **Aceptar**.  
  
    > [!NOTE]  
    >  Los proyectos de complemento siempre se guardan cuando se crean  y no se pueden crear como proyectos temporales.  Para obtener más información sobre proyectos temporales, vea el artículo sobre [Proyectos temporales](http://msdn.microsoft.com/es-es/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### Para crear un proyecto de personalización en el nivel de documento  
  
1.  En el menú **Archivo**, elija **Nuevo**, **Proyecto**.  Si su IDE está configurado para usar la configuración de desarrollo de Visual Basic, en el menú **Archivo** elija **Nuevo** y **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto**.  
  
    > [!NOTE]  
    >  De forma predeterminada, los proyectos de Office tienen como destino [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Para obtener más información, vea el artículo de [.NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).  
  
2.  En el panel de plantillas, debajo del nodo del lenguaje que desee usar, expanda **Office\/SharePoint**.  
  
3.  Seleccione el nodo **Complementos de Office**.  
  
4.  En la lista de plantillas de proyecto, seleccione una plantilla de proyecto de nivel de documento.  Para consultar una lista de las plantillas disponibles, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
    > [!NOTE]  
    >  Si al seleccionar el nodo **Complementos de Office**, no ve las plantillas de proyecto, asegúrese de que **.NET Framework 4** o una versión posterior se haya seleccionado en el cuadro combinado de la parte superior del cuadro de diálogo.  Las plantillas de proyecto de Office se pueden ver para ambas versiones de .NET Framework.  
  
5.  En el cuadro **Nombre**, escriba un nombre para el proyecto.  De forma predeterminada, este nombre también se usa para el documento.  Si el IDE está definido para usar la configuración de desarrollo de Visual C\# o la configuración de desarrollo general, escriba también la ubicación y el nombre de la solución.  
  
    > [!NOTE]  
    >  No se pueden usar caracteres suplentes en la ruta de acceso del proyecto ni en el nombre del proyecto.  Para obtener información sobre los caracteres suplentes, vea el artículo sobre [NIB: Unicode Support for Surrogate Pairs and Combining Character Sequences](http://msdn.microsoft.com/es-es/cba3285c-7b47-4ce8-8970-f48d6ac03e39).  Además, si tiene previsto implementar la solución para su uso sin conexión, los caracteres del nombre del proyecto deben ajustarse a las especificaciones del protocolo HTTP.  
  
6.  Elija el botón **Aceptar**.  
  
     Se abre el **Asistente para proyectos de Visual Studio Tools para Office**.  
  
7.  Seleccione **Crear un nuevo documento** si desea crear un nuevo documento para la solución, o seleccione **Copiar un documento existente** si desea personalizar un documento existente.  
  
     Si crea un nuevo documento, especifique el nombre en el cuadro **Nombre** y seleccione el formato del documento mediante el cuadro **Formato**.  Para obtener más información acerca de los formatos disponibles, vea el artículo sobre [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
     Si usa un documento existente, especifique la ubicación del mismo en el cuadro **Ruta de acceso completa al documento existente**.  Puede usar rutas de acceso absolutas y rutas UNC.  No use HTTP, FTP ni otras rutas de acceso de protocolo para el documento.  
  
     Las ubicaciones tienen los siguientes formatos:  
  
    -   \[*unidad*\]:\\  
  
    -   \\\\*Servidor*\\*Recurso\_compartido*  
  
     No use estos caracteres en la ubicación:  
  
    -   Asterisco \(\*\)  
  
    -   Barra vertical \(|\)  
  
    -   Dos puntos \(:\) \(Excepto después de la letra de unidad\)  
  
    -   Comillas dobles \("\) \(Las rutas de acceso que contienen espacios no requieren comillas\)  
  
    -   Menor que \(\<\)  
  
    -   Mayor que \(\>\)  
  
    -   Signo de interrogación \(?\)  
  
    -   Signo de porcentaje \(%\)  
  
    > [!NOTE]  
    >  Si usa un documento existente en un proyecto de [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], utilice únicamente documentos que se crearon en [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o se convirtieron a esa versión.  Del mismo modo, si usa un documento existente en un proyecto de Word 2010, utilice únicamente documentos que se crearon en Word 2010 o se convirtieron a esa versión.  Si usa un documento que se creó en una versión anterior de Word, se deshabilitarán determinadas características del documento.  Si intenta escribir código que usa estas características, pueden producirse errores en el proyecto.  Para convertir un documento, ábralo en [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010. A continuación, en la pestaña **Archivo**, elija **Información** y luego **Convertir**.  
  
8.  Elija **Finalizar**.  
  
9. Agregue la carpeta del proyecto y sus subcarpetas a la lista de ubicaciones de confianza en el Centro de confianza de Word en los casos siguientes:  
  
    -   Si crea un documento de Word que se basa en un archivo .docm y el documento contiene un proyecto de VBA u hospeda controles de Windows Forms.  Agregar la carpeta del proyecto a la lista de ubicaciones de confianza servirá para asegurarnos de que el documento funciona del modo esperado en tiempo de diseño.  
  
    -   Si crea un proyecto de plantilla de Word basado en un archivo .dotx.  Agregue la carpeta del proyecto a la lista de ubicaciones de confianza para que se pueda ejecutar y depurar el proyecto.  
  
     Para obtener más información sobre cómo agregar un documento a las ubicaciones de confianza, vea el sitio web de Microsoft Office Online [Crear, quitar o cambiar una ubicación de confianza de los archivos](https://support.office.com/es-es/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## Vea también  
 [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md)   
 [Desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  