---
title: Desarrollo de Office y SharePoint en Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 76043da9815becd6b5cb25a2117b4ff746d6d242
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898653"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Desarrollo de Office y SharePoint en Visual Studio
  Puede ampliar Microsoft Office y SharePoint mediante la creación de una aplicación ligera o un complemento que los usuarios descarguen desde la [Tienda Office](https://store.office.com/) o un catálogo de la organización, o bien mediante la creación de una solución basada en .NET Framework que los usuarios instalen en un equipo.  
  
 En este tema:  
  
-   [Crear complementos para Office y SharePoint](#Apps)  
  
-   [Crear un complemento de VSTO](#Add-ins)  
  
-   [Crear una solución de SharePoint](#Solutions)  
  
##  <a name="Apps"></a> Crear complementos para Office y SharePoint  
 Office 2013 y SharePoint 2013 presentan un nuevo modelo de complementos que ayuda a compilar, distribuir y rentabilizar los complementos que amplían Office y SharePoint.  Estos complementos se pueden ejecutar en Office o SharePoint Online y los usuarios pueden interactuar con ellos desde muchos dispositivos.  
  
 Obtenga información sobre cómo usar el nuevo [modelo de complemento de Office](/office/dev/add-ins/overview/office-add-ins) para ampliar la experiencia de Office para los usuarios.  
  
 Estos complementos tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.  Para comenzar, use Office Developer Tools en Visual Studio o las herramientas ligeras basadas en web con nombre en clave herramientas de desarrollo de Office 365 Napa, que permiten crear proyectos, escribir código y ejecutar complementos en un explorador.  
  
 ![Las aplicaciones para Office y SharePoint el modelo conceptual](../vsto/media/officeandsharepointapps2015.png "aplicaciones para Office y SharePoint el modelo conceptual")  
  
### <a name="build-an-office-add-in"></a>Crear un complemento de Office  
 Puede crear un complemento de Office para ampliar la funcionalidad de Office. Se trata básicamente de una página Web que se hospeda en una aplicación de Office como Word, Excel, Outlook y PowerPoint. La aplicación puede agregar funcionalidad a documentos, hojas de cálculo, mensajes de correo electrónico, citas, presentaciones y proyectos.  
  
 Puede vender la aplicación en la Tienda Office.  En la [Tienda Office](https://store.office.com/) , es fácil rentabilizar los complementos, administrar las actualizaciones y hacer un seguimiento de la telemetría. También puede publicar la aplicación para los usuarios por medio de un catálogo de aplicaciones en SharePoint o en Exchange Server.  
  
 La siguiente aplicación para Office muestra datos de una hoja de cálculo en un mapa de Bing.  
  
 ![Aplicación de contenido para Office](../vsto/media/appforoffice.png "aplicación de contenido para Office")  
  
 **Más información**  
  
|En|Vea|  
|--------|---------|  
|Obtenga más información sobre los complementos de Office y luego cree uno.|[Complementos de Office](/office/dev/add-ins/publish/publish)|  
|Compare las distintas maneras en que puede ampliar Office para decidir si le conviene usar una aplicación o un complemento de Office.|[Guía básica para los complementos de Office, VSTO y VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
  
### <a name="build-a-sharepoint-add-in"></a>Crear un complemento de SharePoint  
 Puede compilar un complemento de SharePoint a fin de ampliar la funcionalidad de SharePoint para los usuarios. Es básicamente una aplicación pequeña, fácil de usar e independiente que resuelve una necesidad de usuario o de empresa.  
  
 Puede vender la aplicación para SharePoint en la [Tienda Office](https://store.office.com/). También puede publicar el complemento para los usuarios por medio de un catálogo de complementos en SharePoint.  Los propietarios de los sitios pueden instalar, actualizar y desinstalar el complemento en sus sitios de SharePoint sin ayuda del administrador de un servidor de la granja o de la colección de sitios.  
  
 Este es un ejemplo de una aplicación para SharePoint que ayuda a los usuarios administrar contactos de negocios.  
  
 ![Aplicación de administrador de contactos empresariales para SharePoint](../vsto/media/appforsharepoint.png "aplicación de administrador de contactos empresariales para SharePoint")  
  
 **Más información**  
  
|En|Vea|  
|--------|---------|  
|Obtenga más información sobre los complementos de SharePoint y luego cree uno.|[Complementos de SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|  
|Compare los complementos de SharePoint con las soluciones tradicionales de SharePoint.|[Complementos de SharePoint en comparación con las soluciones de SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Elija si quiere compilar un complemento de SharePoint o una solución de SharePoint.|[Decidir entre las soluciones de SharePoint y los complementos de SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
  
##  <a name="Add-ins"></a> Crear un complemento de VSTO  
 Crear un complemento de VSTO para Office 2007 u Office 2010, o para ampliar Office 2013 y Office 2016 más allá de lo que es posible con los complementos de Office. Los complementos de VSTO solo se ejecutan en el escritorio. Los usuarios deben instalar los complementos VSTO, para que sean suelen ser más difíciles de implementar y admitir.  Sin embargo, su complemento de VSTO se puede integrar más estrechamente en Office. Por ejemplo, puede agregar pestañas y controles a la cinta de Office y realizar tareas de automatización avanzadas, como la combinación de documentos o la modificación de gráficos. Puede aprovechar .NET Framework y usar C# y Visual Basic para interactuar con objetos de Office.  
  
 Este es un ejemplo que puede hacer que un complemento de VSTO. Este complemento de VSTO agrega controles de la Cinta, un panel de tareas personalizado y un cuadro de diálogo a PowerPoint.  
  
 ![Solución de complemento de PowerPoint](../vsto/media/powerpointaddin.png "solución de complemento de PowerPoint")  
  
 **Más información**  
  
|En|Leer|  
|--------|----------|  
|Compare las distintas maneras en que puede ampliar Office y decida si debería usar un complemento de VSTO o un complemento de Office.|[Guía básica para los complementos de Office, VSTO y VBA](https://blogs.msdn.microsoft.com/officeapps/2013/06/18/roadmap-for-apps-for-office-vsto-and-vba/)|  
|Cree un complemento de VSTO.|[Crear complementos de VSTO con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|  
  
##  <a name="Solutions"></a> Crear una solución de SharePoint  
 Crear una solución de SharePoint para SharePoint Foundation 2010 y SharePoint Server 2010, o bien, para ampliar SharePoint 2013 y SharePoint 2016 de maneras más allá de lo que es posible con un complemento de SharePoint.  
  
 Las soluciones de SharePoint requieren servidores de granja de SharePoint locales. Los administradores deben instalarlos y, como las soluciones se ejecutan en SharePoint, pueden afectar al rendimiento del servidor. Sin embargo, las soluciones proporcionan un acceso más detallado a los objetos de SharePoint. Además, cuando se compila una solución de SharePoint, se puede aprovechar .NET Framework y usar C# y Visual Basic para interactuar con objetos de SharePoint.  
  
 **Más información**  
  
|En|Vea|  
|--------|---------|  
|Comparar soluciones de SharePoint con complementos de SharePoint|[Complementos de SharePoint en comparación con las soluciones de SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|  
|Cree una solución de SharePoint.|[Crear soluciones de SharePoint](../sharepoint/create-sharepoint-solutions.md)|  
