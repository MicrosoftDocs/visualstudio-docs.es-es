---
title: Procedimiento Crear proyectos de Office en Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38be1ae60dd86160bc9b107ffc0bdd19f7a1e56d
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867187"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Procedimiento Crear proyectos de Office en Visual Studio
  Puede usar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para crear complementos de VSTO y de nivel de documento personalizaciones para aplicaciones de Microsoft Office. Para obtener más información acerca de estos tipos de proyectos, vea [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-vsto-add-in-project"></a>Para crear un proyecto de complemento de VSTO  
  
1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Si su entorno de desarrollo integrado (IDE) se establece para usar [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] configuración de desarrollo, en el **archivo** menú, elija **New** > **proyecto**.  
  
    Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
   > [!NOTE]  
   >  De forma predeterminada, los proyectos de Office tienen como destino [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para obtener más información, consulte [perfil de cliente de .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2. En el panel Plantillas, bajo el nodo para el idioma que desea usar, expanda **Office/SharePoint**.  
  
3. Elija la **complementos de Office** nodo.  
  
4. En la lista de plantillas de proyecto, seleccione una plantilla de proyecto de complemento de VSTO. Para obtener una lista de plantillas de proyecto disponibles complementos de VSTO, consulte [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Si las plantillas de proyecto no son visibles al seleccionar el **complementos de Office** nodo, asegúrese de que **.NET Framework 4** o posterior, está seleccionado en el cuadro combinado en la parte superior del cuadro de diálogo. Las plantillas de proyecto de Office se pueden ver para ambas versiones de .NET Framework.  
  
5. En el **nombre** , escriba un nombre para el proyecto. De forma predeterminada, el nombre del proyecto también se usa como nombre de la solución.  
  
6. En el **ubicación** , escriba la ruta de acceso donde desea crear el proyecto. Puede usar rutas de acceso absolutas y UNC. No use HTTP, FTP ni otras rutas de acceso de protocolo.  
  
    Las ubicaciones tienen los siguientes formatos:  
  
   * [*drive*\]\:  
  
   * \\\\*Servidor*\\*recurso compartido*  
  
     No use estos caracteres en la ubicación:  
  
   * Asterisco (*)  
  
   * Barra vertical (|)  
  
   * Dos puntos (:) (Excepto después de la letra de unidad)  
  
   * Comillas dobles (") (Las rutas de acceso que contienen espacios no requieren comillas)  
  
   * Menor que (\<)  
  
   * Mayor que (>)  
  
   * Signo de interrogación (?)  
  
   * Signo de porcentaje (%)  
  
7. Elija el botón **Aceptar** .
  
    > [!NOTE]  
    >  Los proyectos de complemento siempre se guardan cuando se crean y no se pueden crear como proyectos temporales. Para obtener más información sobre proyectos temporales, vea [proyectos temporales](https://msdn.microsoft.com/9cf1944c-7045-44cc-8701-7b0eb4099f2b).  
  
### <a name="to-create-a-document-level-customization-project"></a>Para crear un proyecto de personalización en el nivel de documento  
  
1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Si su IDE está configurado para usar la configuración de desarrollo de Visual Basic, en el **archivo** menú, elija **New** > **proyecto**.  
  
    Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
   > [!NOTE]  
   >  De forma predeterminada, los proyectos de Office tienen como destino [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Para obtener más información, consulte [perfil de cliente de .NET Framework](/dotnet/framework/deployment/client-profile).  
  
2. En el panel Plantillas, bajo el nodo para el idioma que desea usar, expanda **Office/SharePoint**.  
  
3. Seleccione el nodo **Complementos de Office** .  
  
4. En la lista de plantillas de proyecto, seleccione una plantilla de proyecto de nivel de documento. Para obtener una lista de plantillas de proyecto de nivel de documento disponibles, consulte [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md).  
  
   > [!NOTE]  
   >  Si las plantillas de proyecto no son visibles al seleccionar el **complementos de Office** nodo, asegúrese de que **.NET Framework 4** o posterior, está seleccionado en el cuadro combinado en la parte superior del cuadro de diálogo. Las plantillas de proyecto de Office se pueden ver para ambas versiones de .NET Framework.  
  
5. En el **nombre** , escriba un nombre para el proyecto. De forma predeterminada, este nombre también se usa para el documento. Si el IDE está definido para usar la configuración de desarrollo de Visual C# o la configuración de desarrollo general, escriba también la ubicación y el nombre de la solución.  
  
   > [!NOTE]  
   >  No se pueden usar caracteres suplentes en la ruta de acceso del proyecto ni en el nombre del proyecto. Además, si tiene previsto implementar la solución para su uso sin conexión, los caracteres del nombre del proyecto deben ajustarse a las especificaciones del protocolo HTTP.  
  
6. Elija el botón **Aceptar** .  
  
    Se abre el **Asistente para proyectos de Visual Studio Tools para Office** .  
  
7. Seleccione **crear un nuevo documento** si desea crear un nuevo documento para la solución, o seleccione **copiar un documento existente** si desea personalizar un documento existente.  
  
    Si crea un nuevo documento, especifique el nombre en el **nombre** cuadro y seleccione el formato del documento mediante el **formato** cuadro. Para obtener más información acerca de los formatos disponibles, consulte [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
    Si usa un documento existente, especifique la ubicación del documento en el **ruta de acceso completa del documento existente** cuadro. Puede usar rutas de acceso absolutas y rutas UNC. No use HTTP, FTP ni otras rutas de acceso de protocolo para el documento.  
  
    Las ubicaciones tienen los siguientes formatos:  
  
   - [*drive*\]\:  
  
   - \\\\*Servidor*\\*recurso compartido*  
  
     No use estos caracteres en la ubicación:  
  
   - Asterisco (*)  
  
   - Barra vertical (|)  
  
   - Dos puntos (:) (Excepto después de la letra de unidad)  
  
   - Comillas dobles (") (Las rutas de acceso que contienen espacios no requieren comillas)  
  
   - Menor que (\<)  
  
   - Mayor que (>)  
  
   - Signo de interrogación (?)  
  
   - Signo de porcentaje (%)  
  
   > [!NOTE]  
   >  Si usa un documento existente en un proyecto de [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)], utilice únicamente documentos que se crearon en [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o se convirtieron a esa versión. Del mismo modo, si usa un documento existente en un proyecto de Word 2010, utilice únicamente documentos que se crearon en Word 2010 o se convirtieron a esa versión. Si usa un documento que se creó en una versión anterior de Word, se deshabilitarán determinadas características del documento. Si intenta escribir código que usa estas características, pueden producirse errores en el proyecto. Para convertir un documento, ábralo en [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o Word 2010, en el **archivo** pestaña en la cinta de opciones, elija **información** > **convertir**.  
  
8. Elija **Finalizar**.  
  
9. Agregue la carpeta del proyecto y sus subcarpetas a la lista de ubicaciones de confianza en el Centro de confianza de Word en los casos siguientes:  
  
   - Creación de un documento de Word que se basa en un *.docm* archivo y el documento contiene un proyecto de VBA u hospeda controles de formularios Windows Forms. Agregar la carpeta del proyecto a la lista de ubicaciones de confianza servirá para asegurarnos de que el documento funciona del modo esperado en tiempo de diseño.  
  
   - Creación de un proyecto de plantilla de Word que se basa en un *.dotx* archivo. Agregue la carpeta del proyecto a la lista de ubicaciones de confianza para que se pueda ejecutar y depurar el proyecto.  
  
     Para obtener más información sobre cómo agregar un documento a las ubicaciones de confianza, consulte el sitio web de Microsoft Office Online [crear, quitar o cambiar una ubicación de confianza para los archivos](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="see-also"></a>Vea también  
 [Introducción a las plantillas de proyecto de Office](../vsto/office-project-templates-overview.md)   
 [Desarrollo en colaboración de las soluciones de Office](../vsto/collaborative-development-of-office-solutions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
